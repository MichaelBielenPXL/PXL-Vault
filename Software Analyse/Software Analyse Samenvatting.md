# Softwareanalyse en Projectmanagement - Volledige Samenvatting

## Inleiding

Softwareanalyse en projectmanagement is een vak dat zich richt op het ontwerpen, structureren en beheren van softwareprojecten. Het omvat technieken om vereisten te definiëren, processen te modelleren, en kwaliteitsvolle documentatie te produceren. Deze samenvatting bespreekt de belangrijkste aspecten, methodologieën en praktijkvoorbeelden die tijdens het vak aan bod kwamen. Het doel is om een gestructureerd overzicht te bieden dat je helpt bij het voorbereiden op je examen.

---

## 1. Vereistenbeheer en Requirements Engineering

Het verzamelen, specificeren en beheren van vereisten is een van de belangrijkste taken in softwareontwikkeling. Requirements Engineering bestaat uit twee hoofdonderdelen:

### 1.1 Requirements Development

Requirements Development omvat vier fasen:

1. **Elicitation**: Het ophalen van vereisten bij stakeholders.
2. **Analysis**: Het analyseren en structureren van vereisten.
3. **Specification**: Het vastleggen van vereisten in duidelijke documentatie.
4. **Validation**: Het controleren of de vereisten volledig en correct zijn.

### 1.2 Requirements Management

Hierbij worden wijzigingen in vereisten beheerd en gevolgd gedurende de levenscyclus van het project. Belangrijke activiteiten zijn versiebeheer en impactanalyse.

![Requirements Engineering Framework](Software%20Analyse/images/RequirementsEngineeringFramework.png)

### 1.3 Types vereisten

1. **Functionele vereisten**: Beschrijven wat het systeem moet doen.
2. **Niet-functionele vereisten**: Beschrijven hoe het systeem moet presteren (bijv. snelheid, veiligheid).
3. **Beperkingen**: Regels waaraan het systeem moet voldoen, zoals wetgeving.

### 1.4 ISO 25010 Framework

ISO 25010 definieert acht softwarekwaliteitskenmerken:

- Functionality
- Reliability
- Performance efficiency
- Usability
- Security
- Maintainability
- Compatibility
- Portability

![ISO 25010 Framework](Software%20Analyse/images/ISO25010.png)

Lees meer in [[WK-01 Intro to SWA]].

---

## 2. Stakeholderanalyse en communicatie

Stakeholderanalyse helpt bij het identificeren van belanghebbenden en hun behoeften. Effectieve communicatie is cruciaal om verwachtingen te beheren en conflicten te voorkomen.

### 2.1 Tools voor stakeholderanalyse

1. **RACI-matrix**: Definieert verantwoordelijkheden (Responsible, Accountable, Consulted, Informed).
2. **Stakeholder-kaarten**: Visualiseren de invloed en betrokkenheid van stakeholders.

### 2.2 Het communicatiemodel

Het communicatiemodel laat zien hoe informatie tussen stakeholders wordt gedeeld. Het model bestaat uit een zender, ontvanger, kanaal en boodschap.

![Communicatiemodel](Software%20Analyse/images/Communicatiemodel.png)

Lees meer in [[WK-02 Introduction (continued)]].

---

## 3. Modelleringstechnieken

Modelleertechnieken worden gebruikt om complexe processen en vereisten te visualiseren. Dit vergemakkelijkt de communicatie tussen technische en niet-technische stakeholders.

### 3.1 Contextdiagrammen

Contextdiagrammen definiëren de grenzen van een systeem en visualiseren de datastromen tussen externe entiteiten en het systeem.

**Voorbeeld:**

- Externe entiteiten: Klanten, leveranciers.
- Datastromen: Bestellingen, betalingen.

![Contextdiagram Voorbeeld](Software%20Analyse/images/ContextDiagramExample.png)

Lees meer in [[WK-03 System and System Context - Introduction & Context diagram]].

### 3.2 Business Use Cases (BUCs)

BUCs beschrijven bedrijfsprocessen op een hoog niveau. Een BUC bestaat uit:

- **Trigger**: Het evenement dat de use case start.
- **Normale stroom**: Het standaardproces.
- **Alternatieve en uitzonderingsstromen**: Variaties en foutafhandeling.

![BUC Diagram](Software%20Analyse/images/BUCDiagram.png)

Lees meer in [[WK-04 System and System Context - BUC diagram & descriptions]].

### 3.3 Domeinmodellen

Domeinmodellen beschrijven de concepten, attributen en relaties binnen een systeem. Ze zijn cruciaal voor het begrijpen van de probleemruimte en de objectgeoriënteerde ontwikkeling.

![Domeinmodel Voorbeeld](Software%20Analyse/images/DomainModelExample.png)

Lees meer in [[WK-05 & 06 System and System Context - Domain mode]].

---

## 4. System Use Cases (SUCs)

System Use Cases (SUCs) beschrijven interacties tussen actoren en het systeem. Ze worden gebruikt om functionele vereisten te specificeren.

### 4.1 Elementen van een SUC

1. **Actoren**: Gebruikers of systemen die interacties uitvoeren.
2. **System Boundary**: Definieert wat binnen en buiten het systeem valt.
3. **Flows**:
    - **Sunny Day Scenario**: De standaardstroom.
    - **Alternative Flows**: Variaties op het proces.
    - **Exception Flows**: Fouten en uitzonderingen.

