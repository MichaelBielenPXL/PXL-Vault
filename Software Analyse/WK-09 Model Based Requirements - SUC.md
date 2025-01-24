# Softwareanalyse en Projectmanagement - Week 09

## Inleiding
Week 09 introduceert het modelleren van **System Use Cases (SUCs)**. Het doel van SUCs is het vastleggen en documenteren van de interacties tussen actoren en het systeem. Dit wordt bereikt door **SUC-diagrammen** en **SUC-descriptions**, die beide worden gebruikt om functionele vereisten in kaart te brengen.

---

## 1. Wat is een System Use Case (SUC)?
Een **System Use Case** beschrijft de interacties tussen een systeem en externe actoren. Dit kan worden weergegeven in twee vormen:
1. **SUC-diagram**: Visualiseert actoren, het systeem en hun interacties.
2. **SUC-description**: Beschrijft de stromen (flows) binnen een scenario in natuurlijke taal.

![SUC Diagram Componenten](SUCComponents1.png)  
![SUC Diagram Componenten](SUCComponents2.png)  
![SUC Diagram Componenten](SUCComponents3.png)  
![SUC Diagram Componenten](SUCComponents4.png)  
![SUC Diagram Componenten](SUCComponents5.png)  

*Bron: WK09 - 01 - SWA - Req Model Based SUC - 00 IntroductionAndExercises.pdf, slide 15-16*

---

## 2. Elementen van een SUC
De belangrijkste elementen van een SUC zijn:
1. **Actoren**: Personen of systemen die interacties uitvoeren.
2. **System Boundary**: Definieert wat binnen en buiten het systeem valt.
3. **Use Cases**: Beschrijvingen van wat het systeem doet.
4. **Relaties**:
   - **Include**: Gebruik van gedeelde functionaliteit.
   - **Extend**: Uitzonderingen of optionele functionaliteiten.
   - **Associaties**: Interacties tussen actoren en use cases.

---

## 3. Proces: Het maken van SUCs
Stappen om een SUC te creëren:
1. **Identificeer actoren**: Wie gebruikt het systeem?
2. **Definieer systeemgrenzen**: Wat valt binnen het systeem en wat niet?
3. **Maak een SUC-diagram**: Visualiseer actoren en interacties.
4. **Werk SUC-descriptions uit**:
   - **Preconditions**: Wat moet waar zijn voordat het proces start?
   - **Sunny Day Scenario**: Beschrijving van het normale proces.
   - **Alternative Flows**: Variaties die het proces succesvol afronden.
   - **Exception Flows**: Situaties waarin iets misgaat.

![Proces voor SUC-creatie](SUCProcess1.png)  
![Proces voor SUC-creatie](SUCProcess2.png)  
*Bron: WK09 - 01 - SWA - Req Model Based SUC - 00 IntroductionAndExercises.pdf, slide 20-21*

---

## 4. Case Study: SmartMart
Een casus over een slimme winkelervaring voor klanten van SmartMart. De belangrijkste interacties zijn:
- **Inloggen**: Klanten melden zich aan of resetten hun wachtwoord.
- **Winkelen**: Producten selecteren, zoeken en toevoegen aan de winkelwagen.
- **Bestellen**: Afronden van de bestelling, inclusief betaling.
- **Levering**: Automatisering door robots en bezorgpartners.

![SmartMart SUC Diagram](SmartMartSUC.png)  
*Bron: SUC Smart Mart.docx, pagina 1-2*

---

## 5. Voorbeeld: SUC voor een geldautomaat
Een geldautomaat heeft de volgende SUC:
- **Preconditions**: Klant heeft een bankpas en pincode.
- **Sunny Day Scenario**:
  1. Klant steekt de pas in.
  2. Klant voert een pincode in.
  3. Klant selecteert een bedrag.
  4. Automaat geeft het bedrag.
- **Alternative Flows**:
  - Klant wil de pincode wijzigen.
- **Exception Flows**:
  - Klant voert een onjuiste pincode in.

![ATM SUC Diagram](ATMSUC.png)  
*Bron: WK09 - 01 - SWA - Req Model Based SUC - 03 Example SUC diagram & description ATM-v2.docx, pagina 1*

---

## 6. Template: SUC-descriptions
Een SUC-description bevat:
- **SUC Title**: Kort en krachtig, bijv. "Plaatsen van een bestelling".
- **SUC Description**: Context en doel van de SUC.
- **Preconditions**: Vereisten voordat de use case begint.
- **Main Success Scenario**: De normale stroom.
- **Alternative Flows**: Variaties die leiden tot een succesvol resultaat.
- **Exception Flows**: Fouten of mislukte stappen.
- **Outcome**: Het eindresultaat na de uitvoering.

![SUC Template](SUCTemplate.png)  
*Bron: WK09 - 01 - SWA - Req Model Based SUC - 02 Template SUC Description Blanc.docx, pagina 2*

---

## Conclusie
System Use Cases bieden een gestructureerde manier om systeemfunctionaliteit vanuit het perspectief van de gebruiker vast te leggen. Door gebruik te maken van SUC-diagrammen en descriptions worden functionele vereisten duidelijk gedocumenteerd, wat de communicatie met stakeholders en de ontwikkeling van systemen vergemakkelijkt.
