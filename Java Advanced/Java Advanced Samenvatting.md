# Uitgebreide Uitleg: Java Advanced met Spring Boot

## Inleiding

Dit vak biedt een diepgaande introductie tot geavanceerde Java-concepten in combinatie met Spring Boot, een krachtig framework voor het bouwen van moderne en schaalbare applicaties. Van het bouwen van RESTful webservices tot het implementeren van een 3-lagen architectuur, dit vak behandelt alle fundamentele en gevorderde aspecten die nodig zijn om robuuste enterprise-applicaties te ontwikkelen.

---

## Hoofdstuk 1: Kennismaking met Spring Boot

Spring Boot is ontworpen om de ontwikkeling van Java-applicaties te versnellen door automatische configuratie en ingebouwde hulpmiddelen. Het elimineert veel boilerplate-configuratie die nodig is in traditionele Spring-applicaties.

### Belangrijke Concepten:

- **`@SpringBootApplication`**: Combineert drie annotaties (`@EnableAutoConfiguration`, `@ComponentScan`, en `@Configuration`) om Spring-applicaties eenvoudiger te configureren.
- **Embedded Servers**: Spring Boot wordt geleverd met ingebouwde servers zoals Tomcat, wat het mogelijk maakt om applicaties direct uit te voeren zonder externe configuratie.
- **Spring Initializr**: Een webtool waarmee je snel projecten kunt genereren met de benodigde dependencies.

### Dependency Management

Spring Boot biedt een krachtig dependency management-systeem dat het eenvoudiger maakt om de juiste versies van bibliotheken te gebruiken. Dit wordt mogelijk gemaakt door de **Spring Boot Dependency Parent** en **Bill of Materials (BOM)**:

- **Spring Boot Parent POM**: Zorgt voor standaardconfiguraties en afhankelijkheidsversies.
    
    ```xml
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.5.2</version>
        <relativePath />
    </parent>
    ```
    
- **Starters**: Spring Boot biedt voorgedefinieerde "starter"-dependencies zoals `spring-boot-starter-web`, die alle benodigde bibliotheken bevatten voor een bepaald doel.

**Voorbeeld van een POM.xml met starters:**

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>
</dependencies>
```

Dit zorgt ervoor dat alle dependencies compatibel zijn met de Spring Boot-versie die je gebruikt.

### Codevoorbeeld:

```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

### Extra Functionaliteiten:

1. **Actuator**: Biedt productieklare monitoring en management-eindpunten zoals `/actuator/health`.
2. **DevTools**: Versnelt de ontwikkelingscyclus door automatische herlaadfunctionaliteit.

**Voordelen van Spring Boot:**

- Snelle configuratie.
- Ingebouwde productie-klare functies zoals monitoring en metrics.
- Naadloze integratie met andere Spring-modules.

➡️ Zie ook: [[1 - Kennismaking met Spring Boot]]

---

## Hoofdstuk 2: RESTful Webservices

REST (Representational State Transfer) is een architectuurstijl die communicatie tussen systemen stroomlijnt via standaard HTTP-methoden (GET, POST, PUT, DELETE). In Spring Boot worden RESTful webservices eenvoudig geïmplementeerd met Spring Web.

### Belangrijke Annotaties:

- **`@RestController`**: Geeft aan dat een klasse een REST-controller is.
- **`@RequestMapping`**: Definieert het basispad voor een endpoint.
- **`@GetMapping`, `@PostMapping`**: Specificeert de HTTP-methoden voor specifieke paden.

### Voorbeeld REST-API:

```java
@RestController
@RequestMapping("/api")
public class UserController {

    @GetMapping("/users")
    public List<User> getUsers() {
        return List.of(new User("Alice"), new User("Bob"));
    }

    @PostMapping("/users")
    public String createUser(@RequestBody User user) {
        return "Gebruiker " + user.getName() + " aangemaakt!";
    }
}
```

➡️ Zie ook: [[2 - RESTful Webservices met Spring Boot]]

