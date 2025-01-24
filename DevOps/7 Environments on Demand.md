# Samenvatting: "6. Environments on Demand"

## Hoofdstuk 6: DTAP & Environments on Demand

---

### Wat is DTAP?
- **DTAP**: Development, Test, Acceptance, Production.
  - Fasen in de ontwikkeling en levering van software.
  - Elke omgeving wordt opgezet met specifieke doelen.
  - Traditioneel handmatig, nu zoveel mogelijk geautomatiseerd.

- **Doel van DTAP:**
  - Valideren van software in verschillende omgevingen voordat deze in productie gaat.
  - Configuratieparameters per omgeving:
    - IP-adressen.
    - API-endpoints.
    - Credentials.
    - Testdata.

---

### Deployment Pipeline
- **Continuous Deployment (CD):**
  - Frequent en geautomatiseerd leveren van nieuwe functionaliteiten.
  - Stappen:
    1. Code ophalen en dependencies installeren.
    2. Code bouwen, testen en artifacts archiveren.
    3. Deployen naar omgevingen (bijv. QA en productie).
  - Elke omgeving heeft unieke configuraties die beheerd worden via Configuration Management.

---

### Configuration Management
- **Best Practices:**
  - Aparte repository voor configuratiedata.
  - Single Source of Truth.
  - Configuratie georganiseerd per omgeving (Test, Acceptatie, Productie).
- **Automatisering:**
  - Voor nu: semi-automatisch via SSH, SCP of Docker.
  - Toekomst: volledig automatisch met tools zoals Chef, Puppet of Ansible.

---

### Application Release Automation (ARA)
- **Voordelen:**
  - Stroomlijnen van processen.
  - Verminderen van handmatige taken.
  - Verbeteren van samenwerking en productiviteit.
- **Implementatie:**
  - "Build once, deploy anywhere."
  - Gebruik van Docker voor consistente deploys.

---

### Mutable vs Immutable Infrastructuur
- **Mutable Infrastructure:**
  - Servers worden continu bijgewerkt, wat kan leiden tot configuratieverschillen.
  - Unieke servergeschiedenis maakt debugging complex.
- **Immutable Infrastructure:**
  - Gebruik van Infrastructure-as-Code (bijv. Docker).
  - Elke wijziging resulteert in een nieuwe versie.
  - Voorkomt configuratiedrift, verhoogt voorspelbaarheid en betrouwbaarheid.
- **Pets vs Cattle:**
  - **Pets:** Unieke servers met specifieke configuraties (mutable).
  - **Cattle:** Gestandaardiseerde, vervangbare servers (immutable).

---

### Docker
- **Voordelen:**
  - "Runs anywhere" (waar Docker beschikbaar is).
  - Inclusief alle dependencies.
  - Bevordert immutable infrastructuur.
- **Best Practices:**
  - Gebruik idempotente Dockerfiles.
  - Specificeer vaste versienummers voor dependencies.
  - Vermijd het opslaan van ongecontroleerde gegevens op het internet.

---

### Recap
- **Environments on Demand:**
  - Automatisering en standaardisering van omgevingen voor snelle en betrouwbare softwarelevering.
  - Gebruik van tools zoals Docker en Configuration Management voor optimale efficiëntie.

---

### Assignments
- Praktijkopdracht: Configureren van een DTAP-opzet met omgevingen on demand.

---
