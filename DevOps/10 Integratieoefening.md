# Samenvatting: "10. Integratieoefening"

## Hoofdstuk 10: Integratieoefening

---

### Recap van GitHub Ecosysteem
- **Meer dan alleen code repositories:**
  - Issue tracking.
  - Kanban & projectbeheer.
  - Wiki & documentatie.
  - Releases.
  - Security- en dependency-scans.
  - CI/CD-functionaliteit.
- **Geïntegreerd ecosysteem:**
  - GitHub Actions voor geautomatiseerde workflows.
  - Integratie met GitHub-repositories en pull requests.

---

### GitHub Actions
- **Wat is het?**
  - Een tool voor geautomatiseerde workflows (pipelines).
  - Kan draaien op cloud-gehoste machines of self-hosted runners.
- **Structuur:**
  - Geschreven in YAML met een vaste structuur:
    - **Triggers:** Bepaalt wanneer de pipeline wordt uitgevoerd (bijv. bij events of handmatig).
    - **Jobs:** Taken die worden uitgevoerd.
    - **Steps:** Logica of stappen binnen een job.
      - **Uses keyword:** Voorgeconfigureerde modules uit de GitHub Marketplace.
      - **Run keyword:** Voor eigen commando’s.
- **Functionaliteiten:**
  - Visuele feedback per stage/step.
  - Output zichtbaar onder de "Actions"-tab.
  - Automatische meldingen bij falen.
  - Secret manager voor het opslaan van credentials en secrets.

---

### Azure en Azure App Service
- **Wat is Azure?**
  - Een cloudplatform van Microsoft met diensten zoals computing, storage en networking.
  - Pay-as-you-go-prijzen met gratis $100 tegoed voor studenten en gratis services.
  - Meer informatie:
    - [Azure voor studenten](https://azure.microsoft.com/nl-nl/free/students/).
    - [Gratis services](https://azure.microsoft.com/en-us/pricing/free-services/).
- **Azure App Service:**
  - Hostingservice voor applicaties in de cloud.
  - Voordelen:
    - Eenvoudige integratie met GitHub Actions.
    - Ondersteuning voor containers.
    - Weinig tot geen operationele kennis vereist.
    - Gratis onder bepaalde voorwaarden.
  - Introductie lab:
    - [Containers deployen op Azure App Service](https://learn.microsoft.com/en-us/training/modules/deploy-run-container-app-service/).

---

### Integratieoefening: OpsDev
- **Doel:** 
  - Integreren van GitHub-repository’s en workflows met Azure App Services.
- **Kenmerken:**
  - Gebruik van het GitHub-ecosysteem:
    - Repositories.
    - GitHub Actions.
    - GitHub Secrets.
  - Deployment naar het Azure cloudplatform.

---

### Bronnen
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [Azure App Service Documentatie](https://azure.microsoft.com/en-us/products/app-service/)

---