---

## Hoofdstuk 3: Collections en de Map-interface

Java's Collections Framework biedt datastructuren zoals `List`, `Set`, en `Map` om gegevens efficiënt te beheren. De `Map`-interface wordt gebruikt om key-value-paren op te slaan.

### Veelgebruikte Implementaties

#### 1. **`HashMap`**

Een `HashMap` biedt snelle toegang tot gegevens op basis van de sleutel. Het slaat gegevens op in willekeurige volgorde en biedt geen garantie voor de volgorde van iteratie.

**Voorbeeld:**

```java
HashMap<String, Integer> hashMap = new HashMap<>();
hashMap.put("Alice", 30);
hashMap.put("Bob", 25);
System.out.println(hashMap);
```

_Output:_ `{Bob=25, Alice=30}`

#### 2. **`TreeMap`**

Een `TreeMap` sorteert de sleutel-waarde-paren op natuurlijke volgorde van de sleutels of volgens een aangepaste comparator. Dit is nuttig als gesorteerde gegevens vereist zijn.

**Voorbeeld:**

```java
TreeMap<String, Integer> treeMap = new TreeMap<>();
treeMap.put("Charlie", 40);
treeMap.put("Alice", 30);
treeMap.put("Bob", 25);
System.out.println(treeMap);
```

_Output:_ `{Alice=30, Bob=25, Charlie=40}`

#### 3. **`LinkedHashMap`**

Een `LinkedHashMap` behoudt de invoervolgorde. Dit is handig wanneer de volgorde van invoer belangrijk is.

**Voorbeeld:**

```java
LinkedHashMap<String, Integer> linkedHashMap = new LinkedHashMap<>();
linkedHashMap.put("Alice", 30);
linkedHashMap.put("Bob", 25);
linkedHashMap.put("Charlie", 40);
System.out.println(linkedHashMap);
```

_Output:_ `{Alice=30, Bob=25, Charlie=40}`

### Vergelijking van Implementaties

|Eigenschap|`HashMap`|`TreeMap`|`LinkedHashMap`|
|---|---|---|---|
|**Volgorde**|Willekeurig|Gesorteerd|Invoervolgorde|
|**Prestaties**|Zeer snel|Langzamer|Minder snel|
|**Gebruik**|Snel zoeken|Gesorteerde data|Volgorde nodig|

➡️ Zie ook: [[3 - Collections Map]]

---

## Hoofdstuk 4: Dependency Injection (DI) en Inversion of Control (IoC)

### Wat is Dependency Injection?

DI is een techniek waarmee objecten hun afhankelijkheden van buitenaf ontvangen in plaats van deze zelf te maken. Dit wordt beheerd door Spring's IoC-container (Inversion of Control). Er zijn drie primaire methoden om DI toe te passen in Spring:

#### 1. Constructor Injection

Hierbij worden afhankelijkheden doorgegeven via de constructor. Dit is de aanbevolen methode omdat het object immutabel maakt en expliciet aangeeft welke afhankelijkheden nodig zijn.

**Voorbeeld:**

```java
@Component
public class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
    }
}
```

#### 2. Setter Injection

Afhankelijkheden worden doorgegeven via setter-methoden. Dit is handig voor optionele afhankelijkheden of situaties waarin waarden na objectcreatie moeten worden ingesteld.

**Voorbeeld:**

```java
@Component
public class Car {
    private Engine engine;

    @Autowired
    public void setEngine(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
    }
}
```

#### 3. Field Injection

Hierbij worden afhankelijkheden direct in een veld geïnjecteerd met de annotatie `@Autowired`. Hoewel het eenvoudig is, wordt dit afgeraden omdat het testbaarheid vermindert.

**Voorbeeld:**

```java
@Component
public class Car {
    @Autowired
    private Engine engine;

    public void drive() {
        engine.start();
    }
}
```

### Voordelen van Dependency Injection

