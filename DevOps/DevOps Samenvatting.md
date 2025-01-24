## 1. Introductie DevOps
### Wat is DevOps?
- **[[1 Introductie DevOps]]**
  - DevOps combineert **Development** en **Operations** om samenwerking, efficiëntie en snelheid in softwareontwikkeling en -levering te verbeteren.
  - **Belangrijkste doelen:**
    - Automatiseren van processen.
    - Verminderen van silo's tussen teams.
    - Snelle feedbackloops en continue verbeteringen.

### Levenscyclus van een Applicatie
1. **Planning en requirements:** Definiëren van projectdoelen.
2. **Ontwikkeling:** Schrijven van code en bouwen van functionaliteiten.
3. **Testing:** Valideren van de kwaliteit en functionaliteit.
4. **Deployment:** Implementeren in productie.
5. **Monitoring en feedback:** Analyseren van prestaties en problemen.

### Wall of Confusion
- De kloof tussen ontwikkelaars (Dev) en operations (Ops), vaak veroorzaakt door tegenstrijdige prioriteiten:
  - **Dev:** Focus op snelheid en nieuwe features.
  - **Ops:** Focus op stabiliteit en minimale risico’s.

### Functionele en Niet-Functionele Vereisten
- **Functioneel:** Wat moet de software doen? (Bijv. inloggen, gegevens opslaan)
- **Niet-functioneel:** Hoe presteert de software? (Bijv. snelheid, betrouwbaarheid)

---

## 2. The 3 Ways
### Overzicht
- **[[2 Agile & DevOps - The 3 Ways]]**
De 3 Ways vormen de kernprincipes van DevOps:
1. **Flow:** Focus op snelle en efficiënte werkstromen.
2. **Feedback:** Creëer continue feedbackloops.
3. **Continuous Learning:** Verbeter constant door te experimenteren.

### Agile vs DevOps
- **Agile:** Iteratieve aanpak gericht op samenwerking en flexibiliteit.
- **DevOps:** Praktische focus op automatisering en integratie tussen ontwikkeling en operations.

### Testing Pyramides
- **Ideal Testing Pyramid:**
  - Veel unit tests, minder integratietests, minimaal handmatige tests.
- **Non-Ideal Testing Pyramid:**
  - Te veel handmatige of end-to-end tests, wat traag en foutgevoelig is.

---

## 3. Source Control
- **[[3 Source control]]**
### Wat is Source Control?
- Beheersysteem voor code en configuraties.
- Voorbeelden: **Git**, **GitHub**.
- **Belangrijke concepten:**
  - **Branches:** Voor afzonderlijke ontwikkelingen.
  - **Commits:** Kleine, traceerbare wijzigingen.
  - **Pull Requests:** Samenwerking en code review.

### GitHub Workflows
- **Feature Branches:** Voor nieuwe functies.
- **Main Branch:** Voor stabiele releases.
- **Pull Requests:** Vraag om wijzigingen te mergen en reviewen.

### Best Practices
- Schrijf duidelijke commit messages.
- Gebruik branches om conflicten te vermijden.

---

## 4. CI/CD Pipelines
- **[[4 Flows - Pipelines]]**
### Wat is CI/CD?
- **Continuous Integration (CI):**
  - Regelmatige integratie van code.
  - Automatisch bouwen en testen.
- **Continuous Deployment (CD):**
  - Automatische release naar productie.

### Pipeline Stappen
1. **Code ophalen:** Haal de laatste wijzigingen uit versiebeheer.
2. **Build:** Compileer en bouw de software.
3. **Testen:** Voer unit- en integratietests uit.
4. **Artifacts:** Sla build-resultaten op.
5. **Deploy:** Implementatie naar test- en productieomgevingen.

---

## 5. Pipelines in Jenkins
- **[[5 Flows - Pipelines in Jenkins]]**
### Wat is Jenkins?
- Automatiseringstool voor CI/CD.
- **Freestyle Project:** Eenvoudige workflows.
- **Pipeline Project:** Geavanceerde, op scripts gebaseerde workflows.

### Belangrijke Concepten
- **Stages:** Grote stappen binnen de pipeline (bijv. build, test).
- **Steps:** Acties binnen een stage.
- **Agents:** Bepalen waar de pipeline draait (bijv. lokale server, cloud).

---

## 6. DTAP en Omgevingen
- **[[7 Environments on Demand]]**
### Wat is DTAP?
- **Development:** Ontwikkeling van nieuwe functionaliteiten.
- **Test:** Valideren van functionaliteit.
- **Acceptance:** Goedkeuring door eindgebruikers.
- **Production:** Live-omgeving.

### Immutable vs Mutable Infrastructure
- **Mutable:** Servers worden bijgewerkt, wat configuratiedrift kan veroorzaken.
- **Immutable:** Nieuwe servers worden opgebouwd, wat betrouwbaarheid verhoogt.

### Tools
- **Docker:** Consistente omgevingen via containerisatie.
- **Configuration Management:** Tools zoals Ansible, Puppet.

---

## 7. Geïntegreerd Testen
- **[[8 Integrated Testing]]**
### Soorten Testen
1. **Unit Testing:** Test individuele functies.
2. **Integratietesten:** Controleer interacties tussen systemen.
3. **Functionele Testen:** Test de volledige workflow.
4. **Performance Testing:** Analyseer snelheid en betrouwbaarheid.

### Tools
- **Postman:** API-testing.
- **Playwright/Selenium:** End-to-end testing.
- **Lighthouse:** Performance-analyse.

---

## 8. Monitoring en Reporting
- **[[9 Monitoring & Reporting]]**
### Wat is Monitoring?
- Verzamel en analyseer gegevens (metrics en logs) om systemen te bewaken.
- **Metrics:** CPU-gebruik, responstijd.
- **Logs:** Gedetailleerde foutmeldingen.

### Deployment Strategieën
- **Rolling Deploys:** Geleidelijke implementatie.
- **Blue/Green Deploys:** Twee identieke omgevingen.
- **Canary Deploys:** Kleine updates naar een gebruikersgroep.

---

## Examentips
1. **Begrijp de theorie:**
   - Focus op concepten zoals CI/CD, DTAP, testing en monitoring.
2. **Ken de tools:**
   - Begrijp het gebruik van GitHub, Jenkins, Docker, en testing tools.
3. **Oefen de voorbeeldvragen:**
   - Bereid je voor op vragen over de 3 Ways, commit messages en pipeline-stappen.
4. **Houd tijd in de gaten:**
   - Je hebt 1,5 uur. Verspil geen tijd aan twijfel over antwoorden.

---
