# Dockerfile Introduction

## Wat is een Dockerfile?

Een **Dockerfile** is een tekstbestand waarin je alle stappen definieert die nodig zijn om een Docker container image te bouwen. Het is de blauwdruk van een container en maakt het mogelijk om reproduceerbare en consistente omgevingen te creëren.

### Belangrijkste kenmerken:

- **Reproduceerbaarheid**: Een Dockerfile zorgt ervoor dat een image op elke machine consistent kan worden gebouwd.
- **Simpel te gebruiken**: Door gebruik te maken van gestandaardiseerde instructies kun je complexe omgevingen eenvoudig configureren.
- **Modulair**: Elke instructie in een Dockerfile bouwt voort op de vorige en creëert een nieuwe laag.

Een Dockerfile begint altijd met een basis image (`FROM`) en voegt vervolgens lagen toe door instructies zoals `COPY`, `RUN` en `CMD`.

---

## Belangrijke Dockerfile-instructies

Hieronder volgt een overzicht van de meest gebruikte Dockerfile-instructies:

### 1. `FROM`

- **Doel**: Geeft de basis image op waarop alle andere lagen worden gebouwd.
- **Syntax**:
    
    ```Dockerfile
    FROM <image>:<tag>
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    FROM node:20-alpine
    ```
    
    - Gebruikt een lichte Node.js-basis image gebaseerd op Alpine Linux.

---

### 2. `WORKDIR`

- **Doel**: Stelt de werkdirectory in voor alle volgende instructies in de Dockerfile.
- **Voordeel**: Zorgt ervoor dat bestanden georganiseerd blijven en commando's vanuit dezelfde directory worden uitgevoerd.
- **Syntax**:
    
    ```Dockerfile
    WORKDIR <pad>
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    WORKDIR /app
    ```
    
    - Als `/app` nog niet bestaat, wordt deze directory automatisch aangemaakt.

---

### 3. `COPY`

- **Doel**: Kopieert bestanden of mappen van de build context (bijvoorbeeld je lokale projectmap) naar de container.
- **Syntax**:
    
    ```Dockerfile
    COPY <bron> <doel>
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    COPY package.json /app/package.json
    ```
    
    - Kopieert alleen het bestand `package.json` naar de map `/app` in de container.

---

### 4. `ADD`

- Lijkt op `COPY`, maar biedt extra functionaliteit:
    - Kan bestanden downloaden van een URL.
    - Kan gecomprimeerde bestanden (zoals `.tar.gz`) automatisch uitpakken.
- **Voorbeeld**:
    
    ```Dockerfile
    ADD http://example.com/file.tar.gz /tmp/file.tar.gz
    ```
    

**Best Practice**: Gebruik liever `COPY` tenzij je de extra functionaliteiten van `ADD` nodig hebt.

---

### 5. `RUN`

- **Doel**: Voert een commando uit in een nieuwe laag bovenop de huidige image.
- Wordt vaak gebruikt voor:
    - Installeren van software.
    - Configureren van de omgeving.
- **Syntax**:
    
    ```Dockerfile
    RUN <commando>
    ```
    
- Voorbeelden:
    
    ```Dockerfile
    RUN apt-get update && apt-get install -y curl
    RUN npm install
    ```
    
    - Installeert respectievelijk systeem- en Node.js-afhankelijkheden.

**Tips**:

- Combineer meerdere commando's in één `RUN`-instructie om het aantal lagen te minimaliseren:
    
    ```Dockerfile
    RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
    ```
    

---

### 6. `CMD`

- **Doel**: Stelt het standaardcommando in dat wordt uitgevoerd wanneer de container start.
- **Syntax**:
    
    ```Dockerfile
    CMD ["executable", "param1", "param2"]
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    CMD ["node", "app.js"]
    ```
    
    - Start automatisch `node app.js` wanneer de container draait.

**Opmerking**: Een container kan slechts één `CMD`-instructie hebben. Als er meerdere `CMD`-instructies in een Dockerfile staan, wordt alleen de laatste uitgevoerd.

---

### 7. `ENTRYPOINT`