- **Losse koppeling:** Klassen zijn minder afhankelijk van specifieke implementaties.
- **Betere testbaarheid:** Simpele mock-implementaties kunnen worden gebruikt tijdens unit tests.
- **Duidelijke afhankelijkheden:** Constructor Injection maakt afhankelijkheden expliciet, wat de code leesbaarder en onderhoudsvriendelijker maakt.

➡️ Zie ook: [[4 - Dependency Injection en Inversion of Control (IoC)]]

---

## Hoofdstuk 5: Spring Validation

Spring Validation maakt het eenvoudig om gebruikersinvoer te valideren via annotaties. Het integreert met de Bean Validation API (`javax.validation`) en stelt ontwikkelaars in staat om invoer efficiënt te valideren en foutmeldingen te beheren.

### Veelgebruikte Annotaties

- **`@NotNull`**: Controleert dat een veld niet null is.
- **`@Size`**: Controleert de grootte of lengte van een waarde.
- **`@Email`**: Controleert of een string een geldig e-mailadres is.
- **`@Min` en `@Max`**: Valideert numerieke grenzen.

**Voorbeeld van een DTO met validatie:**

```java
public class UserDTO {
    @NotNull(message = "Naam mag niet null zijn")
    @Size(min = 2, max = 50, message = "Naam moet tussen 2 en 50 karakters zijn")
    private String name;

    @Min(value = 18, message = "Leeftijd moet minimaal 18 zijn")
    private int age;

    @Email(message = "E-mailadres moet geldig zijn")
    private String email;

    // Getters en setters
}
```

### Validatie in Controllers

Validatie wordt geactiveerd door de annotatie `@Valid`. Fouten kunnen worden opgevangen en verwerkt met het `BindingResult`-object.

**Voorbeeld:**

```java
@RestController
@RequestMapping("/users")
public class UserController {

    @PostMapping
    public ResponseEntity<?> createUser(@Valid @RequestBody UserDTO userDTO, BindingResult result) {
        if (result.hasErrors()) {
            return ResponseEntity.badRequest().body(result.getAllErrors());
        }
        return ResponseEntity.ok("Gebruiker succesvol aangemaakt");
    }
}
```

### Uitleg van Validatiefouten

De `BindingResult`-interface bevat een lijst van fouten die tijdens validatie zijn opgetreden. Deze fouten kunnen worden teruggestuurd naar de gebruiker in een begrijpelijk formaat.

**Voorbeeld van foutverwerking:**

```java
if (result.hasErrors()) {
    List<String> errors = result.getAllErrors().stream()
        .map(DefaultMessageSourceResolvable::getDefaultMessage)
        .collect(Collectors.toList());
    return ResponseEntity.badRequest().body(errors);
}
```

### Validatieberichten Aanpassen

Validatieberichten kunnen worden aangepast met resourcebundles of in de `application.properties`.

**Voorbeeld:**

```properties
userDTO.name.NotNull=De naam is verplicht
userDTO.age.Min=De minimale leeftijd is {value}
```

➡️ Zie ook: [[5 - Spring Validation]]

---

## Hoofdstuk 6: Unit Testen met JUnit

Unit testing is een essentieel onderdeel van softwareontwikkeling. Het richt zich op het testen van individuele componenten (meestal methoden) om te verifiëren dat ze correct functioneren.

### Wat is JUnit?

JUnit is een veelgebruikt testframework in Java dat wordt gebruikt om unit tests te schrijven en uit te voeren. Het biedt een gestructureerde aanpak en verschillende hulpmiddelen om tests efficiënt te maken.

### Belangrijke Annotaties in JUnit

- **`@Test`**: Geeft aan dat een methode een testmethode is.
- **`@BeforeEach`**: Voert voorbereidingsstappen uit vóór elke testmethode.
- **`@AfterEach`**: Voert opruimacties uit na elke testmethode.
- **`@BeforeAll`**: Voert voorbereidende acties uit voordat alle tests worden uitgevoerd (moet `static` zijn).
- **`@AfterAll`**: Voert afsluitende acties uit na alle tests (moet `static` zijn).
- **`@Disabled`**: Schakelt een test tijdelijk uit.

