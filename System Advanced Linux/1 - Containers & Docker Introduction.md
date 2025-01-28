# Containers & Docker: Introduction

## Wat zijn containers?

Containers zijn lichtgewicht, draagbare, en geïsoleerde omgevingen waarin applicaties kunnen draaien. Ze maken gebruik van de onderliggende functies van het Linux-besturingssysteem, zoals **cgroups** en **namespaces**, om resources te isoleren en processen te sandboxen. Hierdoor kunnen applicaties consistent werken, ongeacht de omgeving waarin ze worden uitgevoerd.

### Container Image
Een **container image** is een vooraf geconfigureerd pakket dat alle benodigde componenten bevat om een applicatie te laten draaien:
- **Applicaties**: De software zelf.
- **Dependencies**: Bibliotheken en tools die nodig zijn voor de applicatie.
- **Besturingssysteem**: Vaak een minimale Linux-distributie.

Belangrijkste eigenschappen van een container image:
- **Immutable**: Een image is onveranderlijk; wijzigingen worden nooit opgeslagen in de originele image.
- **Herbruikbaar**: Eén image kan worden gebruikt om meerdere containers op te starten.

### Container
Een container is een geïsoleerd proces dat wordt uitgevoerd op basis van een image. Containers gebruiken de resources van het host-besturingssysteem, maar draaien in een aparte omgeving.

Eigenschappen van containers:
- **Ephemeral**: Containers zijn vluchtig; zodra ze worden verwijderd, verdwijnt ook hun status.
- **Immutable**: Containers worden altijd op dezelfde manier gestart vanuit de image.
- **Stateless**: Containers slaan geen gegevens op tenzij expliciet geconfigureerd via volumes of bind mounts.

Containers bieden een gestandaardiseerde en efficiënte manier om applicaties te bouwen, te testen en in productie te brengen.

---

## Waarom bestaan containers?

Containers zijn ontworpen om veelvoorkomende problemen op te lossen die ontwikkelaars en bedrijven tegenkomen bij het ontwikkelen en implementeren van software. Drie kernvoordelen van containers zijn **portabiliteit**, **agility** en **scalability**.

### 1. Portabiliteit
Containers bieden een oplossing voor het klassieke probleem: "It works on my machine." Een container draait consistent, ongeacht de omgeving:
- Containers bevatten alle vereiste componenten, zoals afhankelijkheden en configuraties.
- Een image die op een ontwikkelmachine draait, kan zonder aanpassingen worden gebruikt in een test- of productieomgeving.

**Voorbeeld**: Een ontwikkelaar bouwt een container met een Python-applicatie op zijn laptop. Deze container kan direct worden ingezet in een cloudomgeving zonder compatibiliteitsproblemen.

### 2. Agility
Containers verbeteren de snelheid en flexibiliteit van softwareontwikkeling:
- **Snelle ontwikkeling**: Ontwikkelaars kunnen lokaal werken in containers die identiek zijn aan productieomgevingen.
- **Integratie met CI/CD**: Containers spelen een sleutelrol in Continuous Integration en Continuous Deployment (CI/CD), wat leidt tot snellere en frequentere implementaties.

**Scenario**: Een ontwikkelaar kan wijzigingen doorvoeren, laten testen en automatisch laten implementeren in productie, zonder handmatige interventie.

