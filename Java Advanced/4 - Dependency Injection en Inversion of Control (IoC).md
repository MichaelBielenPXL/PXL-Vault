# Samenvatting Hoofdstuk 4: Dependency Injection en Inversion of Control (IoC)

## Wat is Inversion of Control (IoC)?

Inversion of Control (IoC) is een ontwerppatroon dat de afhankelijkheidsrelaties binnen een applicatie beheert door een container te gebruiken om objecten aan te maken en hun afhankelijkheden te injecteren. Dit bevordert losgekoppelde architecturen en verhoogt de testbaarheid van code.

In traditionele Java-code:

- Klassen maken hun eigen afhankelijkheden aan.
- Er is sprake van een sterke koppeling, wat onderhoud bemoeilijkt.

Met IoC:

- De controle over objectcreatie wordt omgedraaid en aan een IoC-container gegeven.
- De container beheert de levenscyclus en injectie van objecten.

---

## Dependency Injection (DI)

Dependency Injection is een vorm van IoC waarbij afhankelijkheden aan objecten worden geleverd in plaats van deze direct in de klasse te creëren. Spring ondersteunt verschillende vormen van DI:

### 1. Constructor Injection

Afhankelijkheden worden doorgegeven via de constructor van een klasse. **Voorbeeld:**

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

Hier wordt de afhankelijkheid (`Engine`) geïnjecteerd via de constructor.

### 2. Setter Injection

Afhankelijkheden worden via setter-methoden geïnjecteerd. **Voorbeeld:**

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

Setter-injectie is handig voor optionele afhankelijkheden.

### 3. Field Injection

Afhankelijkheden worden rechtstreeks geïnjecteerd in een veld met de annotatie `@Autowired`. **Voorbeeld:**

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

Hoewel dit populair is vanwege de eenvoud, wordt constructor-injectie aanbevolen voor betere testbaarheid.

---

## Beans en de IoC-container

### Wat zijn Beans?

Beans zijn objecten die door de IoC-container worden beheerd. Ze worden gedefinieerd en geïnjecteerd door annotaties of XML-configuratie.

### Belangrijke annotaties

1. **@Component**: Geeft aan dat een klasse een bean is.
2. **@Service**: Specifiek voor servicelogica.
3. **@Repository**: Specifiek voor data-toegang.
4. **@Controller**: Specifiek voor webcontrollers.

**Voorbeeld:**

```java
@Component
public class Engine {
    public void start() {
        System.out.println("Engine started");
    }
}
```

### Configureren van Beans

Beans kunnen worden geconfigureerd met behulp van de `@Bean`-annotatie binnen een configuratieklasse. **Voorbeeld:**

```java
@Configuration
public class AppConfig {

    @Bean
    public Engine engine() {
        return new Engine();
    }

    @Bean
    public Car car() {
        return new Car(engine());
    }
}
```

De IoC-container beheert automatisch de afhankelijkheden tussen `Car` en `Engine`.

---

## Voordelen van Dependency Injection

- **Losse koppeling:** Klassen zijn minder afhankelijk van elkaar.
- **Eenvoudige testbaarheid:** Mocking van afhankelijkheden is eenvoudig.
- **Beheerbare levenscyclus:** De container regelt de creatie en het opruimen van objecten.
- **Herbruikbare code:** Objecten kunnen eenvoudiger worden hergebruikt binnen verschillende contexten.

---

## Conclusie

Hoofdstuk 4 behandelt de kernprincipes van Dependency Injection en Inversion of Control. Door gebruik te maken van Spring’s IoC-container en DI-mechanismen, kunnen ontwikkelaars robuuste en onderhoudbare applicaties bouwen met losgekoppelde architecturen. Dit maakt Spring een krachtig framework voor enterprise Java-ontwikkeling.

Heb je specifieke vragen over DI of IoC? Laat het me weten!