### Een Simpele JUnit Test

Hier is een voorbeeld van een eenvoudige test:

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class CalculatorTest {

    @Test
    void testAddition() {
        Calculator calculator = new Calculator();
        int result = calculator.add(2, 3);
        assertEquals(5, result, "De som van 2 en 3 moet 5 zijn");
    }
}
```

In dit voorbeeld:

- `assertEquals(expected, actual, message)` controleert of de verwachte waarde overeenkomt met de daadwerkelijke waarde.
- De test slaagt als de methode `add` het correcte resultaat retourneert.

### Assertions

JUnit biedt verschillende assertiemethoden om testresultaten te verifiëren. Veelgebruikte assertions zijn:

- **`assertEquals`**: Controleert of twee waarden gelijk zijn.
- **`assertNotEquals`**: Controleert of twee waarden ongelijk zijn.
- **`assertTrue`**: Controleert of een voorwaarde waar is.
- **`assertFalse`**: Controleert of een voorwaarde onwaar is.
- **`assertNull`**: Controleert of een object `null` is.
- **`assertThrows`**: Controleert of een verwachte uitzondering wordt gegooid.

**Voorbeeld van `assertThrows`:**

```java
@Test
void testException() {
    assertThrows(IllegalArgumentException.class, () -> {
        throw new IllegalArgumentException("Ongeldige invoer");
    });
}
```

### Lifecycle Callbacks

JUnit ondersteunt lifecycle callbacks om herhalende setup- of teardown-acties te beheren.

**Voorbeeld:**

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.Test;

public class SampleTest {

    @BeforeEach
    void setUp() {
        System.out.println("Voorbereiden vóór elke test");
    }

    @AfterEach
    void tearDown() {
        System.out.println("Opruimen na elke test");
    }

    @Test
    void testExample() {
        System.out.println("Test uitgevoerd");
    }
}
```

_Output:_

```
Voorbereiden vóór elke test
Test uitgevoerd
Opruimen na elke test
```

### Integratie met Mockito

In situaties waarin afhankelijkheden moeten worden gemockt, kan **Mockito** worden gebruikt. Dit framework maakt het eenvoudig om mock-objecten te maken en gedrag te simuleren.

**Voorbeeld met Mockito:**

```java
import static org.mockito.Mockito.*;
import org.junit.jupiter.api.Test;

public class UserServiceTest {

    @Test
    void testGetUser() {
        UserRepository mockRepository = mock(UserRepository.class);
        when(mockRepository.findById(1)).thenReturn(new User("Alice"));

        UserService userService = new UserService(mockRepository);
        User user = userService.getUser(1);

        assertEquals("Alice", user.getName());
    }
}
```

In dit voorbeeld:

- `mock()` maakt een gesimuleerd object aan.
- `when(...).thenReturn(...)` stelt het verwachte gedrag in voor een specifieke methode-aanroep.

### Voordelen van Unit Tests

- **Kwaliteitsborging:** Helpt bij het opsporen van fouten in een vroeg stadium.
- **Regressietesten:** Zorgt ervoor dat nieuwe wijzigingen bestaande functionaliteit niet breken.
- **Documentatie:** Testen documenteren hoe een component hoort te werken.

➡️ Zie ook: [[6 - Unit Testen met JUnit]]

---

## Hoofdstuk 7: Lambda Expressies en Streams

Lambda-expressies en de Stream API, geïntroduceerd in Java 8, bieden een krachtige manier om declaratieve, functionele programmeerconcepten te gebruiken binnen Java. Ze maken het werken met collecties compacter, leesbaarder en efficiënter.

### Lambda-Expressies

Lambda-expressies zijn anonieme functies die gedrag definiëren en kunnen worden doorgegeven als parameter. Ze verkorten de traditionele syntaxis van anonieme inner classes.

