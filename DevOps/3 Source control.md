# Samenvatting: "3 Source control - Slides"

## Hoofdstuk 3: Source Control

---

### Waarom Source Control?
- **Single Source of Truth**:
  - Eén centrale plek voor alle code en configuratie.
- **Samenwerking**:
  - Teams kunnen efficiënt samenwerken aan dezelfde code.
- **Feedback**:
  - Mogelijkheid om wijzigingen te beoordelen en te verbeteren.

---

### Recap & Algemeen Gebruik
- **Wat beheren met source control?**
  - Software code.
  - Infrastructure as code.
  - Documenten (bijv. tekstbestanden).
- **Tools**:
  - Git, SVN, TFS, etc.

- **Best practices**:
  - **Commit messages**:
    - Geven feedback over wijzigingen.
    - Creëren een duidelijke wijzigingsgeschiedenis.
    - Meer informatie: [Git Commit Guide](https://chris.beams.io/posts/git-commit/).
  - **Remote repositories**:
    - Code pushen naar een centrale locatie.

---

### GitHub en Samenwerking
- **Branching**:
  - Strategie voor het werken met branches.
  - Ontwikkel nieuwe functies in aparte branches.
  - Belangrijke links:
    - [GitHub Flow](https://guides.github.com/introduction/flow/).
    - [Branching tutorials](https://www.atlassian.com/git/tutorials/using-branches).
- **Pull requests**:
  1. Ontwikkelaar maakt een nieuwe branch.
  2. Branch wordt naar de centrale repository gepusht.
  3. Pull request wordt aangemaakt voor feedback en evaluatie.
  4. Teamleden reviewen en geven feedback.
  5. Wijzigingen worden gemerged naar de hoofdbranch.

---

### GitHub Flow
#### **Branches:**
- Default branch:
  - **Main**: Voor releases.
  - **Development**: Voor actieve ontwikkeling.
- Basiscommando's:
  - Nieuwe branch aanmaken:
    ```bash
    git branch nieuwe-branch
    git checkout -b nieuwe-branch
    ```
  - Branch pushen:
    ```bash
    git push origin nieuwe-branch
    ```
  - Branch mergen:
    ```bash
    git merge nieuwe-branch
    ```
  - Branch verwijderen:
    ```bash
    git branch -d nieuwe-branch
    ```

#### **Pull Requests:**
- **Doel:**
  - Signaal dat de code klaar is voor een merge.
  - Communicatie tussen teamleden en evaluatie van de code.
- **Inhoud van een pull request:**
  - Beschrijving, opmerkingen en tags voor collega’s.
- **Templates:**
  - Maak een `pull_request_template.md` aan in de root van de repository.

---

### Problemen en Conflicten
- **Merge Conflicts**:
  - Kunnen optreden bij wijzigingen op dezelfde regel of bij verwijderde bestanden.
- **Oplossing**:
  - Pipeline pauzeren en het probleem direct oplossen.
- **Voorkomen van technische schuld**:
  - Problemen niet laten liggen, maar aanpakken zodra ze ontstaan.

---

### Bronnen
- **Links:**
  - [GitHub Flow](https://guides.github.com/introduction/flow/)
  - [Git tutorials](https://www.atlassian.com/git/tutorials/)
  - [Git Commit Guide](https://chris.beams.io/posts/git-commit/)

---
