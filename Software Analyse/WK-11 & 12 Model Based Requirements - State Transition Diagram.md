# Softwareanalyse en Projectmanagement - Week 11

## Inleiding
Week 11 richt zich op het gebruik van **State Transition Diagrams (STDs)** om het dynamische gedrag van systemen te modelleren. Deze diagrammen worden gebruikt om de mogelijke toestanden van een systeem en de gebeurtenissen die toestandsveranderingen veroorzaken te visualiseren.

---

## 1. Wat is een State Transition Diagram (STD)?
Een **State Transition Diagram** beschrijft:
1. **System States**: De verschillende toestanden waarin een systeem zich kan bevinden.
2. **Events**: Gebeurtenissen die een toestandstransitie veroorzaken.
3. **Actions**: Specifieke acties die worden uitgevoerd tijdens een transitie.

### Voordelen:
- Geeft een duidelijk beeld van systeemgedrag.
- Geschikt voor simulatie en testen.
- Visualiseert complexe toestanden en overgangen.

![STD Componenten](STDComponents.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 5*

---

## 2. Belangrijke elementen van een STD
- **Begin- en eindtoestanden**: Markeren het start- en eindpunt van het systeem.
- **Overgangen (Transitions)**: Bepaalde condities of gebeurtenissen die toestandsveranderingen veroorzaken.
- **Guard Conditions**: Voorwaarden waaraan moet worden voldaan voordat een overgang plaatsvindt.
- **Acties (Actions)**: Taken die worden uitgevoerd als onderdeel van een transitie.

### Proces voor het maken van een STD:
1. Definieer alle mogelijke toestanden.
2. Beschrijf elke toestand.
3. Teken overgangen tussen toestanden.
4. Definieer gebeurtenissen en guard conditions.
5. Documenteer acties.

![STD Proces](STDProcess.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 9*

---

## 3. Case Study: Digitale huisdierapplicatie
Een voorbeeld van een STD voor een digitaal huisdier:
- **Toestanden**:
  - Happy
  - Sad
  - Heart-broken
- **Overgangen**:
  - Happy → Sad (na straf)
  - Sad → Happy (na beloning)
  - Sad → Heart-broken (bij herhaalde straf)

![STD Digital Pet](STDDigitalPet.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 12*

---

## 4. Case Study: Brandstofpomp
Een STD beschrijft het gedrag van een brandstofpomp:
- **Toestanden**:
  - Idle
  - Validating Card
  - Fueling
  - Payment Processing
- **Overgangen**:
  - Idle → Validating Card (na invoeren van de kaart)
  - Validating Card → Fueling (bij goedkeuring)
  - Fueling → Payment Processing (na afronden van tanken)

![STD Fuel Pump](STDFuelPump.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 13*

---

## 5. Case Study: VR-bril
Een VR-bril heeft de volgende toestanden:
- **Toestanden**:
  - Standby
  - Booting
  - Main Menu
  - Running Application
- **Overgangen**:
  - Standby → Booting (na inschakelen)
  - Booting → Main Menu (na initialisatie)
  - Main Menu → Running Application (na selectie van een applicatie)

![STD VR Bril](STDVRBril.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 14*

---

## 6. Voor- en nadelen van STDs
### Voordelen:
- Gedetailleerde modellering van systeemgedrag.
- Geschikt voor interface-ontwerp en simulaties.
- Helpt bij het identificeren van fouten in systeemontwerp.

### Nadelen:
- Kan complex worden bij grote systemen.
- Moeilijk te begrijpen voor niet-technische stakeholders.

![STD Voordelen en Nadelen](STDProsCons.png)  
*Bron: WK11 - 01 - SWA - Req Model Based STT - 00 IntroductionAndExercises.pdf, slide 10*

---

## Conclusie
State Transition Diagrams zijn een waardevol hulpmiddel voor het modelleren van dynamisch systeemgedrag. Door gebruik te maken van cases zoals een digitale huisdierapplicatie en een VR-bril, worden de principes van STDs effectief toegepast om functionele vereisten vast te leggen.
****