**Syntax:**

```java
(parameters) -> expression
```

**Voorbeelden:**

1. Een expressie met één parameter:
    
    ```java
    x -> x * x
    ```
    
    Dit verhoogt `x` tot de macht twee.
2. Meerdere parameters:
    
    ```java
    (a, b) -> a + b
    ```
    
    Som van twee waarden.
3. Meerdere regels:
    
    ```java
    (a, b) -> {
        int result = a * b;
        return result;
    }
    ```
    

### Functional Interfaces

Lambda-expressies werken met **functional interfaces**. Een functional interface heeft slechts één abstracte methode.

**Voorbeelden van ingebouwde functional interfaces:**

- **`Predicate<T>`**: Controleert een voorwaarde en retourneert `true` of `false`.
    
    ```java
    Predicate<String> isEmpty = s -> s.isEmpty();
    ```
    
- **`Function<T, R>`**: Transformeert een waarde van type `T` naar type `R`.
    
    ```java
    Function<Integer, String> toString = i -> "Nummer: " + i;
    ```
    
- **`Consumer<T>`**: Voert een actie uit op een object zonder iets te retourneren.
    
    ```java
    Consumer<String> printer = System.out::println;
    ```
    

### Stream API

De Stream API biedt een declaratieve manier om collecties en arrays te verwerken. Het maakt gebruik van pipelined verwerking.

#### Basis Operaties op Streams

1. **`filter`**: Filtert elementen op basis van een voorwaarde.
    
    ```java
    List<String> names = List.of("Alice", "Bob", "Charlie");
    List<String> filtered = names.stream()
        .filter(name -> name.startsWith("A"))
        .collect(Collectors.toList());
    ```
    
2. **`map`**: Transformeert elk element in de stream.
    
    ```java
    List<Integer> numbers = List.of(1, 2, 3);
    List<Integer> squared = numbers.stream()
        .map(n -> n * n)
        .collect(Collectors.toList());
    ```
    
3. **`reduce`**: Combineert alle elementen in de stream tot één waarde.
    
    ```java
    int sum = numbers.stream()
        .reduce(0, Integer::sum);
    ```
    
4. **`sorted`**: Sorteert de elementen.
    
    ```java
    List<String> sortedNames = names.stream()
        .sorted()
        .collect(Collectors.toList());
    ```
    
5. **`forEach`**: Voert een actie uit op elk element.
    
    ```java
    names.stream()
        .forEach(System.out::println);
    ```
    

### Parallel Streams

Parallelle streams verdelen de verwerking over meerdere threads om prestaties te verbeteren bij grote datasets.

**Voorbeeld:**

```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);
numbers.parallelStream()
    .forEach(System.out::println);
```

> **Let op:** Parallelle verwerking kan onverwachte resultaten geven bij niet-threadveilige collecties.

### Combinatie van Lambda's en Streams

Een voorbeeld waarbij lambda-expressies en streams samen worden gebruikt:

```java
List<String> names = List.of("Alice", "Bob", "Charlie", "David");
List<String> processedNames = names.stream()
    .filter(name -> name.length() > 3)
    .map(String::toUpperCase)
    .sorted()
    .collect(Collectors.toList());
System.out.println(processedNames);
```

**Uitvoer:**

```
[ALICE, CHARLIE, DAVID]
```

### Voordelen van Lambda's en Streams

- **Leesbaarheid**: Minder boilerplate-code.
- **Prestaties**: Streams gebruiken lazy evaluation.
- **Flexibiliteit**: Makkelijk combineren van verschillende operaties.

➡️ Zie ook: [[7 - Lambda Expressies en Streams]] Lambda-expressies maken Java compacter en eleganter. De Stream API biedt een declaratieve manier om collecties te verwerken.

➡️ Zie ook: [[7 - Lambda Expressies en Streams]]

---

## Hoofdstuk 8: 3-Lagen Architectuur en Spring Data JPA

