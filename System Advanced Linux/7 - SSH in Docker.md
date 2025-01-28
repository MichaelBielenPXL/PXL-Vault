# SSH in Docker

## Wat is SSH?

**SSH (Secure Shell)** is een protocol dat veilige communicatie mogelijk maakt tussen twee computers via een onbeveiligd netwerk. Het wordt vaak gebruikt voor:

- Beveiligde toegang tot externe servers.
- Bestanden overzetten.
- Uitvoeren van commando’s op afstand.

SSH maakt gebruik van asymmetrische encryptie (bijvoorbeeld RSA of ECDSA) om de verbinding te beveiligen.

---

## SSH gebruiken in Docker-containers

Hoewel Docker-containers bedoeld zijn om specifieke taken uit te voeren en doorgaans geen SSH nodig hebben, kunnen er scenario's zijn waarbij SSH handig is, bijvoorbeeld voor debugging of onderhoud. Hier is een overzicht van hoe SSH kan worden ingesteld en gebruikt in een Docker-container.

---

## Een container voorbereiden met SSH

### Stap 1: Maak een Dockerfile

Om SSH in een container te gebruiken, moeten we een Dockerfile schrijven die een SSH-server installeert.

**Voorbeeld Dockerfile:**

```Dockerfile
# Gebruik een basis image
FROM ubuntu:20.04

# Installeer OpenSSH Server
RUN apt-get update && apt-get install -y openssh-server

# Maak een directory voor SSH
RUN mkdir /var/run/sshd

# Stel een wachtwoord in voor root (onveilig voor productie!)
RUN echo 'root:password' | chpasswd

# Schakel root login in via SSH
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Voorkom dat SSH automatisch afsluit
RUN echo "PermitTTY yes" >> /etc/ssh/sshd_config

# Stel de standaardpoort in en expose deze
EXPOSE 22

# Start de SSH-server
CMD ["/usr/sbin/sshd", "-D"]
```

---

### Stap 2: Bouw de container image

Gebruik het volgende commando om de Dockerfile te bouwen:

```bash
docker build -t ssh-container .
```

### Stap 3: Start de container

Start een container met de SSH-server:

```bash
docker run -d -p 2222:22 --name ssh-container ssh-container
```

- `-d`: Draait de container in de achtergrond.
- `-p 2222:22`: Map poort 2222 op de host naar poort 22 in de container.

### Stap 4: Verbinden via SSH

Gebruik een SSH-client om verbinding te maken met de container:

```bash
ssh root@localhost -p 2222
```

- Wachtwoord: `password` (zoals ingesteld in de Dockerfile).

---

## Een bestaande container configureren voor SSH

Als je een bestaande container wilt aanpassen om SSH te ondersteunen, kun je de volgende stappen volgen:

### Stap 1: Open een shell in de container

```bash
docker exec -it <container-id> /bin/bash
```

### Stap 2: Installeer en configureer SSH

```bash
apt-get update && apt-get install -y openssh-server
mkdir /var/run/sshd
```

### Stap 3: Stel een wachtwoord in

```bash
echo 'root:password' | chpasswd
```

### Stap 4: Pas de configuratie aan

Bewerk `/etc/ssh/sshd_config` en zorg ervoor dat de volgende regels correct zijn:

```plaintext
PermitRootLogin yes
PermitTTY yes
```

### Stap 5: Start de SSH-server

```bash
service ssh start
```

---

## SSH sleutels gebruiken (veiligere methode)

In plaats van wachtwoorden te gebruiken, kun je SSH sleutels configureren voor een veiligere verbinding.

### Stap 1: Genereer een SSH-sleutel

Op de host:

```bash
ssh-keygen -t rsa -b 2048
```

- De publieke sleutel wordt opgeslagen in `~/.ssh/id_rsa.pub`.

### Stap 2: Voeg de sleutel toe aan de container

1. Kopieer de publieke sleutel naar de container:
    
    ```bash
    docker cp ~/.ssh/id_rsa.pub <container-id>:/root/.ssh/authorized_keys
    ```
    
2. Zorg ervoor dat de permissies correct zijn:
    
    ```bash
    docker exec <container-id> chmod 600 /root/.ssh/authorized_keys
    ```
    

### Stap 3: Verbinden zonder wachtwoord

Nu kun je verbinden zonder een wachtwoord:

```bash
ssh root@localhost -p 2222
```

---

## Beveiligingsmaatregelen

1. **Gebruik SSH-sleutels:**
    
    - Vermijd wachtwoordauthenticatie, vooral in productieomgevingen.
2. **Beperk toegang:**
    
    - Gebruik een firewall of Docker-netwerken om toegang tot SSH te beperken.
3. **Schakel rootlogin uit:**
    
    - Pas de configuratie aan om rootlogin te verbieden:
        
        ```plaintext
        PermitRootLogin no
        ```
        
4. **Gebruik gebruikersaccounts:**
    
    - Maak aparte gebruikersaccounts aan voor SSH-toegang:
        
        ```bash
        useradd -m -s /bin/bash gebruiker
        echo 'gebruiker:wachtwoord' | chpasswd
        ```
        
5. **Expose alleen benodigde poorten:**
    
    - Vermijd het openstellen van poorten die niet nodig zijn.

---

## Alternatieven voor SSH in Docker

SSH is meestal niet nodig in containers, omdat Docker zelf al uitgebreide tools biedt voor beheer en debugging:

- **Gebruik `docker exec`:** Voor directe toegang tot een draaiende container:
    
    ```bash
    docker exec -it <container-id> /bin/bash
    ```
    
- **Gebruik Docker-volumes:** Voor bestandsoverdracht tussen de host en container:
    
    ```bash
    docker cp bestand.txt <container-id>:/pad/in/container
    ```
    
- **Beheer via Docker Compose:** Automatiseer toegang en configuraties met een `docker-compose.yml`-bestand.
    

---

## Conclusie

Hoewel SSH niet standaard vereist is in Docker-containers, kan het nuttig zijn voor specifieke scenario’s zoals debugging of onderhoud. Het is echter belangrijk om beveiligingsmaatregelen te implementeren, zoals het gebruik van SSH-sleutels en het beperken van netwerktoegang. Voor veelgebruikte taken biedt Docker zelf krachtige tools die SSH vaak overbodig maken.