![SUC Diagram](Software%20Analyse/images/SUCComponents1.png)
![SUC Diagram](Software%20Analyse/images/SUCComponents2.png)
![SUC Diagram](Software%20Analyse/images/SUCComponents3.png)
![SUC Diagram](Software%20Analyse/images/SUCComponents4.png)
![SUC Diagram](Software%20Analyse/images/SUCComponents5.png)


Lees meer in [[WK-09 Model Based Requirements - SUC]].

---

## 5. Activiteitendiagrammen

Activiteitendiagrammen (UML) worden gebruikt om processen te modelleren. Ze visualiseren workflows, parallelle processen en beslissingen.

### 5.1 Belangrijke elementen

- **Activiteiten**: Acties die worden uitgevoerd.
- **Control Flows**: Verbindingen tussen activiteiten.
- **Decision Nodes**: Conditionele splitsingen.
- **Swim Lanes**: Verdeling van verantwoordelijkheden.

![Activiteitendiagram Voorbeeld](Software%20Analyse/images/ActivityDiagramExample.png)

**Voorbeeld Case:** Aankooporders:

1. Orders onder €1500 worden direct verwerkt.
2. Orders boven €1500 vereisen offertes.

![Aankooporders Diagram](Software%20Analyse/images/ActivityDiagramAankoop.png)

Lees meer in [[WK-10 Model Based Requirements - Activity Diagram]].

---

## 6. State Transition Diagrams (STDs)

STDs modelleren de toestanden en overgangen van een systeem.

### 6.1 Elementen

- **States**: Toestanden waarin een systeem zich kan bevinden.
- **Transitions**: Gebeurtenissen die overgangen veroorzaken.
- **Actions**: Acties die plaatsvinden tijdens een overgang.

### 6.2 Voorbeelden

1. Digitale huisdierapp:
    - Toestanden: Happy, Sad, Heartbroken.
    - Overgangen: Happy → Sad (na straf).

![STD Digital Pet](Software%20Analyse/images/STDDigitalPet.png)

2. Brandstofpomp:
    - Toestanden: Idle, Fueling, Payment Processing.

![STD Fuel Pump](/Software%20Analyse/images/STDFuelPump.png)

Lees meer in [[WK-11 & 12 Model Based Requirements - State Transition Diagram]].

---

## 7. Documentatie en sjablonen

### 7.1 IEEE 830 SRS

De IEEE 830-standaard biedt een sjabloon voor het structureren van Software Requirements Specification (SRS).

- **Secties**:
    1. Inleiding: Doel, scope.
    2. Algemene beschrijving: Overzicht van systeem en beperkingen.
    3. Specifieke vereisten: Gedetailleerde functionaliteiten.

![IEEE 830 Template](Software%20Analyse/images/IEEE830Template.png)

Lees meer in [[WK-08 Requirements in Natural Language]].

### 7.2 Volère Framework

Volère biedt een gestructureerde aanpak voor het vastleggen van vereisten, inclusief fit criteria om de volledigheid te controleren.

![Volère Template](Software%20Analyse/images/VolereTemplate.png)

Lees meer in [[WK-08 Requirements in Natural Language]].

---

## 8. Cases en Praktijkvoorbeelden

### 8.1 Stad Kortrijk-app

Functionaliteiten:

1. Afvalkalender: Informatie over ophaling.
2. Evenementenkalender: Registratie en weergave.
3. Documentendownloads: Attesten opvragen.

![Kortrijk App Functionaliteiten](Software%20Analyse/images/KortrijkAppFeatures.png)

Lees meer in [[WK-08 Requirements in Natural Language]].

### 8.2 SmartMart

Een slimme winkelervaring met processen zoals:

- Inloggen.
- Producten selecteren.
- Bestellen en bezorgen.

![SmartMart SUC Diagram](Software%20Analyse/images/SmartMartSUC.png)

Lees meer in [[WK-09 Model Based Requirements - SUC]].

---

## 9. Analyse- en communicatietools

### SWOT-analyse

Een SWOT-analyse wordt gebruikt om sterke punten, zwakke punten, kansen en bedreigingen te evalueren. Het helpt bij het nemen van strategische beslissingen.

![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis1.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis2.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis3.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis4.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis5.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis6.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis7.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis8.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis9.png)
![SWOT Voorbeeld](Software%20Analyse/images/SWOTAnalysis10.png)

Lees meer in [[WK-07 Elicitation]].

---

## 10. Conclusie

Softwareanalyse en projectmanagement biedt een gestructureerde aanpak voor het plannen, ontwerpen en uitvoeren van softwareprojecten. Het gebruik van modelleertechnieken, gestandaardiseerde documentatie, en effectieve communicatie zijn cruciaal om software van hoge kwaliteit te leveren. Met cases zoals de Stad Kortrijk-app en SmartMart worden theorie en praktijk effectief gecombineerd.

---

## Referenties

Deze samenvatting is gebaseerd op de cursusmaterialen van alle weken, waaronder:

- [[WK-01 Intro to SWA]]
- [[WK-02 Introduction (continued)]]
- [[WK-03 System and System Context - Introduction & Context diagram]]]
- [[WK-04 System and System Context - BUC diagram & descriptions]]
- [[WK-05 & 06 System and System Context - Domain mode]]
- [[WK-07 Elicitation]]
- [[WK-08 Requirements in Natural Language]]
- [[WK-09 Model Based Requirements - SUC]]
- [[WK-10 Model Based Requirements - Activity Diagram]]
- [[WK-11 & 12 Model Based Requirements - State Transition Diagram]]