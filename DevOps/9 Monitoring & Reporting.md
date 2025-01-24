# Samenvatting: "9. Monitoring & Reporting"

## Hoofdstuk 9: Monitoring & Reporting

---

### Wat is Monitoring?
- **Definitie:** Het verzamelen en analyseren van gegevens (metrics en logs) om systemen en applicaties te bewaken.
- **Metrics:** Meetpunten zoals:
  - Hardwaregegevens: CPU-gebruik, netwerksnelheden, HDD-temperatuur.
  - Applicatiegegevens: Logging en netwerkactiviteit.
- **Logs:**
  - Voorbeelden:
    - `/var/log/syslog`, `/var/log/kern`.
  - Tools voor loganalyse:
    - **Lokale tools:** Windows Event Viewer, Cockpit, Webmin.
    - **Log-aggregatietools:** ELK Stack, Graylog, Nagios Log Server, Splunk.

---

### Historie van Monitoring
- **Begin:** Simple Network Monitoring Protocol (SNMP) (1988).
  - Gebruik van MIB (Management Information Base) om metrics te definiëren.
- **Evolutie van tools:**
  - Eerste generatie: Data-aggregerende tools zoals Munin en PRTG.
  - Tweede generatie: Alerting-tools zoals Nagios en Check_MK.
  - Moderne tools:
    - **APM (Application Performance Management):**
      - Mix van business logic en predictive monitoring (bijv. Zabbix, Datadog, New Relic).
    - **AI-Ops (Artificial Intelligence for IT Operations):**
      - Tools zoals BigPanda, Dynatrace, Anodot.

---

### Doel van Monitoring
- **Real-time feedback:**
  - Monitoring wordt uitgebreid met deployment-specifieke data.
  - Minimaliseren van risico's tijdens releases.

---

### Low-Risk Release Strategieën
1. **Classic Deploys:**
   - **Voordelen:** Eenvoudig, snel en goedkoop.
   - **Nadelen:** Risico op downtime, moeilijke rollback.
2. **Rolling Deploys:**
   - **Voordelen:** Geleidelijke updates, relatief eenvoudig terug te draaien.
   - **Nadelen:** App/DB moet zowel oude als nieuwe artifacts ondersteunen.
3. **Blue/Green Deploys:**
   - **Voordelen:** Snelle rollback, minder risico.
   - **Nadelen:** Complex en duur.
4. **Canary Deploys:**
   - **Voordelen:** Geleidelijke updates met echte gebruikers, snelle rollback.
   - **Nadelen:** Complexiteit bij scripting en vereiste monitoring.
5. **A/B Testing:**
   - **Voordelen:** Goedkoop en eenvoudig testen van nieuwe features.
   - **Nadelen:** Kan gebruikerservaring verstoren; databasecompatibiliteit vereist aandacht.

---

### Tools en Methoden
- **Monitoringtools:**
  - Hardware: Munin, PRTG.
  - Applicatie: Zabbix, New Relic, Datadog.
  - Logging: ELK Stack, Graylog, Splunk.
- **Testing als metric:**
  - Monitoren van prestaties tijdens deployments met tools zoals APM en loggers.

---

### Recap
- Monitoring en reporting zijn essentieel voor stabiliteit en betrouwbaarheid in DevOps.
- Gebruik van moderne tools en strategieën helpt risico’s te minimaliseren tijdens releases.

---

### Bronnen
- **Continuous Monitoring - The Big Picture:** Overzicht van monitoring in DevOps (45 minuten).
- Artikel: [Blue-Green vs Canary Deployments](https://harness.io/2018/02/blue-green-vs-canary-deployments).

---
