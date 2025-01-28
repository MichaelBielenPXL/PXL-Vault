# Samenvatting System Advanced Linux

## Inleiding

Dit document bevat een uitgebreide samenvatting van de belangrijkste concepten en leerdoelen van het vak **System Advanced Linux**. Elk onderdeel bevat een korte uitleg en een verwijzing naar relevante hoofdstukken met **Obsidian Atomic Links**, zodat je gemakkelijk kunt navigeren.

---

## 1. Containers & Docker Introduction

Containers zijn geïsoleerde, lichtgewicht omgevingen voor softwaretoepassingen. Ze zorgen voor **portabiliteit, schaalbaarheid** en zijn een kernonderdeel van **DevOps en CI/CD**. In tegenstelling tot traditionele virtual machines (VM's) delen containers de kernel van het host-besturingssysteem, wat ze efficiënter maakt in termen van snelheid en resourcegebruik.

### Waarom Containers?

Containers lossen veelvoorkomende problemen in softwareontwikkeling en -implementatie op:

- **Consistentie**: Een applicatie draait overal hetzelfde, ongeacht het onderliggende systeem.
- **Schaalbaarheid**: Containers kunnen eenvoudig worden opgeschaald of gerepliceerd.
- **Snelle implementaties**: Omdat ze lichtgewicht zijn, kunnen containers snel starten en stoppen.
- **Isolatie**: Applicaties in containers draaien geïsoleerd van elkaar, wat stabiliteit en veiligheid vergroot.

### Containers versus Virtual Machines

|**Kenmerk**|**Containers**|**Virtual Machines**|
|---|---|---|
|Opstarttijd|Milliseconden|Minuten|
|Resourcegebruik|Laag|Hoog|
|Isolatie|Procesniveau|Besturingssysteemniveau|
|Portabiliteit|Hoog|Beperkt|

### Werken met Docker

Docker is het populairste platform voor containerbeheer. Enkele veelgebruikte commando’s:

- **Een container starten**: `docker run -d -p 8080:80 --name my-container nginx`
- **Actieve containers bekijken**: `docker ps`
- **Alle containers bekijken (inclusief gestopte)**: `docker ps -a`
- **Een container stoppen**: `docker stop my-container`
- **Een container verwijderen**: `docker rm my-container`

📌 [[1 - Containers & Docker Introduction]]

Containers zijn geïsoleerde, lichtgewicht omgevingen voor softwaretoepassingen. Ze zorgen voor **portabiliteit, schaalbaarheid** en zijn een kernonderdeel van **DevOps en CI/CD**. Dit hoofdstuk behandelt:

- Wat containers zijn en hoe ze werken.
- Het verschil tussen **containers** en **virtual machines**.
- Hoe Docker wordt gebruikt om containers te beheren.

📌 [[1 - Containers & Docker Introduction]]

---

## 2. Dockerfile Introduction

Een **Dockerfile** is een scriptbestand dat instructies bevat om een **Docker image** te bouwen. Met een Dockerfile kunnen ontwikkelaars een gestandaardiseerde en herhaalbare containeromgeving creëren. Dit proces is fundamenteel voor het werken met **Infrastructure as Code (IaC)** en geautomatiseerde CI/CD-pipelines.

### Waarom Dockerfiles?

Dockerfiles maken het mogelijk om containers consistent te bouwen en te configureren, zonder handmatige stappen. De voordelen zijn:

- **Automatisering**: Geen handmatige installatie van afhankelijkheden.
- **Portabiliteit**: Werkt overal hetzelfde, van ontwikkelmachine tot productieomgeving.
- **Versiebeheer**: Elke wijziging in de Dockerfile kan worden getraceerd en beheerd via Git.
- **Efficiëntie**: Door caching en optimalisatie worden builds sneller en zuiniger.

### Basisstructuur van een Dockerfile

Een typische Dockerfile bevat de volgende instructies:

|**Commando**|**Beschrijving**|
|---|---|
|`FROM`|Specificeert de basis image waarop de build is gebaseerd.|
|`WORKDIR`|Bepaalt de werkdirectory binnen de container.|
|`COPY`|Kopieert bestanden van de host naar de container.|
|`RUN`|Voert commando’s uit tijdens de buildfase.|
|`CMD`|Stelt het standaardcommando in dat wordt uitgevoerd bij het starten van de container.|
|`EXPOSE`|Geeft aan op welke poorten de container luistert.|

### Voorbeeld Dockerfile

```Dockerfile
# Stap 1: Basis image
FROM node:18-alpine

# Stap 2: Werkdirectory instellen
WORKDIR /app

# Stap 3: Kopieer package.json en installeer dependencies
COPY package.json .
RUN npm install

# Stap 4: Kopieer de rest van de bestanden
COPY . .

# Stap 5: Expose poort en start applicatie
EXPOSE 3000
CMD ["node", "server.js"]
```

### Werken met lagen en caching

Elke instructie in een Dockerfile genereert een nieuwe **laag** (layer). Docker maakt gebruik van caching om builds sneller te maken. **Best practices voor caching:**

- Zet `COPY package.json .` **voordat** je `RUN npm install` uitvoert. Hierdoor worden afhankelijkheden niet opnieuw geïnstalleerd als de code niet is gewijzigd.
- Gebruik multi-stage builds voor kleinere images.

### Multi-stage builds

Met **multi-stage builds** kun je een lichte en geoptimaliseerde productie-image maken.

```Dockerfile
# Eerste stage: Buildomgeving
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Tweede stage: Productie
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

📌 [[2 - Dockerfile Introduction]]

Een **Dockerfile** is een script dat de instructies bevat om een container image te bouwen. Dit hoofdstuk bespreekt:

- De basisstructuur van een Dockerfile.
- Veelgebruikte commando’s zoals `FROM`, `RUN`, `CMD`, en `COPY`.
- Hoe Docker image lagen werkt en hoe caching werkt voor efficiënte builds.

📌 [[2 - Dockerfile Introduction]]

---

## 3. Docker Container Management

Het effectief beheren van Docker-containers is essentieel voor het bouwen en onderhouden van stabiele applicaties. Dit hoofdstuk behandelt de kernprincipes en commando’s om containers te beheren, inclusief het starten, stoppen, inspecteren en loggen van containers.

### 1. Containers starten en stoppen

Het opstarten en beheren van containers gebeurt met het `docker run`-commando.

**Voorbeeld:**

```bash
docker run -d -p 8080:80 --name webserver nginx
```

- `-d` : Draait de container in de achtergrond (detached mode).
- `-p 8080:80` : Koppelt poort 8080 van de host naar poort 80 in de container.
- `--name webserver` : Geeft de container een naam.
- `nginx` : De gebruikte image.

Een container stoppen:

```bash
docker stop webserver
```

Een container herstarten:

```bash
docker restart webserver
```

### 2. Containerstatus bekijken

Om een lijst van draaiende containers te zien:

```bash
docker ps
```

Om alle containers (inclusief gestopte) te bekijken:

```bash
docker ps -a
```

Om details van een container te inspecteren:

```bash
docker inspect webserver
```

### 3. Logs en debugging

Voor het bekijken van de logs van een container:

```bash
docker logs webserver
```

Real-time logs volgen:

```bash
docker logs -f webserver
```

Statistieken bekijken:

```bash
docker stats webserver
```

### 4. Interactie met een draaiende container

Een shell openen binnen een draaiende container:

```bash
docker exec -it webserver /bin/bash
```

- `-i` : Interactieve modus.
- `-t` : Open een terminal.

Bestanden kopiëren van en naar een container:

```bash
docker cp bestand.txt webserver:/usr/share/nginx/html
```

### 5. Containers verwijderen

Een container verwijderen:

```bash
docker rm webserver
```

Een gestopte container verwijderen:

```bash
docker rm $(docker ps -aq)
```

**Let op:** Een draaiende container moet eerst gestopt worden voordat deze verwijderd kan worden.

📌 [[3 - Docker Container Management]]

Containers beheren is een essentieel onderdeel van het werken met Docker. Dit hoofdstuk behandelt:

- Het starten en stoppen van containers (`docker run`, `docker stop`).
- Hoe je logs bekijkt (`docker logs`) en real-time statistieken verzamelt (`docker stats`).
- Hoe je containers beheert met `docker ps`, `docker exec`, en `docker inspect`.

📌 [[3 - Docker Container Management]]

---

## 4. Werken met Docker Images

Docker images vormen de bouwstenen van containers. Een **Docker image** is een alleen-lezen sjabloon die alles bevat wat nodig is om een container te draaien, inclusief de applicatiecode, runtime, bibliotheken en afhankelijkheden.

### 1. Docker Images ophalen en beheren

**Een image downloaden van Docker Hub:**

```bash
docker pull nginx
```

**Bekijk alle beschikbare images op je systeem:**

```bash
docker image ls
```

**Verwijder een ongebruikte image:**

```bash
docker rmi nginx
```

### 2. Eigen Docker Images bouwen

Een Dockerfile wordt gebruikt om aangepaste images te bouwen. Een voorbeeld:

```Dockerfile
# Stap 1: Kies een basisimage
FROM python:3.9-slim

# Stap 2: Stel de werkdirectory in
WORKDIR /app

# Stap 3: Kopieer afhankelijkheden en installeer ze
COPY requirements.txt .
RUN pip install -r requirements.txt

# Stap 4: Kopieer de rest van de bestanden
COPY . .

# Stap 5: Definieer het startcommando
CMD ["python", "app.py"]
```

**De image bouwen met een tag:**

```bash
docker build -t my-python-app .
```

### 3. Werken met image-tags

**Een bestaande image taggen:**

```bash
docker tag my-python-app myrepo/my-python-app:1.0
```

**Een image pushen naar Docker Hub:**

```bash
docker push myrepo/my-python-app:1.0
```

### 4. Optimalisatie van Docker Images

Om Docker images klein en efficiënt te houden, volgen hier enkele best practices:

- Gebruik **lichte basisimages** zoals `alpine` in plaats van volledige OS-images.
- Minimaliseer lagen door instructies in één `RUN`-commando te combineren.
- Gebruik `.dockerignore` om onnodige bestanden niet in de image op te nemen.
- Maak gebruik van **multi-stage builds** om alleen de essentiële bestanden in de uiteindelijke image op te nemen.

📌 [[4 - Working with Docker Images]]

Een **Docker Image** is de blauwdruk voor een container. In dit hoofdstuk leer je:

- Hoe je Docker images downloadt van **Docker Hub** (`docker pull`).
- Hoe je je eigen images bouwt met een Dockerfile.
- Hoe je images deelt via Docker Hub (`docker push`).

📌 [[4 - Working with Docker Images]]

---

## 5. Building Images with Dockerfiles

Dockerfiles zijn essentieel voor het bouwen van op maat gemaakte Docker-images. Dit hoofdstuk behandelt **geavanceerde optimalisatie** en **best practices** om efficiënte en goed presterende images te maken.

### 1. Wat is een Dockerfile?

Een **Dockerfile** is een tekstbestand met instructies om een Docker-image te bouwen. Elke instructie wordt als een laag in de image opgeslagen, wat caching en hergebruik mogelijk maakt.

### 2. Basisstructuur van een Dockerfile

Een typische Dockerfile bevat de volgende elementen:

```Dockerfile
# Basisimage
FROM python:3.9-slim

# Werkdirectory instellen
WORKDIR /app

# Afhankelijkheden kopiëren en installeren
COPY requirements.txt .
RUN pip install -r requirements.txt

# Applicatiebestanden kopiëren
COPY . .

# Poorten openstellen
EXPOSE 5000

# Startcommando instellen
CMD ["python", "app.py"]
```

### 3. Multi-stage builds

Met multi-stage builds minimaliseer je de grootte van een image door alleen de benodigde bestanden in de uiteindelijke build op te nemen.

```Dockerfile
# Eerste stage: buildomgeving
FROM node:18 AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Tweede stage: productieomgeving
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 4. Optimalisatie van Docker-images

Om de prestaties te verbeteren, gebruik de volgende best practices:

- **Minimaliseer lagen:** Combineer meerdere `RUN`-instructies.
- **Gebruik een `.dockerignore`-bestand:** Voorkomt dat onnodige bestanden in de image terechtkomen.
- **Gebruik lichte basisimages:** Kies `alpine` of `slim` varianten.
- **Gebruik caching:** Kopieer afhankelijkheden vóór codebestanden.

### 5. Veelgebruikte commando’s

- **Bouw een Docker-image:**
    
    ```bash
    docker build -t mijn-app .
    ```
    
- **Lijst van lokale images bekijken:**
    
    ```bash
    docker image ls
    ```
    
- **Een image verwijderen:**
    
    ```bash
    docker rmi mijn-app
    ```
    
- **Een image pushen naar Docker Hub:**
    
    ```bash
    docker push mijnrepo/mijn-app:1.0
    ```
    

📌 [[5 - Building Images with Dockerfiles]]

Naast het leren over Dockerfiles, richt dit hoofdstuk zich op **geavanceerde image-optimalisatie**:

- Gebruik van **multi-stage builds** om kleinere images te maken.
- Werken met **environment variables** en build arguments.
- Gebruik van `.dockerignore` om onnodige bestanden uit de build te houden.

📌 [[5 - Building Images with Dockerfiles]]

---

## 6. Networking and Data Persistence

Networking en data-persistentie zijn essentiële componenten van Docker-gebaseerde applicaties. Dit hoofdstuk behandelt hoe containers met elkaar en met de buitenwereld communiceren, en hoe je gegevens persistent kunt opslaan.

### 1. Docker-netwerken

Docker gebruikt virtuele netwerken om containers veilig en efficiënt met elkaar te laten communiceren. De drie belangrijkste netwerktypes zijn:

- **Bridge Network** (standaard): Containers op hetzelfde netwerk kunnen elkaar vinden via hun naam.
    
    ```bash
    docker network create my-bridge
    docker run -d --network my-bridge --name container1 nginx
    ```
    
- **Host Network**: De container deelt het netwerk van de hostmachine, waardoor deze direct toegankelijk is zonder port-mapping.
    
    ```bash
    docker run --network host nginx
    ```
    
- **None Network**: Volledige netwerkisolatie, nuttig voor containers die geen internettoegang nodig hebben.
    
    ```bash
    docker run --network none busybox
    ```
    

**Bekijk actieve netwerken:**

```bash
docker network ls
```

**Inspecteer een specifiek netwerk:**

```bash
docker network inspect my-bridge
```

### 2. Container-naar-container communicatie

Containers kunnen via DNS communiceren wanneer ze zich in hetzelfde Docker-netwerk bevinden. Bijvoorbeeld:

```bash
ping container1
```

Voor cross-network communicatie kan een container worden verbonden met meerdere netwerken:

```bash
docker network connect my-bridge container2
```

### 3. Data persistence in Docker

Containers zijn standaard stateless; wanneer een container wordt verwijderd, gaan alle gegevens verloren. Docker biedt twee methoden om gegevens persistent te maken:

#### a. **Docker Volumes**

Volumes worden beheerd door Docker en zijn de aanbevolen manier om gegevens op te slaan.

**Maak een volume aan:**

```bash
docker volume create my-volume
```

**Gebruik een volume in een container:**

```bash
docker run -d -v my-volume:/data --name app-container nginx
```

**Bekijk en beheer volumes:**

```bash
docker volume ls
```

#### b. **Bind Mounts**

Bind mounts koppelen een specifieke map van de host aan een container.

```bash
docker run -d -v /path/op/host:/data --name app-container nginx
```

### 4. Back-ups en herstel

Om een volume te back-uppen:

```bash
docker run --rm -v my-volume:/data -v $(pwd):/backup busybox tar cvf /backup/backup.tar /data
```

Om een back-up terug te zetten:

```bash
docker run --rm -v my-volume:/data -v $(pwd):/backup busybox tar xvf /backup/backup.tar -C /
```

📌 [[6 - Networking and Data Persistence in Docker]]

Docker maakt gebruik van een **virtueel netwerk** om containers met elkaar en met de buitenwereld te laten communiceren. Dit hoofdstuk bespreekt:

- **Bridge, Host en None** netwerken.
- Hoe containers met elkaar communiceren via **DNS en IP-adressen**.
- Het instellen van **Docker volumes** en **bind mounts** voor persistente opslag.

📌 [[6 - Networking and Data Persistence in Docker]]

---

## 7. SSH in Docker

SSH wordt soms gebruikt om containers te debuggen, onderhoud uit te voeren of toegang op afstand mogelijk te maken. Hoewel Docker andere ingebouwde tools biedt, zoals `docker exec` en `docker logs`, kan SSH nuttig zijn in specifieke scenario's.

### 1. Een container voorbereiden met SSH

Om SSH in een container te gebruiken, voeg je een OpenSSH-server toe tijdens de buildfase.

**Voorbeeld Dockerfile:**

```Dockerfile
FROM ubuntu:20.04
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:password' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

### 2. Container starten met SSH

**Bouw en draai de container:**

```bash
docker build -t ssh-container .
docker run -d -p 2222:22 ssh-container
```

- `-p 2222:22`: Koppelt poort 2222 op de host aan poort 22 in de container.

**Verbinden via SSH:**

```bash
ssh root@localhost -p 2222
```

### 3. Gebruik van SSH-sleutels

SSH-sleutels zijn veiliger dan wachtwoorden. Je kunt een publieke sleutel toevoegen aan de container.

**Publieke sleutel toevoegen:**

```bash
docker exec -it <container-id> /bin/bash
mkdir -p /root/.ssh
echo "<public-key>" >> /root/.ssh/authorized_keys
chmod 600 /root/.ssh/authorized_keys
```

**Verbinden zonder wachtwoord:**

```bash
ssh root@localhost -p 2222
```

### 4. Beveiliging van SSH in containers

- **Gebruik SSH-sleutels in plaats van wachtwoorden.**
- **Beperk toegang:** Gebruik Docker-netwerken of firewalls om SSH-toegang te beperken.
- **Verwijder SSH na debugging:** Als SSH niet meer nodig is, verwijder het dan om de aanvalsvectoren te minimaliseren.

### 5. Alternatieven voor SSH

Docker biedt ingebouwde tools die SSH vaak overbodig maken:

- **`docker exec`:** Voor toegang tot een draaiende container.
    
    ```bash
    docker exec -it <container-id> /bin/bash
    ```
    
- **`docker logs`:** Voor het bekijken van logbestanden.
    
    ```bash
    docker logs <container-id>
    ```
    
- **Bind mounts:** Gebruik bind mounts of volumes om bestanden over te brengen.

📌 [[7 - SSH in Docker]]

SSH wordt soms gebruikt om containers te debuggen of configuraties aan te passen. Dit hoofdstuk behandelt:

- Het opzetten van een **SSH-server in een container**.
- Het gebruik van **SSH-sleutels** voor veilige authenticatie.
- Alternatieven voor SSH zoals `docker exec` en `docker logs`.

📌 [[7 - SSH in Docker]]

---

## 8. Introduction to Development Containers

Development Containers (Dev Containers) bieden een gestandaardiseerde ontwikkelomgeving die draait binnen Docker-containers. Dit is een belangrijke tool voor teams die consistente workflows willen creëren, ongeacht het lokale systeem van de ontwikkelaars.

### 1. Wat zijn Dev Containers?

Dev Containers gebruiken een Docker-image om een gecontaineriseerde ontwikkelomgeving op te zetten. Hiermee worden afhankelijkheden, configuraties en ontwikkeltools vastgelegd in een `devcontainer.json`-bestand.

**Voordelen:**

- **Consistentie:** Alle teamleden werken in dezelfde omgeving.
- **Gemakkelijk te delen:** Projecten kunnen worden gedeeld via repositories.
- **Flexibiliteit:** Ondersteuning voor meerdere programmeertalen en frameworks.

### 2. Configureren van Dev Containers

Om een Dev Container te gebruiken, moet een `devcontainer.json`-bestand worden toegevoegd aan je project.

**Voorbeeld van een devcontainer.json:**

```json
{
  "name": "Python Development",
  "image": "python:3.9-slim",
  "postCreateCommand": "pip install -r requirements.txt",
  "extensions": [
    "ms-python.python",
    "esbenp.prettier-vscode"
  ],
  "settings": {
    "editor.formatOnSave": true
  }
}
```

### 3. Belangrijke onderdelen van een devcontainer.json

- **`name`:** Naam van de container.
- **`image`:** De Docker-image die als basis wordt gebruikt.
- **`postCreateCommand`:** Automatisch uitgevoerde commando’s na het maken van de container.
- **`extensions`:** VS Code-extensies die in de container worden geïnstalleerd.
- **`settings`:** Specifieke instellingen voor de ontwikkelomgeving.

### 4. Werken met Dev Containers in VS Code

1. Installeer de extensie **Remote - Containers**.
2. Open het project in VS Code.
3. Gebruik de command palette (Ctrl+Shift+P) en selecteer:
    
    ```
    Remote-Containers: Reopen in Container
    ```
    
4. VS Code bouwt en opent de containeromgeving.

### 5. Best Practices

- **Minimaliseer afhankelijkheden:** Gebruik lichte basisimages zoals `python:3.9-slim`.
- **Gebruik `.dockerignore`:** Voorkom dat onnodige bestanden worden gekopieerd.
- **Automatiseer configuraties:** Gebruik `postCreateCommand` voor taken zoals het installeren van afhankelijkheden.
- **Beveilig je container:** Voeg geen gevoelige gegevens toe aan het configuratiebestand; gebruik hiervoor omgevingsvariabelen.

📌 [[8 - Introduction to Development Containers]]

**Dev Containers** maken het mogelijk om ontwikkelomgevingen te standaardiseren. In dit hoofdstuk leer je:

- Hoe **VS Code Remote Containers** werkt.
- Het gebruik van een `devcontainer.json` bestand.
- Het automatiseren van installaties en configuraties binnen een container.

📌 [[8 - Introduction to Development Containers]]

---

## 9. Build Your Own DNS Server

Een **DNS-server** (Domain Name System) vertaalt domeinnamen zoals `www.example.com` naar IP-adressen, wat essentieel is voor internetcommunicatie. In dit hoofdstuk leer je hoe je je eigen DNS-server opzet, configureert en test met behulp van Docker en de Bind9 DNS-server.

### 1. Wat is een DNS-server?

Een DNS-server kan twee rollen vervullen:

- **Recursive DNS Resolver**: Handelt queries af namens een client door andere DNS-servers te raadplegen.
- **Authoritative DNS Server**: Geeft definitieve antwoorden over specifieke domeinen waarvoor het verantwoordelijk is.

### 2. Bind9 installeren

Bind9 is een populaire open-source DNS-server die kan worden gebruikt om een eigen DNS-server te bouwen.

#### Installatie op Ubuntu:

```bash
sudo apt update
sudo apt install bind9 bind9utils bind9-doc
```

Start en controleer de status:

```bash
sudo systemctl start bind9
sudo systemctl status bind9
```

### 3. Basisconfiguratie van Bind9

De configuratiebestanden van Bind9 bevinden zich in `/etc/bind/`.

#### a. Het configureren van opties:

Pas `/etc/bind/named.conf.options` aan om algemene opties zoals forwarding in te stellen.

```plaintext
options {
    directory "/var/cache/bind";
    forwarders {
        8.8.8.8; // Google DNS
        8.8.4.4;
    };
    allow-query { any; };
    recursion yes;
};
```

#### b. Zones definiëren:

Voeg zones toe in `/etc/bind/named.conf.local`.

```plaintext
zone "example.com" {
    type master;
    file "/etc/bind/zones/db.example.com";
};
```

Maak de map `/etc/bind/zones` aan en een zonebestand:

```bash
sudo mkdir /etc/bind/zones
sudo nano /etc/bind/zones/db.example.com
```

#### Voorbeeld zonebestand:

```plaintext
;
; Zone file for example.com
;
$TTL    604800
@       IN      SOA     ns1.example.com. admin.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.example.com.
@       IN      A       192.168.1.100
ns1     IN      A       192.168.1.100
www     IN      A       192.168.1.101
mail    IN      A       192.168.1.102
```

### 4. Bind9 in een Docker-container

Om Bind9 binnen Docker te draaien, maak je een Dockerfile:

```Dockerfile
FROM ubuntu:20.04
RUN apt-get update && apt-get install -y bind9
COPY named.conf.options /etc/bind/
COPY named.conf.local /etc/bind/
COPY zones/ /etc/bind/zones/
EXPOSE 53/udp
CMD ["/usr/sbin/named", "-g"]
```

Bouw en start de container:

```bash
docker build -t bind9-server .
docker run -d -p 53:53/udp --name dns-server bind9-server
```

### 5. Testen van je DNS-server

#### a. Test lokaal:

Gebruik `dig` of `nslookup` om queries uit te voeren:

```bash
dig @localhost example.com
```

```bash
nslookup example.com localhost
```

#### b. Test vanaf een externe client:

Stel de DNS-server in als primaire DNS-server in de netwerkconfiguratie van een externe client en voer dezelfde queries uit.

### 6. Beveiliging van je DNS-server

- **Beperk toegang:** Pas de configuratie aan om alleen specifieke IP-reeksen queries te laten uitvoeren:
    
    ```plaintext
    allow-query { 192.168.1.0/24; localhost; };
    ```
    
- **Implementeer DNSSEC:** Voorkomt DNS-spoofing door digitale handtekeningen te gebruiken.
- **Gebruik logging:** Schakel logging in om verdachte activiteiten te monitoren.

📌 [[9 - Build Your Own DNS Server]]

---

## 10. Linux Labs Overview

### Inleiding

Hoofdstuk 10 biedt een overzicht van alle praktische labs die zijn ontworpen om de kernconcepten van System Advanced Linux te versterken. De labs zijn gericht op het toepassen van theoretische kennis in real-world scenario's.

### Belangrijke Onderwerpen

#### 1. **Containerbeheer en optimalisatie**

- Leer hoe je containers efficiënt beheert met behulp van geavanceerde Docker-commando's zoals `docker exec`, `docker logs`, en `docker stats`.
- Werk met scripts om containers automatisch te starten, stoppen en verwijderen.
- Optimaliseer resourcegebruik binnen containers met aangepaste configuraties en monitoringtools.

#### 2. **Geavanceerde netwerkconfiguraties**

- Begrijp hoe Docker-netwerken werken, inclusief bridge-, host- en none-netwerken.
- Pas aangepaste netwerken toe voor geïsoleerde communicatie tussen containers.
- Werk met DNS-configuraties om container-naar-container communicatie te verbeteren.

#### 3. **Data persistentie**

- Gebruik Docker-volumes en bind mounts om data persistent op te slaan.
- Implementeer strategieën voor data-back-ups en herstel, inclusief volume migraties tussen hosts.

#### 4. **Debugging van containers**

- Maak gebruik van Docker-tools zoals `docker inspect` en `docker logs` om problemen binnen containers te identificeren.
- Debug applicatiefouten door interactieve toegang tot containers met `docker exec`.

### Hands-on Labs

De labs omvatten praktische oefeningen die je stapsgewijs begeleiden in:

- Het bouwen van geoptimaliseerde Docker-images met Dockerfiles.
- Het configureren van een Bind9 DNS-server in een container.
- Het implementeren van DevOps-concepten met behulp van CI/CD-pipelines in combinatie met Docker.

### Resultaat

Na het voltooien van deze labs zul je in staat zijn om:

1. Containers te beheren en te optimaliseren.
2. Netwerken en data persistentie te configureren voor productieomgevingen.
3. Problemen effectief te debuggen binnen gecontaineriseerde applicaties.

📌 [[10 - Linux Labs Overview]] hoofdstuk biedt een **samenvatting van alle labs** en hands-on oefeningen. De labs richten zich op:

- **Container beheer en optimalisatie.**
- **Geavanceerde netwerkconfiguraties.**
- **Data persistentie en debugging van containers.**

📌 [[10 - Linux Labs Overview]]

---

## Conclusie

Deze samenvatting biedt een overzicht van de belangrijkste concepten van **System Advanced Linux**. Elk hoofdstuk is gekoppeld aan een relevante les in Obsidian via **Atomic Links**, zodat je snel de benodigde informatie kunt vinden en verdiepen.

Gebruik deze gids als referentie om je voor te bereiden op examens en praktijkopdrachten! 🚀
