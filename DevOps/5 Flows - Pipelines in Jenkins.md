# Samenvatting: "5. Flows - Pipelines in Jenkins"

## Hoofdstuk 5: Pipelines in Jenkins

---

### Wat is een Pipeline?
- **Definitie (Jez Humble & David Farley):**
  - Een **deployment pipeline** zorgt ervoor dat alle code in versiebeheer automatisch wordt gebouwd en getest in een productie-achtige omgeving.
  - Kernprincipes:
    - Alle code wordt beheerd via versiebeheer.
    - Code wordt automatisch gebouwd en getest.
    - Omgeving is productiewaardig.
- **Continuous Delivery (CD) Pipeline:**
  - Automatisering van het proces van versiebeheer tot levering aan gebruikers.
  - Elke wijziging doorloopt meerdere stadia van testen en deployment.

---

### Jenkins Pipelines
- **Freestyle Project vs Pipeline:**
  - Pipelines bieden meer flexibiliteit en worden als code beheerd.
- **Pipeline-as-Code:**
  - Geconfigureerd via een `Jenkinsfile`.
  - GUI beschikbaar via de "Blue Ocean" plugin.

#### **Pipeline Stages en Steps:**
- **Stages:**
  - Structuur van de pipeline, weergegeven als kolommen in de stage view.
- **Steps:**
  - Individuele commando’s, triggers of plugins binnen een stage.

#### **Pipeline Agents:**
- Bepalen waar de stages draaien (bijv. op een server, Docker-container of VM).

#### **Post-Run Steps:**
- Worden uitgevoerd na de volledige pipeline-run, ongeacht het resultaat.
- Bij falen van een stap worden volgende stappen/stages niet uitgevoerd, behalve post-run stappen.

---

### Debugging en Errors
- **Build History & Details:**
  - Overzicht van eerdere buildpogingen.
  - Gedetailleerde console output per stap voor debugging.
- **Pipeline Errors:**
  - Mogelijkheid om fouten te analyseren en corrigeren met behulp van console output.

---

### Jenkins Pipeline Scripts
- Scripts worden geschreven in **Groovy**:
  - Documentatie: [Jenkins Pipeline Syntax](https://www.jenkins.io/doc/book/pipeline/syntax/)
  - Groovy documentatie: [Groovy Syntax](https://groovy-lang.org/syntax.html)
- Minimale Pipeline:
  - Basisopzet van een Jenkinsfile om een eenvoudige pipeline te configureren.

---

### Plugins in Jenkins
- **Plugin Manager:**
  - Beheer van extra functionaliteit voor Jenkins.
  - Mogelijkheid om ontbrekende functionaliteit te scripten als er geen plugin beschikbaar is.
- **Belangrijke plugins:**
  - **Git Plugin:** Integratie met Git en GitHub.
  - Plugins voor automatiseren van builds, testen en deploys.

---

### Recap
- **Waarom Jenkins Pipelines?**
  - Automatisering van builds, testen en deployments.
  - Verbetering van efficiëntie en betrouwbaarheid in het ontwikkelproces.
- **Toepassingen:**
  - Beheer van microservices, API’s, front-end en back-end projecten.

---

### Assignments
- Praktijkopdracht: Configureren en implementeren van pipelines in Jenkins.

---
