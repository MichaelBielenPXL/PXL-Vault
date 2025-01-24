
### 1. Hoe ga je om met gevoelige data binnen een pipeline script, zoals wachtwoorden of API-keys? *(1 correct)*  
1. De gevoelige data wordt opgeslagen als een environment variabele en er wordt een referentie gelegd a.d.h.v. een variabele.  
2. De gevoelige data wordt gehasht en deze hash wordt achterliggend vergeleken om te kijken of het wachtwoord correct is.  
3. De wachtwoorden en gevoelige data kunnen als plaintext in het pipeline script geplaatst worden. We moeten er enkel op letten dat de repository op private staat.  
4. We kunnen gebruik maken van de CLI om de gevoelige data/bestanden te encrypteren.  
5. We maken gebruik van SSH keys om de verbinding op te zetten, op die manier gebruiken we geen wachtwoorden en is dit veiliger.  

---

### 2. Welke stellingen zijn **niet waar** in functie van CI/CD? *(2 correct)*  
1. Het maken van een artifact behoort tot continuous integration.  
2. Voor het testen van code a.d.h.v. unittesten & code coverage is er geen testomgeving nodig.  
3. Configuration management behoort tot de continuous integration fase van de pipeline.  
4. Een CI pipeline bevat altijd een stap voor het installeren van dependencies.  
5. Continuous deployment bevat vaak deployments naar verschillende omgevingen.  
6. Binnen pipeline scripts maken we best geen gebruik van het `sudo` commando.  

---

### 3. Waarvoor staan de letters in de afkorting DTAP?  
**Antwoord:** Development, Test, Acceptance, Production.  

---

### 4. Vul in de ontbrekende termen in:  
- **Plan**, create/code, **build**, test/verify, **package/release**, release/deploy, configure/operate, **monitor**.

---

### 5. Welke stellingen over SNMP zijn correct? *(2 correct)*  
1. SNMP wordt gebruikt binnen e-mail om integratie te voorzien van goede feedbackloops.  
2. SNMP staat voor Simple Network Mail Protocol.  
3. SNMP maakt gebruik van een MIB om de beschikbare data hiërarchisch weer te geven.  
4. Er zijn verschillende versies van het SNMP protocol.  
5. SNMP is standaard voorzien van authenticatie zodat niet iedereen aan de data kan.  

---

### 6. Koppel het juiste concept aan de juiste tool:  
**Tools:**  
1. NUnit  
2. Postman  
3. Selenium IDE  
4. Newman  
5. OWASP ZAP  
6. Katalon  
7. Webpagetest  
8. Gatling  

**Concepten:**  
- Functionele testen  
- Integratie testen  
- Performance testen  
- Security testen  
- Unit testen  
- Regressie testen  
- Documentatie testen  
- Systeem testen  

---

### 7. Wat zijn goede regels bij het opstellen van commit messages? *(2 correct)*  
1. Commit berichten moeten best uit lange regels tekst bestaan.  
2. Berichten bestaan uit meerdere regels met opsplitsing van titel & body.  
3. De regels in de body van een commit mogen best maximaal 72 karakters lang zijn.  
4. Het gebruik van witregels en enters is een bad practice.  
5. Commits bestaan best uit korte kernwoorden die high-level een beeld geven van wat er aangepast is in de commit.  
6. Het is belangrijk om aan te geven hoe we iets opgelost hebben in de commit, niet zozeer wat en waarom.  

---

### 8. Gegeven is volgend Groovy script voor een pipeline. Welke stelling is correct? *(1 correct)*  
1. De pipeline installeert de dependencies van de applicatie en runt vervolgens de unittesten a.d.h.v. JUnit.  
2. De pipeline haalt de code binnen van GitHub met credentials. De username die hier gebruikt wordt is ‘pxlstudent’.  
3. De artifact wordt enkel gelinkt als de stappen uit de pipeline geen fouten geven. De ZIP-file wordt wel altijd gemaakt.  
4. De pipeline wordt uitgevoerd onder de homefolder van Jenkins in een folder `workspace`. Daarin krijgt de pipeline zijn eigen folder.  

