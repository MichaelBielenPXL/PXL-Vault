# Samenvatting: "4. Flows - Pipelines"

## Hoofdstuk 4: Pipelines

---

### Wat is een Pipeline?
- Definitie (door Jez Humble en David Farley in *Continuous Delivery*):
  - Een **deployment pipeline** zorgt ervoor dat alle code in versiebeheer automatisch wordt gebouwd en getest in een productie-achtige omgeving.
- **Belangrijke principes**:
  - Alle code wordt beheerd via versiebeheer.
  - Code wordt automatisch gebouwd en getest.
  - Omgeving is productiewaardig.

---

### Stappen in een Pipeline
1. **Code binnenhalen**:
   - Code wordt uit versiebeheer gehaald en in de pipeline geplaatst.
2. **Dependencies installeren**:
   - Afhankelijkheden toevoegen, zoals:
     - **PHP**: `composer install`.
     - **JavaScript**: `npm install`.
3. **Software builden**:
   - Automatiseren van het compileren en packagen van de applicatie.
     - **Java**: `mvn/ant` → `.jar`.
     - **.NET Core**: `dotnet publish` → `.exe`.
4. **Testen**:
   - Automatisch testen van code:
     - Codekwaliteit.
     - Linting.
     - Unit tests.
   - Geen QA-omgeving nodig voor basistests.
5. **Artifacts beheren**:
   - Pakketten archiveren en beheren.
   - Strategie: "Build once, deploy anywhere."
6. **Deployen naar QA en productie**:
   - Automatiseren van deployment:
     - Artifact uit de CI-pipeline gebruiken.
     - Omgevingsspecifieke parameters instellen (bijv. credentials en secrets).

---

### Continuous Integration (CI) en Continuous Delivery/Deployment (CD)
- **Continuous Integration (CI)**:
  - Developers integreren regelmatig hun wijzigingen in de main branch.
  - Wijzigingen worden gevalideerd door builds en geautomatiseerde tests.
- **Continuous Delivery/Deployment (CD)**:
  - Elke wijziging in source control doorloopt een gestandaardiseerd proces van testen en deployment.
  - Kernprincipes:
    - Automatisering.
    - Vertrouwen in de kwaliteit van de build.
    - Snelle iteratie: "Als het pijn doet, doe het vaker."

---

### Waarom Pipelines?
- Voordelen:
  - Vermijdt "integration hell" door regelmatige integraties.
  - Verzekert een betrouwbaar en herhaalbaar proces voor het bouwen en testen van software.
  - Faciliteert snellere levering aan klanten en gebruikers.

---

### Pipeline Tooling
- **Oldskool**:
  - Vendor-agnostische tools.
- **Newskool**:
  - Vendor-specifieke tools zoals Jenkins.
- **Jenkins**:
  - Open-source automatiseringsserver.
  - Geschikt voor:
    - Bouwen.
    - Testen.
    - Deployen.

---

### Recap CI/CD Pipeline
- Een **CI/CD pipeline** is een geautomatiseerde weergave van het proces van versiebeheer tot aan productie.
- Elke wijziging doorloopt de volgende stappen:
  1. Code ophalen.
  2. Dependencies installeren.
  3. Build en test.
  4. Artifact opslaan.
  5. Deployen naar QA.
  6. Deployen naar productie.

---

### Bronnen
- Artikel: [DevOps Explained](https://www.devops.ch/2017/05/10/devops-explained/)

---