### 3. Scalability
Containers zijn ideaal voor het schalen van applicaties:
- Containers starten in milliseconden, terwijl virtuele machines (VM's) vaak minuten nodig hebben.
- Met tools zoals Kubernetes kunnen duizenden containers worden beheerd en automatisch worden geschaald op basis van de vraag.

**Praktijkvoorbeeld**: Stel dat een webshop een piek in bezoekers ervaart. Containers maken het mogelijk om snel extra webservers toe te voegen om de vraag aan te kunnen.

---

## CI/CD en containers

### Wat is CI/CD?
**Continuous Integration (CI)** en **Continuous Deployment/Delivery (CD)** zijn methodologieën die softwareontwikkeling versnellen door het automatiseren van code-integratie, testen en implementatie.

Containers zijn een cruciaal onderdeel van CI/CD-pijplijnen, omdat ze:
1. **Consistentie** bieden: Dezelfde container kan worden gebruikt in ontwikkel-, test- en productieomgevingen.
2. **Snelle implementaties** mogelijk maken: Containers bouwen en implementeren gaat veel sneller dan traditionele methoden.
3. **Rollback-opties** bieden: Dankzij de immutable aard van containers is het eenvoudig om terug te schakelen naar een eerdere versie.

**Workflow**:
1. Een ontwikkelaar commit een wijziging naar een Git-repository.
2. Een CI/CD-tool (bijv. Jenkins of GitHub Actions) bouwt een nieuwe container image.
3. De image wordt getest en vervolgens uitgerold naar productie.

---

## Containers versus virtuele machines

Hoewel containers en virtuele machines vergelijkbare doelen hebben (isolatie en portabiliteit), zijn er belangrijke verschillen.

| **Kenmerk**            | **Containers**                  | **Virtuele Machines**             |
|-------------------------|----------------------------------|------------------------------------|
| **Architectuur**        | Delen de kernel van het host-OS | Volledig besturingssysteem per VM |
| **Resourcegebruik**     | Lichtgewicht                   | Zwaar                             |
| **Opstarttijd**         | Milliseconden                  | Minuten                           |
| **Schaalbaarheid**      | Zeer snel                      | Relatief traag                    |

Containers zijn veel efficiënter omdat ze processen zijn die direct op het host-besturingssysteem draaien, terwijl virtuele machines volledige besturingssystemen emuleren.

**Gebruiksscenario**:
- Containers: Ideaal voor microservices, snelle schaalbaarheid en CI/CD.
- Virtuele machines: Geschikt voor zware toepassingen die volledige isolatie vereisen.

---

## Microservices versus monolithische architectuur

### Monolithische applicaties
Monolithische applicaties zijn grote, geïntegreerde systemen waarin alle functies in één enkele codebase zitten. Dit brengt enkele nadelen met zich mee:
- **Moeilijk schaalbaar**: Je kunt alleen de hele applicatie opschalen, wat inefficiënt is.
- **Traag te updaten**: Het wijzigen van één functie vereist herimplementatie van de hele applicatie.
- **Complexiteit**: Naarmate de codebase groeit, wordt onderhoud steeds lastiger.

### Microservices-architectuur
Microservices splitsen applicaties op in kleine, onafhankelijke services die afzonderlijk kunnen worden ontwikkeld, getest en ingezet.

Voordelen:
- **Individuele schaalbaarheid**: Elke service kan afzonderlijk worden geschaald.
- **Snellere implementaties**: Updates aan één service hebben geen impact op andere delen van de applicatie.
- **Technologie-onafhankelijkheid**: Elk team kan de beste tools kiezen voor hun specifieke service.

Containers zijn een perfecte match voor microservices omdat ze lichtgewicht zijn en eenvoudig te beheren.

---

## Praktische voordelen van containers

1. **Consistentie**:
   - Containers draaien hetzelfde, ongeacht de omgeving.
   - Geen afhankelijkheidsproblemen meer tussen ontwikkel- en productieomgevingen.

2. **Snelle implementaties**:
   - Containers kunnen binnen seconden worden gedeployed of geschaald.
   - Nieuwe versies van applicaties kunnen eenvoudig worden uitgerold zonder downtime.

3. **Efficiëntie**:
   - Containers verbruiken minder resources dan traditionele virtuele machines.
   - Door het delen van de kernel is er minder overhead.

4. **Schaalbaarheid**:
   - Met orkestratietools zoals Kubernetes kunnen duizenden containers automatisch worden beheerd.
   - Containers maken het mogelijk om dynamisch te schalen op basis van de vraag.

---

## Conclusie

Containers hebben de manier waarop software wordt ontwikkeld en geïmplementeerd getransformeerd. Door consistente, draagbare en schaalbare omgevingen te bieden, zijn containers de hoeksteen geworden van moderne DevOps-praktijken en cloud-native architecturen.

Met tools zoals Docker en Kubernetes kunnen ontwikkelaars applicaties snel bouwen, testen en implementeren, terwijl bedrijven profiteren van de efficiëntie en flexibiliteit van containers. Of het nu gaat om het ondersteunen van een microservices-architectuur, het versnellen van CI/CD-processen of het dynamisch schalen van applicaties, containers zijn een essentieel hulpmiddel in de moderne technologie-stack.

**Samenvattend**:
Containers zijn:
- Lichtgewicht
- Draagbaar
- Snel schaalbaar
- Onmisbaar voor moderne softwareontwikkeling
