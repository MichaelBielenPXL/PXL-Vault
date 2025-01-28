# Docker Container Management

## Wat is container management?

Container management verwijst naar het proces van het maken, beheren, controleren en verwijderen van containers. Docker biedt een uitgebreide set tools en commando’s om containers eenvoudig te beheren, zowel voor lokale ontwikkeling als voor productieomgevingen.

---

## Containermanagement basics

### Containers maken

Het aanmaken van containers kan eenvoudig worden gedaan met het `docker run`-commando.

**Voorbeeld:**

```bash
docker run -d -p 8080:80 --name my-container nginx
```

- `-d`: Draait de container in de achtergrond (detached mode).
- `-p`: Stelt poorttoewijzing in, bijvoorbeeld 8080 op de host naar 80 in de container.
- `--name`: Geeft de container een naam (in dit geval `my-container`).
- `nginx`: De image die wordt gebruikt om de container te maken.

**Controleer actieve containers:**

```bash
docker ps
```

Dit geeft een lijst van alle draaiende containers.

**Bekijk alle containers, inclusief gestopte:**

```bash
docker ps -a
```

---

### Containers stoppen en verwijderen

**Stop een container:**

```bash
docker stop my-container
```

**Verwijder een container:**

```bash
docker rm my-container
```

> **Let op**: Een container moet eerst worden gestopt voordat deze kan worden verwijderd.

**Forceer verwijderen:**

```bash
docker rm -f my-container
```

Dit verwijdert een container ongeacht of deze draait.

---

## Interactie met containers

### Shell toegang tot een container

Je kunt interactief een container binnenstappen met behulp van `docker exec` of `docker run`.

**Gebruik `docker exec` om een shell te starten in een draaiende container:**

```bash
docker exec -it my-container /bin/bash
```

- `-i`: Interactieve modus.
- `-t`: Koppelt een pseudo-terminal.

**Start een nieuwe container met een shell:**

```bash
docker run -it ubuntu /bin/bash
```

Dit opent een bash-shell in een nieuwe Ubuntu-container.

---

### Bestanden kopiëren

Je kunt bestanden tussen de host en een container kopiëren met `docker cp`.

**Van host naar container:**

```bash
docker cp bestand.txt my-container:/pad/in/container
```

**Van container naar host:**

```bash
docker cp my-container:/pad/in/container/bestand.txt ./
```

---

## Container logs

Bekijk de logs van een container met het `docker logs`-commando.

**Alle logs weergeven:**

```bash
docker logs my-container
```

**Real-time logs volgen:**

```bash
docker logs -f my-container
```

- `-f`: Volgt de logs in real-time.

**Beperk het aantal weergegeven regels:**

```bash
docker logs --tail 50 my-container
```

Geeft de laatste 50 regels weer.

---

## Container inspecteren

Met `docker inspect` kun je gedetailleerde informatie over een container bekijken.

**Inspecteer een container:**

```bash
docker inspect my-container
```

Dit toont een JSON-uitvoer met alle configuratie- en statusdetails van de container.

**Filter specifieke informatie:**

```bash
docker inspect -f '{{.NetworkSettings.IPAddress}}' my-container
```

Dit retourneert bijvoorbeeld alleen het IP-adres van de container.

---

## Container netwerken

Docker containers communiceren via netwerken. Je kunt standaard Docker-netwerken gebruiken of aangepaste netwerken aanmaken.

**Bekijk beschikbare netwerken:**

```bash
docker network ls
```

### Aangepast netwerk maken

Met een aangepast netwerk kun je containers isoleren of specifieke configuraties instellen.

**Maak een netwerk aan:**

```bash
docker network create my-network
```

**Container verbinden met een netwerk:**

```bash
docker network connect my-network my-container
```

**Container loskoppelen van een netwerk:**

```bash
docker network disconnect my-network my-container
```

---

## Persistentie met volumes

Containers zijn standaard stateless: data gaat verloren als de container wordt verwijderd. Voor persistente opslag gebruik je **volumes**.

### Volumes maken en gebruiken

**Maak een volume aan:**

```bash
docker volume create my-volume
```

**Gebruik een volume in een container:**

```bash
docker run -d -v my-volume:/data --name my-container nginx
```

- `-v my-volume:/data`: Koppelt het volume `my-volume` aan de map `/data` in de container.

### Data bekijken

Bekijk welke volumes beschikbaar zijn:

```bash
docker volume ls
```

Verwijder een volume:

```bash
docker volume rm my-volume
```

---

## Automatisering met Docker Compose

Voor het beheren van meerdere containers kun je **Docker Compose** gebruiken. Hiermee definieer je alle configuraties in een enkel `docker-compose.yml`-bestand.

### Basisvoorbeeld van `docker-compose.yml`:

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: example
```

**Start alle services:**

```bash
docker-compose up -d
```

**Stop alle services:**

```bash
docker-compose down
```

---

## Best Practices voor containermanagement

1. **Geef containers herkenbare namen:** Gebruik `--name` om containers eenvoudig te identificeren.
2. **Gebruik volumes voor data:** Zorg ervoor dat belangrijke gegevens worden opgeslagen in volumes om dataverlies te voorkomen.
3. **Maak gebruik van netwerken:** Beheer communicatie tussen containers met aangepaste Docker-netwerken.
4. **Automatiseer taken met Docker Compose:** Versnel en vereenvoudig het beheer van multi-container toepassingen.
5. **Verwijder ongebruikte resources:** Gebruik `docker system prune` om ongebruikte containers, netwerken en volumes op te schonen:
    
    ```bash
    docker system prune
    ```
    

---

## Conclusie

Docker biedt krachtige tools voor het beheren van containers. Door gebruik te maken van commando's zoals `docker run`, `docker ps`, en `docker logs`, kun je containers eenvoudig creëren, controleren en debuggen. Door volumes en netwerken te benutten, kun je persistente opslag en veilige communicatie tussen containers realiseren. Met best practices en tools zoals Docker Compose kun je containerbeheer verder stroomlijnen voor zowel ontwikkeling als productie.