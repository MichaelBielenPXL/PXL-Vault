# Introduction to Development Containers

## Wat zijn Development Containers?

**Development Containers** (Dev Containers) zijn een krachtige oplossing voor het creëren van uniforme ontwikkelomgevingen. Ze maken gebruik van Docker-containers om een complete ontwikkelomgeving te leveren, inclusief de juiste tools, afhankelijkheden en configuraties. Dit zorgt ervoor dat ontwikkelaars werken in een consistente omgeving, ongeacht het besturingssysteem van hun lokale machine.

---

## Waarom Development Containers?

### Voordelen:

1. **Consistente omgevingen**:
    
    - Elimineert het bekende "works on my machine"-probleem.
    - Dezelfde omgeving wordt gedeeld tussen ontwikkelaars en CI/CD-systemen.
2. **Gemakkelijk te delen**:
    
    - Dev Containers kunnen worden gedefinieerd in configuratiebestanden, zoals `devcontainer.json`, en gedeeld via repositories.
3. **Snelle setup**:
    
    - Ontwikkelaars hoeven alleen Docker en een ondersteunende editor zoals VS Code te installeren.
4. **Flexibiliteit**:
    
    - Ondersteunt meerdere programmeertalen en frameworks binnen aparte containers.

---

## Belangrijke Componenten

### 1. **Docker**

- Dev Containers draaien binnen Docker-containers.
- Vereist een geïnstalleerde en werkende Docker-engine.

### 2. **Visual Studio Code (VS Code)**

- Ondersteuning via de extensie "Remote - Containers".
- Hiermee kun je direct vanuit VS Code een container als ontwikkelomgeving openen.

### 3. **Configuratiebestand: `devcontainer.json`**

- Dit bestand definieert hoe de container wordt geconfigureerd.
- Locatie: `.devcontainer/devcontainer.json` in je project.

**Voorbeeld van `devcontainer.json`:**

```json
{
  "name": "Node.js Development",
  "image": "node:16-alpine",
  "features": {
    "docker-in-docker": "true"
  },
  "mounts": [
    "source=${localWorkspaceFolder},target=/workspace,type=bind"
  ],
  "settings": {
    "terminal.integrated.defaultProfile.linux": "bash"
  },
  "extensions": [
    "dbaeumer.vscode-eslint"
  ]
}
```

---

## Een Dev Container Configureren

### Stap 1: Maak een `.devcontainer` map

Voeg een map toe aan je project:

```bash
mkdir .devcontainer
```

### Stap 2: Maak het configuratiebestand

Maak een bestand `devcontainer.json`:

```json
{
  "name": "Python Development",
  "image": "python:3.9-slim",
  "postCreateCommand": "pip install -r requirements.txt",
  "settings": {
    "editor.formatOnSave": true
  },
  "extensions": [
    "ms-python.python"
  ]
}
```

### Stap 3: Open het project in de container

- Open VS Code.
- Gebruik de command palette (Ctrl+Shift+P) en selecteer:
    
    ```
    Remote-Containers: Reopen in Container
    ```
    
- VS Code zal de container bouwen en starten op basis van `devcontainer.json`.

---

## Veelgebruikte Opties in `devcontainer.json`

### 1. **`name`**

- Beschrijft de naam van de container.

### 2. **`image`**

- Specificeert de Docker-image die moet worden gebruikt.
- Voorbeeld:
    
    ```json
    "image": "node:16-alpine"
    ```
    

### 3. **`build`**

- Bouwopties voor de container, inclusief een aangepaste Dockerfile.
- Voorbeeld:
    
    ```json
    "build": {
      "dockerfile": "Dockerfile",
      "context": "..",
      "args": {
        "VARIANT": "16"
      }
    }
    ```
    

### 4. **`postCreateCommand`**

- Voert een commando uit nadat de container is gemaakt.
- Voorbeeld:
    
    ```json
    "postCreateCommand": "npm install"
    ```
    

### 5. **`settings`**

- VS Code-specifieke instellingen.
- Voorbeeld:
    
    ```json
    "settings": {
      "editor.tabSize": 4
    }
    ```
    

### 6. **`extensions`**

- Installeert specifieke VS Code-extensies in de container.
- Voorbeeld:
    
    ```json
    "extensions": [
      "ms-python.python",
      "esbenp.prettier-vscode"
    ]
    ```
    

### 7. **`mounts`**

- Definieert bestanden of mappen die tussen de host en container worden gedeeld.
- Voorbeeld:
    
    ```json
    "mounts": [
      "source=${localWorkspaceFolder},target=/workspace,type=bind"
    ]
    ```
    

---

## Best Practices

1. **Gebruik lichte images:**
    
    - Kies bijvoorbeeld voor `alpine`-gebaseerde images om resources te besparen.
2. **Definieer expliciete afhankelijkheden:**
    
    - Gebruik een `requirements.txt` (Python) of `package.json` (Node.js) om afhankelijkheden te beheren.
3. **Gebruik extensies:**
    
    - Installeer automatisch relevante extensies voor je project in de container.
4. **Automatiseer configuraties:**
    
    - Voeg `postCreateCommand` toe om taken zoals het installeren van afhankelijkheden uit te voeren.
5. **Beveilig gevoelige gegevens:**
    
    - Gebruik geheime omgevingsvariabelen in plaats van ze hard te coderen in het configuratiebestand.

---

## Veelvoorkomende problemen en oplossingen

1. **Langzame builds:**
    
    - Optimaliseer je Dockerfile en gebruik caching.
2. **Gebrek aan permissies:**
    
    - Voeg de gebruiker toe aan de juiste groepen of pas permissies aan in de container.
3. **Niet herkende extensies:**
    
    - Controleer of de extensie compatibel is met Remote-Containers.

---

## Conclusie

Development Containers bieden een krachtige manier om consistente ontwikkelomgevingen te creëren. Met tools zoals Docker en VS Code kun je eenvoudig een gecontaineriseerde workflow implementeren die ontwikkelaars helpt om snel en efficiënt te werken. Door gebruik te maken van configuraties zoals `devcontainer.json`, kun je je projecten standaardiseren en de productiviteit verhogen.