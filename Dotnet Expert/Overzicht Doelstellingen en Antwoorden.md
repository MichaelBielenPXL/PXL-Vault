

---
## WPF - Building a UI with XAML

### Doelstellingen en Antwoorden

**Wat is XAML en hoe wordt het in WPF gebruikt?**
XAML is een XML-gebaseerde taal om de UI van een WPF-app te beschrijven. Je definieert visueel de layout en eigenschappen van UI-elementen, terwijl de logica in C# staat.

**Waarom wordt de UI in WPF gesplitst in 2 componenten (C# en XAML)?**
Zo scheid je de visuele opbouw (XAML) van de logica (C#), wat overzichtelijker en onderhoudbaarder is.

**Eigenschappen van een UI-element configureren met verschillende syntaxes:**
- Attribute syntax: `<Button Content="Klik" Width="100" />`
- Property element syntax:
  ```
  <Button>
    <Button.Content>Tekst</Button.Content>
  </Button>
  ```
- Content syntax: `<TextBlock>Hallo</TextBlock>`
- Collection syntax:
  ```
  <StackPanel>
    <Button />
    <Button />
  </StackPanel>
  ```

**UI-elementen schikken met layout-eigenschappen:**
Gebruik Margin, Padding, Alignment, Width, Height om de positie en grootte van elementen te bepalen.

**UI-elementen schikken met layout panels:**
Gebruik StackPanel, Grid, Canvas, DockPanel, WrapPanel om elementen te ordenen en te positioneren.

**Werken met ingebouwde WPF-controls:**
Gebruik standaard controls zoals Button, ListView, GroupBox, Image, Menu, enz. in je XAML.

**Eigen UI-element (UserControl) definiëren en gebruiken:**
Maak een UserControl in XAML en C#, voeg deze toe aan je project en gebruik hem als tag in je UI.

---

## WPF - Databinding & MVVM

### Doelstellingen en Antwoorden

**Wat is een Markup Extension in XAML?**
Een Markup Extension is een speciale syntaxis in XAML (herkenbaar aan accolades {}) waarmee je complexe waarden, objecten of bindings instelt. Voorbeelden zijn Binding, StaticResource en DynamicResource.

**De 4 bouwstenen van data binding?**
Bronobject, bronproperty, doelobject, doelproperty. Je verbindt data uit een object aan een UI-element.

**Hoe zet je een data binding op in XAML?**
Met `{Binding}` in de XAML van een UI-element, bijvoorbeeld `<TextBox Text="{Binding Name}" />`.

**Eigenschappen van een data binding instellen?**
Je kunt bij een databinding verschillende eigenschappen instellen om het gedrag te bepalen, zoals:
- **Source**: het object waar de data vandaan komt (standaard de DataContext).
- **Path**: de eigenschap van het bronobject die je wilt binden.
- **Mode**: de richting van de binding (OneWay, TwoWay, OneWayToSource).
- **UpdateSourceTrigger**: bepaalt wanneer de bron wordt bijgewerkt (bijvoorbeeld bij elke wijziging of pas bij verlies van focus).
- **Converter**: een klasse die de waarde omzet tussen bron en doel.

Voorbeeld:
```xml
<TextBox Text="{Binding Path=Name, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}" />
```
Hier wordt de `Name`-eigenschap van het bronobject gebonden aan de `Text` van de TextBox, in beide richtingen, en wordt de bron direct bijgewerkt bij elke wijziging.

**Binding modes?**
OneWay, TwoWay, OneWayToSource. Kies de mode afhankelijk van de gewenste datastroom.

**Hoe wordt het bronobject gevonden als er geen specifieke bron is?**
Via de DataContext van het UI-element.

**Onderdelen van MVVM en hun verantwoordelijkheid?**
Model: data en businesslogica. View: UI. ViewModel: logica voor de UI, koppelt data en commando's aan de View.

**Voordelen van MVVM?**
Scheiding van UI en logica, beter testbaar, onderhoudbaar.

**Data binding toepassen in MVVM?**
Je bindt UI-elementen aan properties in de ViewModel via DataContext.

**INotifyPropertyChanged en PropertyChanged event?**
INotifyPropertyChanged definieert het PropertyChanged event. Nodig om de UI te updaten bij wijzigingen in de ViewModel.

**Waarom INotifyPropertyChanged implementeren?**
Zodat de UI automatisch reageert op wijzigingen in de ViewModel.

**Converters in data binding?**
Converters zetten data om tussen bron en doel, bijvoorbeeld voor weergave of invoer.

**Waarom werken met Commands in MVVM?**
Commands scheiden UI-acties van logica in de ViewModel.

**ICommand interface: methodes en event?**
Execute (uitvoeren), CanExecute (mag het?), CanExecuteChanged (event bij wijziging uitvoerbaarheid).

**Werken met Commands in View en ViewModel?**
Je bindt een Command property in de ViewModel aan een UI-element in de View.

---

## WPF - Resources & Data Templates & DI

### Doelstellingen en Antwoorden

**Resources definiëren in XAML?**
Met `<ResourceDictionary>` in App.xaml of een FrameworkElement.

**Resources gebruiken met StaticResource?**
Via `{StaticResource Key}` in XAML.

**Resources schikken in verschillende bestanden?**
Gebruik MergedDictionaries in App.xaml.

**Flexible Content Model in XAML?**
ContentControl heeft één Content, ItemsControl heeft een ItemsSource. DataTemplates bepalen de weergave.

**DataTemplate in ContentControl?**
Via ContentTemplate property.

**DataTemplate in ItemsControl?**
Via ItemTemplate property.

**Views tonen met DataTemplates in MVVM?**
Definieer DataTemplates voor verschillende ViewModels.

**Wat is Dependency Injection?**
Principe om afhankelijkheden te injecteren, maakt code losser gekoppeld en testbaar.

**Rol van container bij DI?**
Service collection beheert en levert afhankelijkheden.

**Werken met DI in WPF?**
Configureer services in App.xaml.cs en injecteer in ViewModels.

---

## Entity Framework

### Doelstellingen en Antwoorden

**Wat is een ORM en waarom is EF een ORM?**
ORM koppelt objecten in code aan tabellen in een database. EF Core doet dit automatisch.

**DbContext definiëren en gebruiken voor mapping en interactie?**
DbContext is de centrale klasse voor database-interactie en mapping.

**DbContext en conventies/custom mappings?**
Conventies: Id = PK, DbSet = tabel. Custom mappings via Fluent API.

**Fluent API: custom mappings?**
Met modelBuilder in OnModelCreating: HasKey, HasMaxLength, HasDefaultValue.

**Wat zijn migraties in EF?**
Mechanisme om database-schema te updaten bij wijzigingen in het datamodel.

**3 stappen bij migraties?**
add-migration, update-database, script-migration.

**Wat is een Snapshot bij migraties?**
Momentopname van het datamodel, gebruikt om wijzigingen te detecteren.

**Wijzigingen in code toepassen op database met migraties?**
Via update-database na een migration.

**Data seeden met migraties?**
Gebruik HasData in OnModelCreating.

**EF Core configureren in ASP.NET Core/WPF?**
ASP.NET Core: services.AddDbContext. WPF: in App.xaml.cs of servicecontainer.

**Migratie terugdraaien?**
Met Remove-Migration.

**Gegevens ophalen met LINQ?**
Via context.DbSet.ToList(), Where, FirstOrDefault, enz.

**Query workflow?**
LINQ → SQL → DB-verbinding → materialisatie → tracking.

**Deferred execution?**
LINQ-query's worden pas uitgevoerd bij gebruik.

**Executie methodes van LINQ?**
ToList, ToArray, FirstOrDefault, SingleOrDefault, LastOrDefault.

**Aggregatie methodes van LINQ?**
Count, Min, Max, Average, Sum.

**Logging instellen?**
Via LogTo in OnConfiguring.

**Tracking met EntityEntry?**
DbContext houdt objecten bij via ChangeTracker en EntityEntry.

**Verschil in-memory objecten en entiteiten?**
Entiteiten zijn getrackt door EF, in-memory objecten niet.

**Waarom change tracking vaak niet nodig in webapps?**
Webapps werken vaak stateless, dus tracking is overbodig.

**Change tracking uitschakelen?**
Via AsNoTracking() of context.ChangeTracker.AutoDetectChangesEnabled = false.

**SaveChanges workflow?**
DetectChanges → bepaal state → voer SQL uit.

**Objecten toevoegen, aanpassen, verwijderen?**
Add, Update, Remove op DbSet, gevolgd door SaveChanges.

**Gerelateerde data ophalen?**
Eager loading met Include, explicit loading met Entry().Load().

**Navigation property, shadow property, foreign key property?**
Navigation: verwijzing naar gerelateerd object. Shadow: property niet in code, wel in DB. FK: verwijzing naar PK van andere tabel.

**Relaties definiëren?**
Via navigatie-eigenschappen, FK properties, Fluent API.

**Graph in EF?**
Verzameling van entiteiten met relaties.

**Cascading deletes?**
Automatisch verwijderen van gerelateerde data bij verwijderen van hoofdentiteit.

---

## Onion Architecture

### Doelstellingen en Antwoorden

**Waarom nood aan lagen?**
Om complexiteit te beheersen en onderhoudbaarheid te vergroten.

**Wat is Separation of Concerns (SOC)?**
Het scheiden van verantwoordelijkheden in verschillende klassen/lagen.

**3 voordelen van SOC?**
Beter leesbaar, makkelijker uitbreidbaar, eenvoudiger te onderhouden.

**Applicatie opdelen in lagen/projecten?**
Maak een project per laag: Core, Application, Infrastructure, UI.

**Encapsulation met internal?**
Internal beperkt toegang tot binnen het project, beschermt implementatiedetails.

**Verschillen tussen access modifiers?**
public: overal toegankelijk. private: alleen in klasse. protected: in klasse en subklassen. internal: binnen assembly.

**Verantwoordelijkheid van elke laag in 3-tier architectuur?**
UI: interactie met gebruiker. Business Logic: regels en validatie. Data: database-interactie.

**Communicatie tussen lagen in 3-tier?**
UI ↔ Business Logic ↔ Data. UI kent alleen Business Logic, Business Logic kent alleen Data.

**Voor- en nadelen van 3-tier architectuur?**
Voordelen: scheiding, herbruikbaarheid, schaalbaarheid, testbaarheid. Nadelen: complexiteit, prestatie-overhead, afhankelijkheden.

**Verantwoordelijkheid van de 4 lagen in onion architectuur?**
Core Domain: businessregels. Application Logic: use cases. Infrastructure: implementatie van interfaces. Presentation: UI.

**Communicatie tussen lagen in onion architectuur?**
Presentation → Application Logic → Domain. Infrastructure ↔ Core.

**Applicatie opdelen volgens onion architectuur?**
Projecten per laag, afhankelijkheden van buiten naar binnen.

**Waar hoort een component/klasse thuis?**
Afhankelijk van verantwoordelijkheid: businessregels in Core, UI in Presentation, data in Infrastructure.

**Wat is wiring?**
Het koppelen van services en repositories via dependency injection.

**Wiring toepassen?**
Internals zichtbaar maken en dependency injection gebruiken in het uitvoerbare project.

**Verschil domeinlogica en applicatielogica?**
Domeinlogica: businessregels. Applicatielogica: coördinatie van use cases en interactie tussen lagen.

---

## Language Features

### Doelstellingen en Antwoorden

**Werking van delegates en events?**
Delegates zijn types die naar methodes verwijzen. Events zijn meldingen die een object uitstuurt, waarop andere code kan reageren.

**Delegates en events definiëren en gebruiken?**
Definieer een delegate type, maak een event van dat type, abonneer met +=, verwijder met -=.

**Concept en gebruik van lambda’s?**
Lambda's zijn inline methodes, bijvoorbeeld `(x) => x * 2`. Handig voor korte functies en LINQ.

**Werken met lambda’s in code?**
Gebruik lambda's als argument voor delegates, events, LINQ, enz.

**Principes van asynchrone programmatie?**
Code uitvoeren zonder de hoofdthread te blokkeren, bijvoorbeeld met async/await.

**Asynchrone programma’s ontwikkelen?**
Gebruik async/await, Task, en event handlers voor niet-blokkerende code.

---

## Test Driven Development

### Doelstellingen en Antwoorden

**Soorten automatische testen?**
Unit testen, integratietesten, end-to-end testen.

**5 voordelen van automatische testen?**
Minder bugs, sneller bugs vinden, goedkoper, meer tijd voor features, betrouwbare resultaten.

**3 extra voordelen van TDD?**
Je denkt na over de code, vermijdt onnodige code, alles is getest.

**Eigenschappen van een goede automatische test?**
Test één ding, onafhankelijk, herhaalbaar, duidelijk, betrouwbaar.

**Wat is TDD?**
Ontwikkelmethode waarbij je eerst een test schrijft, dan de code.

**Red-Green-Refactor cyclus?**
Red: test faalt. Green: code zodat test slaagt. Refactor: code verbeteren zonder test te breken.

**Red-Green-Refactor toepassen?**
Herhaal deze cyclus bij elke feature.

**3 TDD wetten van Uncle Bob?**
Geen productcode zonder faaltest, niet meer testcode dan nodig om te falen, niet meer productcode dan nodig om te slagen.

**Wat is refactoring?**
Code verbeteren zonder het gedrag te veranderen.

**DRY principe?**
Don't Repeat Yourself: elk stuk kennis/code hoort maar op één plek.

**Waarom test doubles bij unit testen?**
Om afhankelijkheden te isoleren, geen echte systemen te gebruiken.

**TDD met NUnit en Moq voor desktop/ASP.NET Core?**
Gebruik NUnit voor tests, Moq voor mocks, pas TDD-cyclus toe bij ontwikkeling.

---