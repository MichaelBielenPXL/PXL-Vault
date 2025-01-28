# Working with Docker Images

## Wat zijn Docker Images?

Docker images zijn read-only sjablonen waarmee containers worden gemaakt. Een image bevat alle componenten die nodig zijn om een applicatie uit te voeren, zoals de applicatiecode, bibliotheken, afhankelijkheden en configuratiebestanden. Images zijn **immutable**, wat betekent dat ze niet worden gewijzigd nadat ze zijn gemaakt.

---

## Basisprincipes van Docker Images

### Een Docker Image verkrijgen

Docker images kunnen worden gedownload van **Docker Hub**, een online repository waar duizenden officiële en community-gebaseerde images beschikbaar zijn.

**Een image downloaden:**

```bash
docker pull <image>:<tag>
```

- `<image>`: De naam van de gewenste image.
- `<tag>`: Een specifieke versie van de image (standaard is `latest`).

**Voorbeeld:**

```bash
docker pull nginx:latest
```

---

### Lijst van lokale images bekijken

Om een overzicht te krijgen van alle gedownloade images op je machine:

```bash
docker image ls
```

- Output toont informatie zoals:
    - **Repository**: Naam van de image.
    - **Tag**: Versienummer of label.
    - **Image ID**: Unieke identifier.
    - **Size**: Grootte van de image.

**Voorbeeld output:**

```plaintext
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    2b1234c3a123   2 weeks ago   133MB
```

---

## Een Image bouwen

Docker images worden vaak gebouwd met behulp van een **Dockerfile**, waarin de instructies voor het bouwen van de image staan beschreven.

**Voorbeeld Dockerfile:**

```Dockerfile
FROM node:16-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

### Image bouwen met een Dockerfile

Gebruik het `docker build`-commando om een image te bouwen:

```bash
docker build -t <naam>:<tag> <path>
```

- `-t`: Geeft een naam en tag aan de image.
- `<path>`: Pad naar de directory met de Dockerfile (meestal `.`).

**Voorbeeld:**

```bash
docker build -t myapp:1.0 .
```

### Opgebouwde images controleren

Na het bouwen kun je je image vinden in de lijst van lokale images:

```bash
docker image ls
```

---

## Tags beheren

### Wat zijn tags?

Tags worden gebruikt om specifieke versies van een image te identificeren. Hierdoor kun je eenvoudig onderscheid maken tussen verschillende versies van dezelfde applicatie.

### Image taggen

Gebruik `docker tag` om een image een extra tag te geven:

```bash
docker tag <image>:<tag> <nieuwenaam>:<nieuwe-tag>
```

**Voorbeeld:**

```bash
docker tag myapp:1.0 myapp:latest
```

### Tags verwijderen

Je kunt een specifieke tag verwijderen door de image te verwijderen:

```bash
docker rmi <image>:<tag>
```

**Voorbeeld:**

```bash
docker rmi myapp:1.0
```

---

## Images delen

### Een image pushen naar Docker Hub

1. **Login bij Docker Hub:**
    
    ```bash
    docker login
    ```
    
    Voer je Docker Hub-gebruikersnaam en wachtwoord in.
    
2. **Image taggen met je Docker Hub-gebruikersnaam:**
    
    ```bash
    docker tag <image>:<tag> <gebruikersnaam>/<repository>:<tag>
    ```
    
    **Voorbeeld:**
    
    ```bash
    docker tag myapp:1.0 myusername/myapp:1.0
    ```
    
3. **Push de image naar Docker Hub:**
    
    ```bash
    docker push <gebruikersnaam>/<repository>:<tag>
    ```
    
    **Voorbeeld:**
    
    ```bash
    docker push myusername/myapp:1.0
    ```
    

### Images verwijderen

Als je een image niet meer nodig hebt, kun je deze verwijderen met:

```bash
docker rmi <image>:<tag>
```

**Voorbeeld:**

```bash
docker rmi nginx:latest
```

---

## Optimalisatie van Docker Images

### Minimaliseer de image-grootte

1. **Gebruik lichte basisimages**:
    
    - Kies voor `alpine` of andere minimalistische Linux-distributies.
    - Voorbeeld:
        
        ```Dockerfile
        FROM node:16-alpine
        ```
        
2. **Verwijder ongebruikte bestanden:**
    
    - Gebruik `RUN`-commando’s om tijdelijke bestanden te verwijderen.
    - Voorbeeld:
        
        ```Dockerfile
        RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
        ```
        
3. **Combineer `RUN`-instructies:**
    
    - Minimaliseer het aantal lagen door commando’s te combineren:
        
        ```Dockerfile
        RUN apt-get update && apt-get install -y \
            curl \
            vim && \
            rm -rf /var/lib/apt/lists/*
        ```
        

---

## Inspectie en beheer

### Inspecteer een image

Gebruik `docker inspect` om gedetailleerde informatie over een image te bekijken:

```bash
docker inspect <image>:<tag>
```

**Specifieke details filteren:**

```bash
docker inspect -f '{{.Config.Cmd}}' myapp:1.0
```

- Hiermee kun je bijvoorbeeld het standaard opstartcommando van de image bekijken.

---

## Best Practices

1. **Gebruik officiële basisimages:**
    
    - Kies altijd voor goed onderhouden, veilige basisimages.
2. **Beperk afhankelijkheden:**
    
    - Installeer alleen de software die absoluut nodig is.
3. **Gebruik `.dockerignore`**:
    
    - Vermijd het kopiëren van onnodige bestanden:
        
        ```plaintext
        node_modules
        .git
        .env
        ```
        
4. **Test je images regelmatig:**
    
    - Controleer of je image correct werkt en geen onnodige bestanden bevat.
5. **Rebuild regelmatig:**
    
    - Door een image opnieuw te bouwen, profiteer je van de nieuwste beveiligingspatches in de basisimage.

---

## Conclusie

Docker images zijn de kern van containerisatie en vormen de bouwstenen voor het draaien van containers. Door zorgvuldig om te gaan met tags, optimalisatie en best practices, kun je efficiënte, veilige en schaalbare containeromgevingen bouwen. Of je nu een ontwikkelaar bent die lokaal werkt of een team ondersteunt in productie, het begrijpen van Docker images is essentieel om het meeste uit containertechnologie te halen.