De 3-lagen architectuur is een ontwerpprincipe dat softwaretoepassingen opsplitst in drie gescheiden lagen, elk met een specifieke verantwoordelijkheid. Dit zorgt voor een duidelijke structuur en een betere onderhoudbaarheid van de applicatie.

### Lagen in de Architectuur

1. **Controller-laag:**
    
    - Verwerkt inkomende HTTP-verzoeken.
    - Roept methoden aan in de servicelaag.
    - Retourneert HTTP-responsen aan de gebruiker of client.
    
    **Voorbeeld:**
    
    ```java
    @RestController
    @RequestMapping("/users")
    public class UserController {
    
        @Autowired
        private UserService userService;
    
        @GetMapping
        public List<User> getAllUsers() {
            return userService.getAllUsers();
        }
    
        @PostMapping
        public User createUser(@RequestBody User user) {
            return userService.createUser(user);
        }
    }
    ```
    
2. **Service-laag:**
    
    - Bevat de bedrijfslogica van de applicatie.
    - Verwerkt gegevens die van de controller komen voordat deze worden opgeslagen of opgevraagd in de database.
    
    **Voorbeeld:**
    
    ```java
    @Service
    public class UserService {
    
        @Autowired
        private UserRepository userRepository;
    
        public List<User> getAllUsers() {
            return userRepository.findAll();
        }
    
        public User createUser(User user) {
            return userRepository.save(user);
        }
    }
    ```
    
3. **Repository-laag:**
    
    - Verantwoordelijk voor database-interacties.
    - Maakt gebruik van Spring Data JPA om queries automatisch te genereren.
    
    **Voorbeeld:**
    
    ```java
    @Repository
    public interface UserRepository extends JpaRepository<User, Long> {
        List<User> findByName(String name);
    }
    ```
    

### Voordelen van de 3-Lagen Architectuur

- **Losse koppeling:** Elke laag is verantwoordelijk voor één specifieke taak, waardoor veranderingen in één laag de andere lagen minimaal beïnvloeden.
- **Herbruikbaarheid:** De servicelaag kan worden hergebruikt in verschillende controllers.
- **Onderhoudbaarheid:** De scheiding van verantwoordelijkheden maakt de codebase overzichtelijker en gemakkelijker te onderhouden.

➡️ Zie ook: [[8 - 3-Lagen Architectuur Introductie van Spring Data JPA]]

---

## Hoofdstuk 9: Spring Data JPA en Relaties

Spring Data JPA ondersteunt het modelleren van complexe database-relaties, waardoor ontwikkelaars eenvoudig relaties tussen entiteiten kunnen beheren in een relationele database. De belangrijkste typen relaties zijn:

### 1. `@OneToOne`

Een één-op-één relatie betekent dat één record in een tabel overeenkomt met precies één record in een andere tabel. Dit wordt gebruikt voor unieke koppelingen, zoals tussen een gebruiker en een profiel.

**Voorbeeld:**

```java
@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;

    @OneToOne(cascade = CascadeType.ALL)
    @JoinColumn(name = "profile_id", referencedColumnName = "id")
    private Profile profile;

    // Getters en setters
}

@Entity
public class Profile {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String bio;

    // Getters en setters
}
```

### 2. `@OneToMany`

Een één-op-veel relatie betekent dat één record in een tabel gekoppeld kan zijn aan meerdere records in een andere tabel. Dit is bijvoorbeeld handig voor een auteur met meerdere boeken.

**Voorbeeld:**

```java
@Entity
public class Author {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
    private List<Book> books = new ArrayList<>();

    // Getters en setters
}

@Entity
public class Book {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToOne
    @JoinColumn(name = "author_id")
    private Author author;

    // Getters en setters
}
```

### 3. `@ManyToMany`

Een veel-op-veel relatie betekent dat meerdere records in een tabel gekoppeld kunnen zijn aan meerdere records in een andere tabel. Een voorbeeld hiervan is studenten die zich inschrijven voor meerdere cursussen.

