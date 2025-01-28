# Linux Labs Overview

## Inleiding

Dit document biedt een uitgebreide gids van 2000 woorden over hoofdstuk 10 uit de Linux Labs-handleiding. Het is gericht op het versterken van kennis en praktische vaardigheden met betrekking tot containers, netwerken, data persistence en DevOps-praktijken.

---

## Hoofdstuk 10: Overzicht van alle labs

### 1. **Container Management**

Containers zijn de bouwstenen van moderne softwareontwikkeling. Het doel van deze sectie is om beheertechnieken voor containers te leren en te perfectioneren.

#### a. Containers aanmaken

Het `docker run`-commando wordt gebruikt om containers te starten. Het commando heeft een breed scala aan opties waarmee je containers kunt configureren.

**Voorbeeld:**

```bash
docker run -d -p 8080:80 --name my-container nginx
```

- `-d`: Start de container in de achtergrond.
- `-p 8080:80`: Verbindt poort 8080 op de host met poort 80 in de container.
- `--name my-container`: Geeft de container een naam.
- `nginx`: Specificeert de image die wordt gebruikt.

**Belangrijke aanvullende opties:**

- `-e`: Stel omgevingsvariabelen in.
- `--restart`: Configureer automatisch herstarten van containers (bijvoorbeeld `always` of `on-failure`).

#### b. Containers beheren

Docker biedt krachtige tools om actieve en gestopte containers te beheren.

**Actieve containers bekijken:**

```bash
docker ps
```

**Alle containers (inclusief gestopte) bekijken:**

```bash
docker ps -a
```

**Stop een container:**

```bash
docker stop <container-id>
```

**Verwijder een container:**

```bash
docker rm <container-id>
```

---

### 2. **Docker Images**

Docker images vormen de basis van containers. Begrip van hoe je met images werkt, is cruciaal voor efficiënte containerisatie.

#### a. Images downloaden en beheren

**Een image downloaden:**

```bash
docker pull nginx
```

**Bekijk lokale images:**

```bash
docker image ls
```

#### b. Bouw je eigen images

Images worden gebouwd met behulp van Dockerfiles, waarin alle stappen staan beschreven die nodig zijn om een containeromgeving te creëren.

**Voorbeeld Dockerfile:**

```Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

**Bouw de image:**

```bash
docker build -t my-python-app .
```

#### c. Images pushen naar Docker Hub

1. **Login:**
    
    ```bash
    docker login
    ```
    
2. **Tag je image:**
    
    ```bash
    docker tag my-python-app username/my-python-app:1.0
    ```
    
3. **Push je image:**
    
    ```bash
    docker push username/my-python-app:1.0
    ```
    

---

### 3. **Netwerken in Docker**

Netwerken verbinden containers en maken communicatie mogelijk tussen services.

#### a. Docker-netwerkconcepten

Docker biedt drie standaard netwerken:

1. **bridge**: Standaard netwerktype, geschikt voor communicatie tussen containers op dezelfde host.
2. **host**: Container deelt de netwerkstack van de host.
3. **none**: Geen netwerktoegang.

**Bekijk netwerken:**

```bash
docker network ls
```

#### b. Aangepaste netwerken

Je kunt aangepaste netwerken maken om containers te isoleren en configureren.

**Maak een netwerk aan:**

```bash
docker network create my-network
```

**Verbind een container met een netwerk:**

```bash
docker network connect my-network my-container
```

---

### 4. **Data Persistence**

Data persistence is essentieel voor applicaties die gegevens opslaan, zoals databases.

#### a. Volumes

**Maak een volume aan:**

```bash
docker volume create my-volume
```

**Gebruik een volume in een container:**

```bash
docker run -v my-volume:/data nginx
```

#### b. Bind mounts

Bind mounts koppelen specifieke mappen van de host aan een container.

**Gebruik een bind mount:**

```bash
docker run -v /host/path:/container/path nginx
```

#### c. Data back-ups

**Back-up een volume:**

```bash
docker run --rm -v my-volume:/data -v /backup:/backup busybox tar cvf /backup/backup.tar /data
```

**Herstel een volume:**

```bash
docker run --rm -v my-volume:/data -v /backup:/backup busybox tar xvf /backup/backup.tar -C /
```

---

### 5. **SSH in containers**

Hoewel SSH meestal niet nodig is, kan het handig zijn voor debugging.

#### SSH instellen in een container

**Voorbeeld Dockerfile:**

```Dockerfile
FROM ubuntu:20.04
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

**Bouw en draai de container:**

```bash
docker build -t ssh-container .
docker run -d -p 2222:22 ssh-container
```

**Verbinden met SSH:**

```bash
ssh root@localhost -p 2222
```

---

### 6. **Dev Containers**

Development Containers bieden een uniforme ontwikkelomgeving. Dit gebeurt door het gebruik van Docker-containers in combinatie met tools zoals VS Code.

#### Configureren van een Dev Container

1. Maak een map `.devcontainer`.
2. Voeg een `devcontainer.json` toe.

**Voorbeeld `devcontainer.json`:**

```json
{
  "name": "Python Dev",
  "image": "python:3.9",
  "postCreateCommand": "pip install -r requirements.txt",
  "extensions": [
    "ms-python.python"
  ]
}
```

Open de container in VS Code via:

```bash
Remote-Containers: Reopen in Container
```

---

### 7. **CI/CD en automatisering**

Docker speelt een cruciale rol in CI/CD-processen door consistente omgevingen te bieden.

#### Pipelines met Docker

1. **Build stap:** Maak een container image.
2. **Test stap:** Test de applicatie binnen een container.
3. **Deploy stap:** Zet de container in productie.

**Voorbeeld van een CI-pipeline in Jenkins:**

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t my-app .'
      }
    }
    stage('Test') {
      steps {
        sh 'docker run my-app pytest tests/'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker push my-app'
      }
    }
  }
}
```

---

### 8. **Beveiliging in Docker**

#### Best practices:

1. **Gebruik minimale basisimages:**
    
    - Vermijd grote images; gebruik bijvoorbeeld `alpine`.
2. **Beperk toegang:**
    
    - Gebruik Docker-netwerken om toegang tot containers te beperken.
3. **Implementeer geheime opslag:**
    
    - Gebruik tools zoals Docker Secrets of environment variables.
4. **Houd software up-to-date:**
    
    - Update regelmatig je Docker-images en containers.

---

### Conclusie

Hoofdstuk 10 biedt een samenvattend overzicht van de belangrijkste concepten en technieken in containerisatie. Door de labs te voltooien, versterk je je begrip van containerbeheer, netwerken, data persistence, en geavanceerde tools zoals Dev Containers en CI/CD-pipelines. Het toepassen van deze vaardigheden zal je helpen om efficiëntere en veiligere applicaties te ontwikkelen in een gecontaineriseerde omgeving.