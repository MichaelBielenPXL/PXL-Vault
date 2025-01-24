# Softwareanalyse en Projectmanagement - Week 01

## Inleiding
Week 01 introduceert de basisprincipes van softwareanalyse en projectmanagement. De focus ligt op het belang van duidelijke vereisten, stakeholderanalyse, en projectfasering om succesvolle resultaten te garanderen.

---

## 1. Het essentiële belang van vereisten
Projecten falen vaak door gebrekkig vereistenbeheer. Volgens het Chaos Report 2021 ontstaan 83% van de problemen door onduidelijke specificaties, veranderende eisen en slechte communicatie.

### Soorten vereisten:
1. **Functionele vereisten**: Beschrijven de functies die het systeem moet bieden.
2. **Kwaliteitsvereisten**: Bevatten eigenschappen zoals snelheid, beveiliging en betrouwbaarheid.
3. **Beperkingen**: Stellen technische of organisatorische grenzen aan het project.

Het gebruik van SMART-vereisten en tools zoals JIRA helpt bij het structureren en prioriteren van deze vereisten. Zonder duidelijke vereisten is een project gedoemd te mislukken.

---

## 2. De fasen van een project
De projectlevenscyclus bestaat uit de volgende fasen:
1. **Initiatiefase**: Het identificeren van het probleem en definiëren van doelen.
2. **Ontwerpfase**: Het creëren van technische specificaties en architectuur.
3. **Implementatiefase**: Ontwikkelen en integreren van oplossingen.
4. **Testfase**: Validatie van functionaliteit en prestaties.

Bij agile-projecten wordt gewerkt met iteratieve sprints waarin feedback en communicatie centraal staan. Elke sprint wordt afgesloten met een **sprint review** en **retrospective** om resultaten te evalueren en verbeterpunten te identificeren.

---

## 3. Het Duivelsvierkant
Het "Duivelsvierkant" is een hulpmiddel dat de balans bewaart tussen vier kritieke factoren:
- **Tijd**: Het naleven van deadlines.
- **Kosten**: Het bewaken van budgetten.
- **Scope**: Het beheersen van de omvang van het project.
- **Kwaliteit**: Het leveren van een robuust product.

![Duivelsvierkant](DuivelsVierkant.png)  
*Bron: WK01 - 02 - SWA - Intro - Duivelsvierkant - The project leader's game.pdf, pagina 2*

---

## 4. Stakeholderanalyse
Stakeholders zijn personen of groepen die invloed hebben op of worden beïnvloed door het project. Ze worden onderverdeeld in:
- **Primaire stakeholders**: Direct betrokken, zoals het projectteam en klanten.
- **Secundaire stakeholders**: Indirect betrokken, zoals leveranciers en externe gebruikers.

[[2.3 Stakeholderanalyse_4b822497f110441db14a563358b831e1-240125-1424-406.pdf]]

Een **RACI-matrix** verduidelijkt rollen en verantwoordelijkheden binnen het team.

![Organogram](Organogram.png)  
*Bron: WK01 - 06 - SWA - Intro - Voorbeeld PvA met stakeholderanalyse.pdf, pagina 19*

---

## 5. Kwaliteitsborging en testen
De teststrategie volgt de **Agile Testpiramide**:
1. **Unittesten**: Focust op individuele componenten.
2. **Integratietesten**: Test de samenhang tussen modules.
3. **UI-testen (E2E)**: Evalueert de volledige processtromen.

Daarnaast worden handmatige exploratory testen uitgevoerd om gebruiksvriendelijkheid en betrouwbaarheid te valideren. **Tools** zoals SonarQube, XRay en Selenium worden gebruikt voor geautomatiseerd testen.

![Agile Testpiramide](AgileTestPiramide.png)
*Bron: WK01 - 06 - SWA - Intro - Voorbeeld PvA met stakeholderanalyse.pdf, pagina 21*

---

## 6. Structuur van User Stories en Features
User stories en features zijn essentieel bij het structureren van vereisten. 
- **User stories** beschrijven functionele vereisten vanuit het perspectief van de gebruiker.
- **Features** beschrijven niet-functionele vereisten zoals prestaties en beveiliging.

De afbeelding hieronder toont een overzicht van de verschillende niveaus van vereisten:
- **User Requirements Specification**: "The user shall be able to..."
- **System Requirements Specification**: "The product shall..."
- **Detailed Requirements Specification**: Gedetailleerde beschrijvingen van eisen.

![Structuur User Stories en Features](USerStoryStructure.png)  
*Bron: WK01 - 03 - SWA - Intro - Requirements, what, levels & types.pdf, pagina 17*

---

## 7. Risicobeheer
Risico’s worden proactief beheerd door:
- **Tijdsgebrek**: Strikte planning en realistische deadlines.
- **Codeverlies**: Back-ups en versiebeheer met Git.
- **Technische problemen**: Regelmatig onderhoud en documentatie.

Elke sprint omvat een risico-evaluatie om potentiële problemen vroegtijdig te identificeren en aan te pakken.

---

## 8. Technologie en infrastructuur
Het project maakt gebruik van moderne tools en technologieën:
- **Back-end**: C# met Entity Framework Core.
- **Front-end**: Angular.
- **Hosting**: Microsoft Azure.

De infrastructuur omvat een **DevOps-pipeline** die CI/CD-principes toepast.

![DevOps-pipeline](DevOpsPipelineEnInfrastructuur.png)  
*Bron: WK01 - 06 - SWA - Intro - Voorbeeld PvA met stakeholderanalyse.pdf, pagina 24*

---

## Conclusie
Een goed opgezet projectplan, gecombineerd met duidelijke communicatie, agile-methodologie en moderne technologieën, is essentieel voor succesvolle softwareontwikkeling. Door balans te houden tussen tijd, kosten, scope en kwaliteit, en door risico’s effectief te beheren, kunnen projecten succesvol worden afgerond.
