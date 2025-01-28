# Networking and Data Persistence in Docker

## Netwerken in Docker

Docker maakt het mogelijk om containers eenvoudig met elkaar en met de buitenwereld te verbinden via netwerken. Dit is essentieel voor het bouwen van applicaties die meerdere services bevatten, zoals een frontend, backend en database.

---

## Basisprincipes van Docker-netwerken

### Standaard Docker-netwerken

Docker creëert standaard drie netwerken:

1. **bridge**:
    
    - Het standaard netwerk voor containers.
    - Containers op hetzelfde bridge-netwerk kunnen met elkaar communiceren via hun containernaam.
2. **host**:
    
    - Gebruikt de netwerkstack van de host, waardoor er geen isolatie is tussen de container en de host.
3. **none**:
    
    - Containers hebben geen netwerktoegang.

**Bekijk alle netwerken:**

```bash
docker network ls
```

---

### Een aangepast netwerk maken

Met aangepaste netwerken kun je de communicatie en isolatie van containers beter beheren.

**Netwerk aanmaken:**

```bash
docker network create my-network
```

**Container verbinden met een netwerk:**

```bash
docker run --network my-network --name my-container nginx
```

**Bestaande container aan een netwerk koppelen:**

```bash
docker network connect my-network my-container
```

**Container loskoppelen van een netwerk:**

```bash
docker network disconnect my-network my-container
```

---

### Communicatie tussen containers

Containers in hetzelfde netwerk kunnen met elkaar communiceren via hun **containernaam** of **IP-adres**.

**Voorbeeld:**

- Container A draait op de naam `web`.
- Container B kan communiceren met Container A via:
    
    ```bash
    curl http://web
    ```
    

---

## Poorten en toegang beheren

### Poorten mappen

Je kunt poorten van de host koppelen aan poorten van de container met de `-p` vlag.

**Syntax:**

```bash
docker run -p <host_port>:<container_port> <image>
```

**Voorbeeld:**

```bash
docker run -p 8080:80 nginx
```

- Verbindt poort 8080 op de host met poort 80 in de container.

### Meerdere poorten

Je kunt meerdere poorten mappen door meerdere `-p` vlaggen te gebruiken:

```bash
docker run -p 8080:80 -p 8443:443 nginx
```

---

## Data Persistence in Docker

Containers zijn standaard **stateless**: alle gegevens gaan verloren wanneer een container wordt gestopt of verwijderd. Om data te behouden, kun je volumes of bind mounts gebruiken.

---

### Volumes

Volumes worden beheerd door Docker en bieden een consistente en veilige manier om gegevens op te slaan.

**Voordelen:**

- Data blijft bestaan, zelfs als de container wordt verwijderd.
- Geïsoleerd van de host.

**Volume aanmaken:**

```bash
docker volume create my-volume
```

**Volume gebruiken:**

```bash
docker run -v my-volume:/data nginx
```

- `my-volume` is het volume.
- `/data` is de map in de container waar het volume wordt gekoppeld.

**Lijst van volumes bekijken:**

```bash
docker volume ls
```

**Volume verwijderen:**

```bash
docker volume rm my-volume
```

---

### Bind Mounts

Bind mounts koppelen specifieke mappen van de host aan een container. Hierdoor kun je data op de host direct bewerken.

**Voordelen:**

- Handig tijdens ontwikkeling.
- Toegang tot specifieke hostbestanden.

**Syntax:**

```bash
docker run -v /path/on/host:/path/in/container nginx
```

**Voorbeeld:**

```bash
docker run -v /home/user/data:/data nginx
```

---

## Verschillen tussen Volumes en Bind Mounts

|**Kenmerk**|**Volumes**|**Bind Mounts**|
|---|---|---|
|Beheer|Door Docker|Door de gebruiker|
|Locatie|Beheerd door Docker|Specifieke map op de host|
|Gebruik|Aanbevolen voor productie|Handig tijdens ontwikkeling|

---

## Data back-ups

### Een volume back-uppen

Je kunt een back-up maken van een volume door het te kopiëren naar een map op de host.

**Back-up maken:**

```bash
docker run --rm -v my-volume:/data -v /backup:/backup busybox tar cvf /backup/backup.tar /data
```

**Back-up terugzetten:**

```bash
docker run --rm -v my-volume:/data -v /backup:/backup busybox tar xvf /backup/backup.tar -C /
```

---

## Best Practices

1. **Gebruik volumes voor persistente data:**
    
    - Data wordt veilig beheerd en blijft bestaan, zelfs als containers worden verwijderd.
2. **Beperk bind mounts:**
    
    - Gebruik deze alleen tijdens ontwikkeling om te voorkomen dat hostbestanden per ongeluk worden gewijzigd.
3. **Gebruik netwerken voor isolatie:**
    
    - Verbind containers alleen met netwerken die ze nodig hebben om de veiligheid te verhogen.
4. **Documenteer poorttoewijzingen:**
    
    - Zorg ervoor dat andere ontwikkelaars begrijpen welke poorten worden gebruikt en waarom.
5. **Automatiseer met Docker Compose:**
    
    - Gebruik een `docker-compose.yml`-bestand om netwerken, volumes en services te definiëren.

---

## Conclusie

Het begrijpen van Docker-netwerken en data persistence is essentieel voor het bouwen van robuuste containeromgevingen. Door gebruik te maken van aangepaste netwerken, volumes en bind mounts kun je veilige, schaalbare en efficiënte applicaties ontwerpen. Met de juiste best practices kun je de volledige kracht van Docker benutten in zowel ontwikkel- als productieomgevingen.