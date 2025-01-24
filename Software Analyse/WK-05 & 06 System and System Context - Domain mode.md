# Softwareanalyse en Projectmanagement - Week 05

## Inleiding
Week 05 richt zich op domeinmodellen. Een domeinmodel beschrijft de belangrijkste objecten, klassen en hun relaties binnen een systeem. Domeinmodellen spelen een cruciale rol bij het begrijpen van de probleemruimte en het communiceren met belanghebbenden.

---

## 1. Wat is een Domeinmodel?
Een domeinmodel is een visuele representatie van concepten en hun relaties binnen een probleemdomein. Het helpt bij:
- Begrijpen van de probleemruimte.
- Vastleggen van terminologie.
- Voorbereiden van object-georiënteerde analyse en ontwerp.

[[StudyBuddy_DomainModel.drawio.pdf]]
![Voorbeeld Domeinmodel](DomainModelExample.png)  
*Bron: WK05 - 01 - SWA - System and System Context - DomainModel - 00 IntroductionAndExercises.pdf, slide 6*

---

## 2. Het Proces van Domeinmodellering
Domeinmodellering volgt deze stappen:
1. **Probleembeschrijving voorbereiden**: Analyseer gebruiksscenario’s en requirements.
2. **Concepten en objecten identificeren**: Zoek naar zelfstandige naamwoorden in beschrijvingen.
3. **Vocabulaire ontwikkelen**: Maak een alfabetische lijst en definieer termen.
4. **Associaties identificeren**: Onderzoek relaties tussen concepten.
5. **Attributen toewijzen**: Ken eigenschappen toe aan de concepten.
6. **Multipliciteiten controleren**: Bepaal hoeveel instanties van een klasse in een relatie betrokken zijn.

![Proces van Domeinmodellering](DomainModelProcess.png)  
*Bron: WK05 - 01 - SWA - System and System Context - DomainModel - 00 IntroductionAndExercises.pdf, slide 14*

---

## 3. Case Study: Online Stock Trading System
### Beschrijving:
Een online platform waar klanten aandelen kunnen kopen en verkopen. Belangrijke stappen zijn:
- Registratie van klanten en accounts.
- Handelen in aandelen (kopen en verkopen).
- Communicatie met een beurs voor prijsinformatie en transacties.

### Specifieke Concepten:
- **Klanten**: Moeten voldoende saldo hebben voor transacties.
- **Beurzen**: Verstrekken prijsinformatie.
- **Aandelen**: Worden verhandeld in lotgroottes.

![Online Stock Trading Domeinmodel](OnlineStockDomainModel.png)  
*Bron: WK05 - 04 - SWA - System and System Context - DomainModel - 01 CaseOnlineStock.docx, pagina 1*

---

## 4. Case Study: Tankstation
### Beschrijving:
Een tankstation waar klanten brandstof tanken. Het proces omvat:
- Het activeren van de brandstofpomp.
- Het meten van de hoeveelheid getankte brandstof.
- Het weergeven van de kosten.

### Specifieke Concepten:
- **Klanten**: Gebruikers van de pomp.
- **Brandstofpompen**: Apparaten voor brandstoflevering.
- **Debietmeters**: Meten de getankte hoeveelheid.

![Tankstation Domeinmodel](TankStationDomainModel.png)  
*Bron: WK05 - 02 - SWA - System and System Context - DomainModel - 01 CaseTankStationStart.docx, pagina 1*

---

## 5. Case Study: Point of Sale (POS) System
### Beschrijving:
Een kassasysteem waarmee klanten goederen en diensten kunnen afrekenen. Het proces omvat:
- Het scannen van artikelen.
- Het berekenen van het totaal.
- Het verwerken van betalingen en genereren van een bon.

### Specifieke Concepten:
- **Klanten**: Betalen voor goederen of diensten.
- **Systemen**: Verwerken betalingen en loggen transacties.
- **Artikelen**: Producten die verkocht worden.

![POS Domeinmodel](POSDomainModel.png)  
*Bron: WK05 - 05 - SWA - System and System Context - DomainModel - 01 CasePointOfSale.docx, pagina 1*

---

## 6. Glossary of Terms
Een woordenlijst is essentieel voor consistente communicatie:
- **Klanten**: Personen die gebruikmaken van het systeem.
- **Brandstofpompen**: Apparaten die brandstof leveren.
- **Artikelen**: Producten die worden verkocht.
- **Aandelen**: Financiële activa die verhandeld worden.

![Glossary Voorbeeld](GlossaryExample.png)  
*Bron: WK05 - 01 - SWA - System and System Context - DomainModel - 00 IntroductionAndExercises.pdf, slide 26*

---

## Conclusie
Domeinmodellen helpen ontwikkelteams om het probleemdomein beter te begrijpen en te communiceren met belanghebbenden. Praktijkvoorbeelden zoals het Online Stock Trading System en Tankstation-case benadrukken het belang van duidelijke modellering.
