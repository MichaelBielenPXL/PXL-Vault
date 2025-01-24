# Softwareanalyse en Projectmanagement - Week 10

## Inleiding
Week 10 richt zich op het gebruik van **Activity Diagrams** om functionele vereisten te modelleren. Activity diagrams zijn een krachtig hulpmiddel om processen, parallelle activiteiten en beslissingen binnen een systeem te visualiseren. Deze diagrammen zijn onderdeel van de **UML**-standaard.

---

## 1. Wat is een Activity Diagram?
Een **Activity Diagram** is een modelleermethode die activiteiten binnen een proces beschrijft, inclusief de volgorde en controle tussen deze activiteiten. Het diagram richt zich op:
1. **Activiteiten**: Acties die door het systeem worden uitgevoerd.
2. **Control Flow**: De volgorde waarin activiteiten worden uitgevoerd.
3. **Object Flow**: De data of objecten die door het proces stromen.

### Voordelen:
- **Helderheid**: Maakt complexe processen begrijpelijk.
- **Visualisatie**: Ideaal voor het detailleren van scenarios (zoals Sunny Day, Alternative en Exception Flows).
- **Flexibiliteit**: Ondersteunt parallelle en voorwaardelijke processen.

![Activity Diagram Componenten](ActivityDiagramComponents1.png)  
![Activity Diagram Componenten](ActivityDiagramComponents2.png)  
![Activity Diagram Componenten](ActivityDiagramComponents3.png)  
*Bron: WK10 - 01 - SWA - Req Model Based Activity - 00 IntroductionAndExercises.pdf, slide 22-24*

---

## 2. Belangrijke elementen van een Activity Diagram
### Basiselementen:
1. **Start- en eindnodes**: Begin- en eindpunten van een proces.
2. **Activiteiten**: Functies die door het systeem worden uitgevoerd.
3. **Control Flows**: Verbindingen tussen activiteiten.
4. **Decision Nodes**: Conditionele splitsingen in de stroom.
5. **Fork/Join**: Parallelle processen starten en samenvoegen.

### Geavanceerde elementen:
- **Swim Lanes**: Verdeling van verantwoordelijkheden over actoren of systemen.
- **Object Flows**: Beschrijven hoe data of objecten bewegen door het proces.

![Activity Diagram Swim Lanes](ActivityDiagramSwimLanes1.png)  
![Activity Diagram Swim Lanes](ActivityDiagramSwimLanes2.png)  
*Bron: WK10 - 01 - SWA - Req Model Based Activity - 00 IntroductionAndExercises.pdf, slide 25*

---

## 3. Het Proces: Hoe maak je een Activity Diagram?
1. **Identificeer activiteiten**: Bepaal welke acties het systeem uitvoert.
2. **Bepaal condities en constraints**: Begrijp de voorwaarden en beperkingen tussen activiteiten.
3. **Teken het diagram**:
   - Begin met een startnode.
   - Voeg activiteiten toe en verbind ze met control flows.
   - Gebruik decision nodes voor conditionele paden.
   - Gebruik fork en join voor parallelle processen.

![Activity Diagram Voorbeeld](Software%20Analyse/images/ActivityDiagramExample.png)  
*Bron: WK10 - 01 - SWA - Req Model Based Activity - 00 IntroductionAndExercises.pdf, slide 35*

---

## 4. Case Study: Aankooporders
Een voorbeeld van een activity diagram voor een aankoopdienst:
- **Scenario**:
  - Orders onder €1500 worden direct verwerkt.
  - Orders boven €1500 vereisen eerst offertes.
- **Proces**:
  1. Order wordt ontvangen.
  2. Controle of het bedrag onder of boven de €1500 is.
  3. Bij offertes worden leveranciers geselecteerd en offertes vergeleken.
  4. Bestelbon wordt opgemaakt en verstuurd.

![Aankooporders Diagram](Software%20Analyse/images/ActivityDiagramAankoop.png)  
*Bron: WK10 - 01 - SWA - Req Model Based Activity - 00 IntroductionAndExercises.pdf, slide 37*

---

## 5. Voorbeeld: De Lijn-abonnement
Het activity diagram voor een informatiesysteem van **De Lijn**:
- **Scenario**:
  - Klant geeft persoonlijke gegevens door.
  - Het systeem bepaalt het type abonnement en de prijs op basis van geboortedatum.
  - Na betaling wordt het abonnement geprint.
- **Belangrijkste activiteiten**:
  - Gegevens invoeren.
  - Abonnementstype bepalen.
  - Betaling registreren.
  - Abonnement printen.

![De Lijn Diagram](Software%20Analyse/images/ActivityDiagramDeLijn1.png)  
![De Lijn Diagram](Software%20Analyse/images/ActivityDiagramDeLijn2.png)  
![De Lijn Diagram](Software%20Analyse/images/ActivityDiagramDeLijn3.png)  
![De Lijn Diagram](Software%20Analyse/images/ActivityDiagramDeLijn4.png)  
*Bron: WK10 - 01 - SWA - Req Model Based Activity - 00 IntroductionAndExercises.pdf, slide 38-41*

---

## 6. SWOT-analyse van Activity Diagrams
### Sterke punten:
- Visueel en eenvoudig te begrijpen.
- Ondersteunt parallelle en conditionele processen.
### Zwakke punten:
- Risico op overmatige detaillering.
- Kan tijdrovend zijn bij complexe systemen.
### Kansen:
- Toepasbaar voor gedetailleerde procesanalyse.
### Bedreigingen:
- Interpretatieverschillen tussen stakeholders.

---

## Conclusie
Activity diagrams zijn een krachtige methode om functionele vereisten te modelleren. Door processen en beslissingen te visualiseren, verbeteren ze de communicatie tussen stakeholders en ondersteunen ze een gestructureerde systeemontwikkeling.
