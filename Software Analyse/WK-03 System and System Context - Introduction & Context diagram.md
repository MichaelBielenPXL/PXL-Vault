# Softwareanalyse en Projectmanagement - Week 03

## Inleiding
Week 03 richt zich op het begrijpen van systeemcontext en de grenzen van een systeem. Het benadrukt het belang van contextdiagrammen, SRS (Software Requirements Specification), en het vastleggen van duidelijke documentatie voor een succesvol project.

---

## 1. Subdisciplines van Requirements Engineering
Requirements engineering bestaat uit twee hoofdonderdelen:
1. **Requirements Development**:
   - Elicitation (het ophalen van vereisten).
   - Analysis, Specification en Validation (analyseren, specificeren en valideren).
2. **Requirements Management**:
   - Tracing, Managing en Controlling (volgen, beheren en controleren van vereisten).

![Framework voor Requirements Engineering](RequirementsEngineeringFramework.png)  
*Bron: WK03 - 01 - SWA - System and System Context - Introduction.pdf, slide 5*

---

## 2. Systeemcontext en grenzen
De systeemcontext definieert de interacties tussen een systeem en zijn omgeving. Het is essentieel om de contextgrenzen te identificeren om scope creep te voorkomen.

### Belangrijke begrippen:
- **Systeemgrenzen**: Wat valt binnen het systeem, en wat wordt als extern beschouwd.
- **Contextdiagrammen**: Deze diagrammen visualiseren de datastromen tussen het systeem en de externe entiteiten.

![Systeemcontext en grenzen](SystemContextBoundaries.png)  
*Bron: WK03 - 01 - SWA - System and System Context - Introduction.pdf, slide 22*

---

## 3. Contextdiagrammen
Een contextdiagram (ook wel een DFD niveau 0 genoemd) geeft een overzicht van de datastromen tussen het systeem en externe entiteiten. 
[[Context_diagram_study_budy.pdf]]
### Belangrijke componenten:
1. **Externe entiteiten**: Personen, systemen of processen buiten het systeem.
2. **Datastromen**: De informatie die in en uit het systeem stroomt.
3. **System boundary**: De grens tussen het systeem en de omgeving.

![Contextdiagram voorbeeld](ContextDiagramExample.png)  
*Bron: WK03 - 02 - SWA - System and System Context - ContextDiagram - 00 IntroductionAndExercises.pdf, slide 6*

### Regels voor contextdiagrammen:
1. Arrows mogen elkaar niet kruisen.
2. Alle componenten moeten unieke namen hebben.
3. Datastromen moeten consistent zijn in decompositie.

---

## 4. IEEE 830 - SRS Template
De IEEE 830 standaard helpt bij het documenteren van vereisten. Het biedt een gestructureerde aanpak om systemen te beschrijven.

### Belangrijke onderdelen:
1. **Introductie**: Beschrijving van doel, scope en referenties.
2. **Overzicht**: Systeemcontext, gebruikersklassen en ontwerpbeperkingen.
3. **Systeemfuncties**: Gedetailleerde beschrijvingen van functionaliteiten.
4. **Kwaliteitseisen**: Prestaties, veiligheid en beveiliging.

![IEEE 830 Template](IEEE830Template.png)  
*Bron: WK03 - 01 - SWA - System and System Context - Introduction.pdf, slide 15*

---

## 5. Cafetaria Ordering System (SRS Case Study)
Het Cafetaria Ordering System dient als voorbeeld voor het gebruik van de SRS-structuur. Het systeem stelt medewerkers in staat maaltijden online te bestellen en te laten bezorgen.

### Belangrijke aspecten:
- **Visie**: Het systeem biedt gemak en vermindert voedselverspilling.
- **Scope**: De eerste release ondersteunt alleen lunchbestellingen; latere releases voegen nieuwe functionaliteiten toe.
- **Belangrijkste functies**:
  1. Maaltijden bestellen en annuleren.
  2. Menu's beheren.
  3. Leveringen plannen.

![Cafetaria Ordering System - Contextdiagram](COSContextDiagram.png)  
*Bron: WK03 - 01b - SWA - System and System Context - SRS - Cafetaria Ordering System.pdf, pagina 2*

---

## 6. Use Case: Precision Tools
Als oefening in contextdiagrammen wordt een voorbeeld gegeven van een gereedschapsbedrijf. Het systeem verwerkt bestellingen, genereert verzendorders, en factureert klanten.

![Precision Tools Contextdiagram](PrecisionToolsDiagram.png)  
*Bron: WK03 - 02 - SWA - System and System Context - ContextDiagram - 00 IntroductionAndExercises.pdf, slide 15*

---

## Conclusie
Een goed begrip van systeemcontext en het gebruik van contextdiagrammen is essentieel voor het vastleggen van vereisten. Door gebruik te maken van standaarden zoals IEEE 830 en praktijkvoorbeelden zoals het Cafetaria Ordering System, kunnen ontwikkelteams gestructureerde en succesvolle softwareprojecten realiseren.
