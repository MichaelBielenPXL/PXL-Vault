# Samenvatting Hoofdstuk 6: Unit Testen met JUnit

## Wat is Unit Testing?

Unit testing is een softwaretesttechniek waarbij individuele eenheden of componenten van een applicatie worden getest. Het doel is om te controleren of elke eenheid correct functioneert. In Java wordt JUnit vaak gebruikt als testframework.

Eenheden in unit testing zijn meestal methoden, maar kunnen ook kleinere logische componenten zijn.

---

## JUnit Framework

JUnit is een populair open-source testframework in Java dat wordt gebruikt voor het schrijven en uitvoeren van tests. Het biedt annotaties en hulpprogramma's om tests eenvoudiger te maken.

### Belangrijke Annotaties in JUnit

- **@Test**: Markeert een methode als een testmethode.
- **@BeforeEach**: Voert een methode uit vóór elke testmethode.
- **@AfterEach**: Voert een methode uit na elke testmethode.
- **@BeforeAll**: Voert een methode uit vóór alle testmethoden (moet `static` zijn).
- **@AfterAll**: Voert een methode uit na alle testmethoden (moet `static` zijn).
- **@Disabled**: Schakelt een test tijdelijk uit.

---

## Een Eenvoudige JUnit Test

Hier is een voorbeeld van een eenvoudige JUnit-test:

**Codevoorbeeld:**

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
- De test zal slagen als de methode `add` het correcte resultaat retourneert.

---

## Test Lifecycle in JUnit

JUnit voert tests uit in een bepaalde volgorde met behulp van annotaties zoals `@BeforeEach` en `@AfterEach`. Dit maakt het mogelijk om herhalende voorbereidingen of opruimacties te automatiseren.

**Voorbeeld:**

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.Test;

public class SampleTest {

    @BeforeEach
    void setUp() {
        System.out.println("Voor elke test");
    }

    @AfterEach
    void tearDown() {
        System.out.println("Na elke test");
    }

    @Test
    void testExample() {
        System.out.println("Test uitgevoerd");
    }
}
```

**Uitvoer:**

```
Voor elke test
Test uitgevoerd
Na elke test
```

---

## Assertions

JUnit biedt een reeks assertiemethoden om testvoorwaarden te controleren. Hier zijn enkele veelgebruikte:

|Methode|Beschrijving|
|---|---|
|`assertEquals`|Controleert of twee waarden gelijk zijn.|
|`assertNotEquals`|Controleert of twee waarden ongelijk zijn.|
|`assertTrue`|Controleert of een voorwaarde waar is.|
|`assertFalse`|Controleert of een voorwaarde onwaar is.|
|`assertNull`|Controleert of een object `null` is.|
|`assertNotNull`|Controleert of een object niet `null` is.|
|`assertThrows`|Controleert of een uitzondering wordt gegooid.|

**Voorbeeld van `assertThrows`:**

```java
@Test
void testException() {
    assertThrows(IllegalArgumentException.class, () -> {
        throw new IllegalArgumentException("Ongeldige invoer");
    });
}
```

---

## Mocking met Mockito

In unit tests is het soms nodig om afhankelijkheden van een klasse te simuleren. Dit kan worden bereikt met **Mockito**, een mocking-framework dat goed integreert met JUnit.

### Voorbeeld met Mockito

1. Voeg de Mockito-dependency toe:
    
    ```xml
    <dependency>
        <groupId>org.mockito</groupId>
        <artifactId>mockito-core</artifactId>
        <version>4.0.0</version>
        <scope>test</scope>
    </dependency>
    ```
    
2. Gebruik Mockito om een afhankelijkheid te mocken:
    
    ```java
    import static org.mockito.Mockito.*;
    import org.junit.jupiter.api.Test;
    import org.mockito.Mockito;
    
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
    
    Hier wordt een `UserRepository`-object gemockt en een specifieke returnwaarde ingesteld.
    

---

## Conclusie

JUnit is een essentieel hulpmiddel voor unit testing in Java. Het biedt een gestructureerde aanpak om de kwaliteit van code te waarborgen en fouten vroegtijdig op te sporen. Samen met frameworks zoals Mockito maakt het uitgebreide en flexibele tests mogelijk.

Heb je aanvullende vragen of specifieke hulp nodig bij JUnit? Laat het weten!