# Softwareanalyse en Projectmanagement - Week 04

## Inleiding
Week 04 richt zich op het modelleren van Business Use Cases (BUCs) binnen de systeemcontext. Het behandelt het belang van duidelijke beschrijvingen en diagrammen voor het vastleggen van bedrijfsprocessen en uitzonderingssituaties.

---

## 1. Business Use Case (BUC)
Een Business Use Case beschrijft een bedrijfsproces als een reeks (inter)acties tussen een business actor en een werkproces. Het doel is om waarde te leveren aan de actor. Het resultaat van een BUC wordt vaak grafisch weergegeven in een diagram.

### Belangrijke onderdelen:
1. **Business Event**: Het evenement dat het proces triggert.
2. **Precondities**: Wat moet waar zijn voordat het proces begint.
3. **Standaardstroom (Normal Business Flow)**: De gebruikelijke reeks stappen in het proces.
4. **Alternatieve Stroom (Alternative Business Flows)**: Variaties die leiden tot een succesvol resultaat.
5. **Uitzonderingsstroom (Exception Business Flows)**: Ongewenste maar noodzakelijke afwijkingen.

---

## 2. Business Use Case Diagram
Een Business Use Case Diagram visualiseert de interacties tussen actoren en het systeem of proces. Het bevat:
- **Actoren**: Personen, systemen of organisaties die interacties uitvoeren.
- **Business Use Cases**: De processen of activiteiten die waarde creëren.

![Business Use Case Diagram](Software%20Analyse/images/BUCDiagram.png)  
*Bron: WK04 - 01 - SWA - System and System Context - BUC - 00 IntroductionAndExercises.pdf, slide 9*

---

## 3. Business Use Case Beschrijvingen
De beschrijvingen van BUCs worden gestructureerd vastgelegd in een template. Een voorbeeld van een sjabloon bevat:
- **Trigger**: Wat start de BUC?
- **Stakeholders**: Primaire en secundaire actoren.
- **Normale stroom**: Beschrijft het ‘sunny day’ scenario waarin alles goed gaat.
- **Alternatieve stroom**: Variaties op de normale stroom.
- **Uitzonderingsstroom**: Beschrijft fouten of problemen en hoe deze worden afgehandeld.
- **Uitkomst**: Wat is het eindresultaat?

![BUC Template](Software%20Analyse/images/BUCTemplate.png)  
*Bron: WK04 - 01 - SWA - System and System Context - BUC - 01 Description Template v2 - explained.docx, pagina 1*

---

## 4. Voorbeeld: Incheckproces op een Luchthaven
Een praktijkvoorbeeld van een Business Use Case is het individuele incheckproces op een luchthaven. Dit proces wordt als volgt beschreven:

- **Trigger**: Een passagier wil inchecken.
- **Preconditie**: De passagier heeft een ticket met QR-code en een geldig identiteitsbewijs.
- **Normale stroom**:
  1. De passagier biedt het ticket en identiteitsbewijs aan bij de balie.
  2. De stewardess controleert de geldigheid.
  3. De passagier ontvangt een instapkaart.
- **Alternatieve stroom**:
  - Als de passagier bagage heeft, volgt een bagage-incheckproces.
- **Uitzonderingsstroom**:
  - Als de passagier geen identiteitsbewijs heeft, moet de vlucht worden omgeboekt.

![Luchthavenproces - Inchecken](Software%20Analyse/images/AirportCheckInProcess.png)  
*Bron: WK04 - 01 - SWA - System and System Context - BUC - 04 Description Example - Airport-simplev2.docx, pagina 1*

---

## 5. Business Use Case Modelleerregels
Bij het modelleren van BUCs zijn er enkele belangrijke richtlijnen:
1. Elke BUC heeft één specifiek doel.
2. Gebruik actieve werkwoorden en duidelijke objecten in namen.
3. Beschrijf stappen vanuit het perspectief van actoren, niet vanuit systemen.
4. Focus eerst op de primaire stroom voordat alternatieven en uitzonderingen worden toegevoegd.

---

## 6. Praktijkoefening: Bibliotheek Systeem
Een voorbeeld van een oefening is het modelleren van een bibliotheeksysteem:
- **Business Use Cases**:
  - Lid worden van de bibliotheek.
  - Boeken lenen en terugbrengen.
- **Actoren**: Leden en bibliotheekmedewerkers.
- **Preconditie**: Leden moeten geregistreerd zijn.
- **Uitkomst**: Een soepel proces voor lenen en retourneren.

![Bibliotheek Use Case](Software%20Analyse/images/LibraryUseCase.png)  
*Bron: WK04 - 01 - SWA - System and System Context - BUC - 00 IntroductionAndExercises.pdf, slide 28*

---

## Conclusie
Het gebruik van Business Use Cases helpt om bedrijfsprocessen gestructureerd te modelleren en documenteren. Templates en diagrammen zoals het incheckproces op een luchthaven of het bibliotheeksysteem bieden waardevolle richtlijnen om duidelijke en consistente vereisten vast te leggen.