**Voorbeeld:**

```java
@Entity
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToMany
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private List<Course> courses = new ArrayList<>();

    // Getters en setters
}

@Entity
public class Course {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToMany(mappedBy = "courses")
    private List<Student> students = new ArrayList<>();

    // Getters en setters
}
```

### Fetch Types

Spring JPA biedt twee fetch-strategieën om te bepalen hoe gerelateerde entiteiten worden geladen:

1. **EAGER:** De gerelateerde entiteiten worden onmiddellijk geladen.
2. **LAZY:** De gerelateerde entiteiten worden alleen geladen wanneer ze expliciet worden opgevraagd.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", fetch = FetchType.LAZY)
private List<Book> books;
```

`FetchType.LAZY` wordt aanbevolen voor betere prestaties, tenzij de gegevens direct nodig zijn.

### Cascade Types

Cascade-opties bepalen hoe operaties op een entiteit worden doorgegeven aan gerelateerde entiteiten.

- **ALL:** Voert alle bewerkingen door (persist, merge, remove, refresh, detach).
- **PERSIST:** Alleen `persist`-operaties worden doorgegeven.
- **REMOVE:** Alleen `remove`-operaties worden doorgegeven.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
private List<Book> books;
```

Met `CascadeType.ALL` worden alle wijzigingen aan de `Author` ook toegepast op de gekoppelde `Book`-entiteiten.

➡️ Zie ook: [[9 - Spring Data JPA]]

---

## Hoofdstuk 10: Geavanceerde Database Relaties

Spring JPA biedt tools zoals **cascade types** en **fetch strategies** om het gedrag van entiteiten in complexe relaties te beheren. Deze functionaliteiten zorgen ervoor dat de consistentie tussen gerelateerde entiteiten behouden blijft en de laadtijd wordt geoptimaliseerd.

### Cascade Types

Cascade-opties bepalen hoe operaties (zoals `persist`, `merge`, en `remove`) op een entiteit worden doorgegeven aan gerelateerde entiteiten. Veelgebruikte cascade-opties zijn:

- **`CascadeType.PERSIST`**: Voert alleen persist-operaties door naar de gerelateerde entiteiten.
- **`CascadeType.REMOVE`**: Verwijdert automatisch gerelateerde entiteiten als de hoofdentiteit wordt verwijderd.
- **`CascadeType.ALL`**: Voert alle operaties door, inclusief `persist`, `merge`, en `remove`.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
private List<Book> books;
```

Hier zorgt `CascadeType.ALL` ervoor dat bij het opslaan of verwijderen van een `Author`-entiteit de gerelateerde `Book`-entiteiten automatisch worden verwerkt.

### Fetch Strategies

Fetch-strategieën bepalen hoe gerelateerde entiteiten worden geladen:

1. **`FetchType.LAZY`** (standaard): Laadt gerelateerde entiteiten pas wanneer ze expliciet worden opgevraagd. Dit is efficiënter voor prestaties.
2. **`FetchType.EAGER`**: Laadt gerelateerde entiteiten onmiddellijk bij het laden van de hoofdentiteit.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", fetch = FetchType.LAZY)
private List<Book> books;
```

In dit voorbeeld worden de `Book`-entiteiten pas opgehaald wanneer expliciet om de lijst wordt gevraagd, wat overbodige database-oproepen voorkomt.

➡️ Zie ook: [[10 - Database Relaties met Spring Data JPA]]

---

## Conclusie

Het vak Java Advanced met Spring Boot biedt een solide basis voor het ontwikkelen van schaalbare, robuuste en moderne applicaties. Met tools zoals Spring Data JPA, RESTful webservices, en geavanceerde architecturen leer je niet alleen code te schrijven, maar ook goed ontworpen systemen te bouwen.

Heb je specifieke vragen of wil je meer weten over een bepaald onderwerp? Laat het me weten!