# Samenvatting: "1. Introductie DevOps.pdf"

## Hoofdstuk 1: Introductie DevOps

---

### Levenscyclus van een Applicatie
- **Bouwen van applicaties** is slechts een onderdeel van de levenscyclus.
- Vragen:
  - Wat gebeurt er nadat een developer klaar is met de ontwikkeling?
  - Wat gebeurt er wanneer de applicatie in productie draait?
  - Welke stappen komen vóór en na het ontwikkelen van de applicatie?

---

### Flow van een Applicatie
- De **flow van een applicatie** omvat alle stappen van planning tot het live gaan van de applicatie.
- **Stappen in de flow**:
  1. **Business requirements** opstellen.
  2. **User stories** creëren.
  3. **Wireframes/prototypes** ontwikkelen.
  4. **Development:**
     - Nieuwe features ontwikkelen.
     - Unit tests schrijven en dependencies installeren.
  5. **Ops:** Applicatie draaien in een testomgeving.
  6. **QA:** Functionele tests, integratietests en end-to-end tests.
  7. **Ops:** Deployment naar productieomgeving.
  8. **Feedback:** Bugs, issues, logs en nieuwe features opnemen in de volgende cyclus.

---

### Hands-on: Dev(Fl)Ops
- **Doel:** Applicaties naar productie krijgen.
- Praktijkvoorbeeld:
  - Gebruik van een Linux VM met Node.js.
  - Applicatie bereikbaar maken via `http://vm-ip/` of `http://localhost`.

---

### Reflectie op het Proces
#### Communicatieproblemen:
- Geen directe communicatie tussen Dev (ontwikkelaars) en Ops (operations).
  - Dev weet niet hoe de productieomgeving werkt.
  - Ops weet niet wat Dev nodig heeft.

#### Gebrek aan Automatisatie:
- Geen geautomatiseerde flow:
  - Unit tests kunnen genegeerd worden.
  - Integratietests en end-to-end tests worden handmatig uitgevoerd.

#### Gebrek aan Versiebeheer:
- Geen centraal beheer van code en configuraties.
  - Voorbeelden van problemen:
    - Code wordt verspreid via USB-sticks.
    - Productie kan foute versies bevatten door ontbrekend versiebeheer.
    - Geen overzicht van configuraties (software en infrastructuur).

---

### Bronnen
- Artikel: [DevOps Explained](https://www.devops.ch/2017/05/10/devops-explained/)

---
