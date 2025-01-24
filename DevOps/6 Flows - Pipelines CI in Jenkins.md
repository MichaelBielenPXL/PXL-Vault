# Samenvatting: "5b. Flows - Pipelines CI in Jenkins"

## Hoofdstuk 5b: Continuous Integration (CI) in Jenkins

---

### Wat is een Deployment Pipeline?
- **Definitie (door Jez Humble en David Farley):**
  - Een **deployment pipeline** zorgt ervoor dat alle code in versiebeheer automatisch wordt gebouwd en getest in een productie-achtige omgeving.
- **Belangrijke principes:**
  - Versiebeheer.
  - Automatisch bouwen en testen.
  - Productiewaardige omgeving.

---

### Credential Management
- **Waarom credentials beheren?**
  - Veilige opslag van wachtwoorden, SSH-sleutels, tokens, enz.
- **Veelvoorkomende problemen:**
  - Verkeerd formaat sleutels.
  - Verwisseling van publieke en private sleutels.
  - Gebruik van verkeerde Git-URL (HTTP in plaats van SSH).
  - Onjuiste configuratie van bekende hosts (known hosts).
- **Configuratie:**
  - Opslag via Jenkins Credential Manager.
  - Credentials aanroepen in de `Jenkinsfile` met specifieke syntaxis.

---

### Code Compileren en Tools Configureren
- **Compileren van code:**
  - **Voorbeeld:** Java gebruikt Maven voor het bouwen van applicaties.
- **Globale toolconfiguratie:**
  - Tools zoals Maven, Git, JDK of NPM kunnen globaal worden gedefinieerd.
  - Als een tool niet beschikbaar is via de configuratie:
    - Installeer handmatig op de server of agent.
    - Gebruik een plugin.

---

### Unit Testing
- **Automatisering van tests:**
  - Testframeworks afhankelijk van de programmeertaal:
    - **Java:** JUnit.
    - **NodeJS:** Jest.
  - Integratie met Jenkins:
    - Testresultaten genereren en weergeven via rapportages.
- **Rapportage:**
  - Jenkins biedt ingebouwde ondersteuning voor het genereren van testrapporten.

---

### Artifact Management
- **Wat zijn artifacts?**
  - Buildresultaten (bijv. `.jar` of `.exe`) die worden opgeslagen voor distributie.
- **Artifactbeheer in Jenkins:**
  - Configuratie in de `Jenkinsfile`:
    ```groovy
    post {
        success {
            archiveArtifacts 'target/*.jar'
        }
    }
    ```
  - Mogelijkheden voor externe opslag via plugins.

---

### Overzicht CI in Jenkins
- **Proces van Continuous Integration:**
  1. Code ophalen uit versiebeheer.
  2. Dependencies installeren.
  3. Code compileren.
  4. Automatisch testen met unit tests.
  5. Build artifacts archiveren.
- **Automatiseringstools:**
  - Jenkins biedt uitgebreide ondersteuning voor het configureren van een CI-pipeline met behulp van de `Jenkinsfile`.

---

### Recap
- **Belang van Jenkins in CI:**
  - Verhoogt de betrouwbaarheid en efficiëntie van ontwikkelprocessen.
  - Zorgt voor gestroomlijnde integratie en testen.

---

### Assignments
- Praktijkopdracht: Implementeren van een CI-pipeline in Jenkins.

---
