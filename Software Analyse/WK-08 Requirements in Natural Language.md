# Softwareanalyse en Projectmanagement - Week 08

## Inleiding
Week 08 richt zich op het documenteren van vereisten met behulp van natuurlijke taal (Natural Language - NL), de **Volère-kaarten** en gestandaardiseerde frameworks zoals **IEEE 830 SRS**. Deze week benadrukt het belang van gestructureerde en duidelijke vereisten om de ontwikkeling en het testen van software te ondersteunen.

---

## 1. Vereisten schrijven met natuurlijke taal
Natuurlijke taal wordt gebruikt om vereisten op een manier te beschrijven die begrijpelijk is voor alle stakeholders. Hoewel het eenvoudig en universeel is, kan het ook ambigu zijn.

### Belangrijkste uitdagingen:
1. **Ambiguïteit**: Woorden zoals "alle", "soms", of "geschikt" kunnen meerdere interpretaties hebben.
2. **Nominalisatie**: Complexe processen worden soms te simplistisch beschreven.
3. **Passieve formuleringen**: Zorgt voor minder duidelijkheid over verantwoordelijkheden.

![Uitdagingen bij natuurlijke taal](Software%20Analyse/images/NaturalLanguageChallenges1.png) 
![Uitdagingen bij natuurlijke taal](Software%20Analyse/images/NaturalLanguageChallenges2.png)
*Bron: WK08 - 01 - SWA - Reqs in NL - 00 IntroductionAndExercises.pdf, slide 7*

---

## 2. Het Volère-framework
Het Volère-framework biedt een sjabloon voor het structureren van vereisten. Dit sjabloon maakt gebruik van een combinatie van **user stories**, **systeemvereisten** en andere attributen zoals prioriteit, bron en rationale.

### Belangrijke onderdelen:
1. **User Story**: Beschrijving van de behoefte vanuit het perspectief van de gebruiker.
2. **System Requirement**: Gedetailleerde technische vereiste.
3. **Fit Criteria**: Meetbare criteria om de volledigheid van de vereiste te controleren.

![Volère Kaartsjabloon](Software%20Analyse/images/VolereTemplate.png)  
*Bron: WK08 - 02 - SWA - Reqs in NL - Volére - TemplateAndExplanation.docx, pagina 1*

---

## 3. IEEE 830 - SRS-standaard
De IEEE 830-standaard biedt richtlijnen voor het structureren van een Software Requirements Specification (SRS). Het document is onderverdeeld in:
1. **Inleiding**: Doel en scope.
2. **Algemene beschrijving**: Overzicht van het systeem, interfaces, beperkingen en afhankelijkheden.
3. **Specifieke vereisten**: Gedetailleerde beschrijving van functionaliteiten, kwaliteitseisen en ontwerpbeperkingen.

![IEEE 830 SRS-structuur](IEEE830Structure1.png)  
![IEEE 830 SRS-structuur](IEEE830Structure2.png)  
![IEEE 830 SRS-structuur](IEEE830Structure3.png)  
*Bron: WK08 - 04 - SWA - Reqs in NL - 01 SRS.pdf, slide 3-5*

---

## 4. Case Study: Stad Kortrijk-app
Een praktijkvoorbeeld van vereisten werd gegeven met een app voor inwoners van de stad Kortrijk. De app biedt de volgende functionaliteiten:
- **Afvalkalender**: Informatie over afvalophaling in verschillende wijken.
- **Evenementenkalender**: Verenigingen kunnen evenementen registreren en inwoners kunnen deze bekijken.
- **Documentendownloads**: Attesten zoals gezinssamenstelling of geboorteakte kunnen digitaal worden opgevraagd.

### Technische vereisten:
1. De app ondersteunt alleen Android-apparaten met minimaal versie 10.
2. 95% van de gebruikers moet, na vier keer gebruik, met 75% van de functionaliteiten kunnen werken.

![Kortrijk App Functionaliteiten](Software%20Analyse/images/KortrijkAppFeatures.png)  
*Bron: WK08 - 01 - SWA - Reqs in NL - 01 Opdracht reqs stad Kortrijk.pdf, pagina 1*

---

## 5. Fit Criteria
Fit criteria zorgen ervoor dat vereisten meetbaar zijn en voldoen aan de behoeften van stakeholders. Ze worden gebruikt bij functionele en niet-functionele vereisten.

### Voorbeeld:
- **Functioneel**: "De app moet gebruikers toestaan documenten te downloaden in minder dan 3 seconden."
- **Niet-functioneel**: "Het systeem moet 1000 gebruikers tegelijk kunnen ondersteunen zonder prestatieverlies."

![Fit Criteria Voorbeelden](Software%20Analyse/images/FitCriteriaExamples1.png)  
![Fit Criteria Voorbeelden](Software%20Analyse/images/FitCriteriaExamples2.png)  
*Bron: WK08 - 01 - SWA - Reqs in NL - 00 IntroductionAndExercises.pdf, slide 54-55*

---

## Conclusie
Het gebruik van gestandaardiseerde sjablonen zoals IEEE 830 en Volère helpt bij het creëren van duidelijke, consistente en traceerbare vereisten. Cases zoals de Stad Kortrijk-app tonen de praktische toepassing van deze methodologieën en benadrukken het belang van gestructureerde documentatie.

