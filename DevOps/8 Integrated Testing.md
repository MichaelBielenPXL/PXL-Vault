# Samenvatting: "7. Integrated Testing"

## Hoofdstuk 7: Geïntegreerd Testen

---

### Wat is een Deployment Pipeline?
- **Definitie (door Jez Humble en David Farley):**
  - Een geautomatiseerd proces waarbij code uit versiebeheer wordt gebouwd en getest in een productie-achtige omgeving.
- **Belangrijkste principes:**
  - Automatisch bouwen en testen.
  - Productiewaardige omgeving.
  - Continue integratie en feedback.

---

### Soorten Testen
1. **Unit Testing:**
   - Test afzonderlijke softwarecomponenten.
   - Focus op codekwaliteit en functionaliteit.
   - Tools: JUnit, Jest, etc.
   - Voorbeeld:
     - Controle van batterijduur of activering van een simkaart.

2. **Integratietesten:**
   - Test interacties tussen componenten of systemen, vaak via API’s.
   - Tools:
     - **Postman:** Voor grafische interface en request collections.
     - **Newman:** CLI-integratie voor CI-pipelines.
   - Uitbreidbaar met test scripts:
     - Controle van statuscodes, response body, en variabelen.

3. **Functionele Testen (E2E):**
   - Test complete functionaliteit van een applicatie.
   - Tools: **Playwright** (lightweight E2E testing framework).
   - Playwright functies:
     - Werkt met alle browsers en platforms.
     - Headless modus voor pipelines.
     - Ondersteuning voor locators, assertions, en interactieve debugging.

4. **Niet-Functionele Testen:**
   - **Performance Testing:**
     - Tools: Lighthouse, WebPageTest.
   - **Security Testing:**
     - Controle op kwetsbaarheden en beveiligingslekken.

---

### Testautomatisering
- **Waarom automatiseren?**
  - Snel en betrouwbaar feedback geven.
  - Handmatige tests vermijden om technische schuld te verminderen.
- **In pipelines:**
  - Unit tests draaien bij elke build.
  - Newman voor integratietests.
  - Playwright voor E2E-tests zonder GUI (headless).

---

### Tools voor Geïntegreerd Testen
1. **Postman:**
   - Gebruik voor API-tests.
   - Test scripts om requests/responses te valideren.
   - CLI-integratie via Newman.
2. **Playwright:**
   - E2E testen schrijven in JavaScript/TypeScript.
   - Functies:
     - Debuggen met Visual Studio Code.
     - Locators gebruiken voor DOM-interacties.
     - Rapporten genereren (JSON, JUnit, etc.).
3. **Performance Testing:**
   - Tools zoals Lighthouse en WebPageTest voor front-end performance analyses.

---

### Integratie in Jenkins
- **Continuous Quality:**
  - Globale configuratie voor NodeJS-omgevingen.
  - Testen uitvoeren in headless modus met rapportage.
- **Playwright in CI/CD:**
  - Installeren van browsers en dependencies via ENV-variabelen.
  - Pipelines configureren voor automatische testuitvoering.

---

### Recap
- Geïntegreerd testen is essentieel voor snelle en betrouwbare softwarelevering.
- Automatisering verhoogt efficiëntie en vermindert fouten.
- Gebruik de juiste tools (Postman, Playwright) voor specifieke testbehoeften.

---

### Assignments
- Praktijkopdracht: Configureren en uitvoeren van geïntegreerde tests in een CI/CD-pipeline.

---
