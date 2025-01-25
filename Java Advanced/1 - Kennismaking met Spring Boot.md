# Samenvatting Hoofdstuk 1: Kennismaking met Spring Boot

## Wat is Spring Boot?

Spring Boot is een open-source framework dat is ontworpen om het ontwikkelen van enterprise-applicaties in Java eenvoudiger en efficiënter te maken. Het is gebouwd bovenop het Spring Framework en biedt standaardinstellingen en ingebouwde hulpmiddelen om snel aan de slag te gaan met moderne applicatieontwikkeling.

### Belangrijke kenmerken van enterprise-applicaties

Enterprise-toepassingen ondersteunen bedrijfsprocessen en worden gekenmerkt door:

- **Schaalbaarheid**: Ze moeten een groot aantal gebruikers en gegevens aankunnen.
- **Betrouwbaarheid**: Continu beschikbaarheid en snelle responstijden.
- **Beveiliging**: Robuuste authenticatie, autorisatie en versleuteling.
- **Integratie**: Samenwerking met externe systemen zoals databases en API’s.
- **Flexibiliteit**: Aanpasbaarheid aan veranderende zakelijke eisen.
- **Lange levenscyclus**: Regelmatig onderhoud, updates en verbeteringen.

Spring Boot vereenvoudigt het voldoen aan deze vereisten door krachtige tools en frameworks te combineren.

---

## Waarom kiezen voor Spring Boot?

Spring Boot biedt diverse voordelen voor ontwikkelaars:

- **Weinig configuratie**: Automatische configuratie en ingebouwde instellingen.
- **Snelle ontwikkeling**: Tools zoals Spring Initializr helpen bij het snel opzetten van projecten.
- **Productiviteit**: Minder boilerplate-code en meer focus op businesslogica.
- **Modulariteit**: Ondersteuning voor microservices-architecturen.

### Voorbeeld: Een eenvoudige Spring Boot-applicatie

```java
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

Deze applicatie maakt gebruik van de annotatie `@SpringBootApplication`, die automatisch belangrijke configuraties inschakelt:

- **@EnableAutoConfiguration**: Activeert de automatische configuratie van Spring.
- **@ComponentScan**: Zoekt automatisch naar componenten en beans.
- **@Configuration**: Staat toe om extra beans te definiëren.

---

## De rol van Spring Initializr

Spring Initializr is een webtool waarmee je eenvoudig een Spring Boot-project kunt genereren. Via een gebruiksvriendelijke interface selecteer je:

- **Buildtool**: Maven of Gradle.
- **Taal**: Java, Kotlin of Groovy.
- **Spring Boot-versie**: Bijvoorbeeld 3.3.3 (Long-Term Support).
- **Afhankelijkheden**: Zoals Spring Web, Spring Data JPA, etc.

### Maven-folderstructuur

Wanneer Maven als buildtool wordt gebruikt, heeft je project de volgende structuur:

```
src/main/java    # Broncode
src/test/java    # Testcode
pom.xml          # Projectconfiguratie
```

---

## Inversion of Control (IoC) en Dependency Injection (DI)

### Wat is IoC?

In een traditioneel Java-programma maken klassen hun eigen afhankelijkheden aan, wat resulteert in sterke koppelingen. IoC draait dit principe om door de verantwoordelijkheid voor objectcreatie over te dragen aan een container, zoals de **Application Context** in Spring Boot. Dit leidt tot een flexibelere en beter testbare architectuur.

### Wat is DI?

Dependency Injection (DI) is een techniek waarbij objecten hun afhankelijkheden van buitenaf ontvangen, in plaats van deze zelf te creëren. Spring Boot ondersteunt drie vormen van DI:

- **Constructor Injection**: Voorkeur vanwege zijn immutabiliteit.
- **Setter Injection**: Geschikt voor optionele afhankelijkheden.
- **Field Injection**: Minder aanbevolen vanwege moeilijkere testbaarheid.

### Voorbeeld: IoC en DI

#### Zonder IoC

```java
public class Car {
    private Engine engine = new Engine();

    public void drive() {
        engine.start();
    }
}
```

#### Met IoC

```java
public class Car {
    private Engine engine;

    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        engine.start();
    }
}

@Bean
public Engine petrolEngine() {
    return new PetrolEngine();
}

@Bean
public Car myCar() {
    return new Car(petrolEngine());
}
```

Met Spring Boot wordt het object `Car` beheerd door de IoC-container, die de juiste `Engine` injecteert.

---

## Spring Beans en de Application Context

### Wat zijn Spring Beans?

Spring Beans zijn objecten die door de IoC-container worden beheerd. Ze worden geannoteerd met:

- **@Component**: Voor algemene componenten.
- **@Service**: Voor servicelogica.
- **@Repository**: Voor datatoegang.
- **@Controller** of **@RestController**: Voor webcontrollers.

### Wat is de Application Context?

De Application Context is het centrale mechanisme van Spring waarin alle beans en configuraties worden beheerd. Het:

1. Laadt alle gedefinieerde beans.
2. Verzorgt de injectie van afhankelijkheden.
3. Handhaaft de levenscyclus van beans.

### Voorbeeld van een Spring Bean

```java
@Component
public class WelcomeMessage implements CommandLineRunner {

    @Override
    public void run(String... args) {
        System.out.println("Welcome to Spring Boot!");
    }
}
```

Bij het opstarten van de applicatie wordt de `run`-methode uitgevoerd, wat ideaal is voor initiële taken.

---

## Annotaties en configuratie

Spring Boot maakt intensief gebruik van annotaties om configuratie eenvoudiger te maken.

### Belangrijke annotaties

- **@SpringBootApplication**: Combineert meerdere configuratieannotaties.
- **@Bean**: Definieert een bean in de context.
- **@Autowired**: Injecteert afhankelijkheden automatisch.
- **@ComponentScan**: Scant pakketten op componenten.

### Logging configureren

Via het bestand `application.properties` kun je logging-instellingen aanpassen:

```properties
logging.level.org.springframework=debug
```

Dit helpt om te zien hoe de automatische configuratie van Spring Boot werkt.

---

## Conclusie

Hoofdstuk 1 introduceert Spring Boot als een krachtig framework voor het bouwen van enterprise-applicaties. Met hulpmiddelen zoals IoC, DI, Spring Initializr en een krachtige configuratie-infrastructuur, helpt Spring Boot ontwikkelaars om efficiënter te werken en complexe bedrijfsbehoeften aan te pakken.

Heb je specifieke vragen of behoefte aan meer voorbeelden? Laat het me weten!