- **Doel**: Specificeert het standaardprogramma dat wordt uitgevoerd in de container, met de mogelijkheid om extra argumenten door te geven tijdens runtime.
- **Voorbeeld**:
    
    ```Dockerfile
    ENTRYPOINT ["python", "script.py"]
    ```
    
    - Draait standaard `python script.py` bij het starten van de container.

**Verschil met `CMD`**:

- `CMD` kan worden overschreven door argumenten in de `docker run`-opdracht.
- `ENTRYPOINT` blijft altijd actief, zelfs met extra runtime-argumenten.

---

### 8. `EXPOSE`

- **Doel**: Documenteert de netwerkpoorten die door de container worden gebruikt.
- **Syntax**:
    
    ```Dockerfile
    EXPOSE <poort>
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    EXPOSE 8080
    ```
    
    - Geeft aan dat de container luistert op poort 8080.

**Let op**: `EXPOSE` opent geen poorten; hiervoor moet je de `-p` vlag gebruiken tijdens het starten van de container:

```bash
docker run -p 8080:8080 <image>
```

---

### 9. `ENV`

- **Doel**: Stelt omgevingsvariabelen in die beschikbaar zijn in de container.
- **Syntax**:
    
    ```Dockerfile
    ENV <variabele> <waarde>
    ```
    
- Voorbeeld:
    
    ```Dockerfile
    ENV NODE_ENV=production
    ```
    

---

## Layering en caching

Docker gebruikt een **laagstructuur** bij het bouwen van images. Elke instructie in de Dockerfile creëert een nieuwe laag.

- **Caching**:
    - Ongewijzigde lagen worden hergebruikt bij opeenvolgende builds, wat de buildtijd versnelt.
- **Best practices**:
    - Plaats weinig veranderende instructies, zoals `FROM` en `COPY`, bovenaan de Dockerfile.
    - Combineer meerdere `RUN`-instructies in één commando om het aantal lagen te minimaliseren.

---

## Multi-stage builds

Met multi-stage builds kun je de image-grootte verkleinen door alleen essentiële bestanden en configuraties in de uiteindelijke productie-image op te nemen.

**Voorbeeld:**

```Dockerfile
# Stage 1: Build
FROM node:20 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2: Production
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

- In dit voorbeeld:
    - **Builder stage**: Compileert de applicatie.
    - **Production stage**: Bevat alleen de gecompileerde bestanden, zonder buildtools.

---

## Hands-on: Een eenvoudige NGINX-website

Hieronder een stapsgewijze handleiding om een statische website te hosten met NGINX en Docker.

### 1. Maak een projectdirectory

```bash
mkdir my-nginx-site
cd my-nginx-site
```

### 2. Voeg een `index.html` toe

```html
<!DOCTYPE html>
<html>
  <body>Hello from Docker!</body>
</html>
```

### 3. Schrijf een Dockerfile

```Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 4. Bouw en draai de container

- **Bouwen**:
    
    ```bash
    docker build -t my-nginx-site .
    ```
    
- **Starten**:
    
    ```bash
    docker run -d -p 8080:80 my-nginx-site
    ```
    

### 5. Test de website

- Open een browser en ga naar:
    
    ```
    http://localhost:8080
    ```
    

---

## Best Practices

1. **Minimaliseer lagen**:
    
    - Combineer meerdere `RUN`-instructies:
        
        ```Dockerfile
        RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
        ```
        
2. **Gebruik een `.dockerignore`**:
    
    - Vermijd het kopiëren van onnodige bestanden:
        
        ```
        node_modules
        .git
        ```
        
3. **Gebruik lichte basisafbeeldingen**:
    
    - Kies images zoals `alpine` om de grootte van je container te beperken.
4. **Beveilig je Dockerfile**:
    
    - Voeg geen gevoelige gegevens (zoals wachtwoorden) toe in je Dockerfile.

---

## Conclusie

Dockerfiles zijn een krachtig hulpmiddel om containers consistent en schaalbaar te bouwen. Door gebruik te maken van best practices en efficiënte instructies kun je robuuste en veilige container images maken. Van eenvoudige applicaties tot complexe productieomgevingen, Dockerfiles vormen de basis van moderne containerisatie.