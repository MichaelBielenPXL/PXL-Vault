# Building Images with Dockerfiles

## Wat zijn Dockerfiles?

Een **Dockerfile** is een tekstbestand dat een reeks instructies bevat om een Docker image te bouwen. Het fungeert als een blauwdruk voor hoe de image moet worden samengesteld en welke componenten worden opgenomen. Door een Dockerfile te gebruiken, kun je een consistente, herhaalbare container bouwen die dezelfde resultaten levert, ongeacht waar deze wordt uitgevoerd.

---

## Structuur van een Dockerfile

Een Dockerfile bevat een reeks gestandaardiseerde instructies die worden uitgevoerd in de volgorde waarin ze zijn geschreven. Enkele van de meest voorkomende instructies zijn:

### 1. `FROM`

- **Doel**: Definieert de basis image waarmee de build begint.
- **Voorbeeld:**
    
    ```Dockerfile
    FROM ubuntu:20.04
    ```
    
    - Start met de officiële Ubuntu 20.04 image.

### 2. `WORKDIR`

- **Doel**: Stelt de werkdirectory in waar de commando's worden uitgevoerd.
- **Voorbeeld:**
    
    ```Dockerfile
    WORKDIR /app
    ```
    

### 3. `COPY`

- **Doel**: Kopieert bestanden of mappen van de host naar de container.
- **Voorbeeld:**
    
    ```Dockerfile
    COPY . /app
    ```
    
    - Kopieert alle bestanden uit de huidige directory naar `/app` in de container.

### 4. `RUN`

- **Doel**: Voert een commando uit tijdens de buildfase en voegt het resultaat toe aan de image.
- **Voorbeeld:**
    
    ```Dockerfile
    RUN apt-get update && apt-get install -y curl
    ```
    
    - Installeert `curl` in de container.

### 5. `CMD`

- **Doel**: Definieert het standaardcommando dat wordt uitgevoerd wanneer de container start.
- **Voorbeeld:**
    
    ```Dockerfile
    CMD ["node", "app.js"]
    ```
    
    - Start een Node.js-applicatie.

---

## Een eenvoudige Dockerfile bouwen

Hieronder een voorbeeld van een Dockerfile voor een Node.js-toepassing:

```Dockerfile
# Stap 1: Kies een basis image
FROM node:16-alpine

# Stap 2: Stel de werkdirectory in
WORKDIR /app

# Stap 3: Kopieer projectbestanden naar de container
COPY . .

# Stap 4: Installeer afhankelijkheden
RUN npm install

# Stap 5: Definieer het standaard startcommando
CMD ["node", "app.js"]
```

### Bouw de image

Gebruik het volgende commando om de Dockerfile te bouwen:

```bash
docker build -t mijn-app:1.0 .
```

### Controleer de image

Bekijk de lijst van beschikbare images:

```bash
docker image ls
```

---

## Dockerfiles en lagen

Elke instructie in een Dockerfile creëert een nieuwe laag in de image. Docker gebruikt deze lagen om builds te versnellen door ongewijzigde lagen uit de cache te halen.

### Voorbeeld van lagen:

```Dockerfile
FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

- **Lagen in dit voorbeeld:**
    1. `FROM python:3.10`: Basis image.
    2. `WORKDIR /app`: Werkdirectory instellen.
    3. `COPY requirements.txt .`: Alleen `requirements.txt` wordt toegevoegd.
    4. `RUN pip install -r requirements.txt`: Installeert Python-afhankelijkheden.
    5. `COPY . .`: Kopieert overige projectbestanden.

**Caching:** Als `requirements.txt` niet is gewijzigd, slaat Docker de cache op voor de `RUN pip install`-laag.

---

## Best practices voor Dockerfiles

1. **Minimaliseer lagen:**
    
    - Combineer meerdere commando's in één `RUN`-instructie:
        
        ```Dockerfile
        RUN apt-get update && apt-get install -y \
            curl \
            vim && \
            rm -rf /var/lib/apt/lists/*
        ```
        
2. **Gebruik lichte basisimages:**
    
    - Kies `alpine`-afbeeldingen wanneer mogelijk om de image-grootte te verkleinen.
    - Voorbeeld:
        
        ```Dockerfile
        FROM python:3.10-alpine
        ```
        
3. **Gebruik `.dockerignore`:**
    
    - Vermijd het kopiëren van onnodige bestanden naar de container.
    - Voorbeeld `.dockerignore`:
        
        ```plaintext
        node_modules
        .git
        *.log
        ```
        
4. **Specificeer exacte afhankelijkheden:**
    
    - Gebruik versies om onverwachte wijzigingen te voorkomen:
        
        ```Dockerfile
        RUN pip install flask==2.0.1
        ```
        
5. **Beveilig je Dockerfile:**
    
    - Voeg geen gevoelige informatie toe, zoals wachtwoorden of API-sleutels.
    - Gebruik in plaats daarvan omgevingsvariabelen.

---

## Multi-stage builds

Multi-stage builds verminderen de grootte van de uiteindelijke image door buildtijdtools en tijdelijke bestanden te verwijderen.

### Voorbeeld:

```Dockerfile
# Stage 1: Build
FROM node:16 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Production
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
```

- **Builder stage:** Compileert de applicatie.
- **Production stage:** Bevat alleen de gecompileerde bestanden en NGINX.

**Bouw de image:**

```bash
docker build -t mijn-app:production .
```

---

## Veelvoorkomende valkuilen

1. **Te veel lagen:**
    
    - Elke `RUN`, `COPY` of `ADD` creëert een nieuwe laag. Minimaliseer lagen om de image kleiner te maken.
2. **Onnodige bestanden:**
    
    - Zorg ervoor dat tijdelijke of lokale bestanden niet worden gekopieerd naar de container.
3. **Geen caching benutten:**
    
    - Plaats zelden veranderende instructies bovenaan je Dockerfile om caching te optimaliseren.
4. **Hardgecodeerde waarden:**
    
    - Vermijd het hardcoderen van waarden. Gebruik omgevingsvariabelen:
        
        ```Dockerfile
        ENV PORT=8080
        EXPOSE $PORT
        ```
        

---

## Conclusie

Dockerfiles zijn een krachtig hulpmiddel om consistente en schaalbare container images te bouwen. Door best practices te volgen, zoals het minimaliseren van lagen, het gebruik van multi-stage builds en het optimaliseren van caching, kun je efficiënte en veilige images maken. Of je nu een eenvoudige applicatie bouwt of een complexe productieomgeving, een goed ontworpen Dockerfile is de sleutel tot succes.