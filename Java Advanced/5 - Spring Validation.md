# Samenvatting Hoofdstuk 5: Spring Validation

## Wat is Spring Validation?

Spring Validation is een module binnen het Spring Framework die helpt om gegevensvalidatie eenvoudig en flexibel te implementeren. Het wordt voornamelijk gebruikt om invoer van gebruikers te valideren in webapplicaties en RESTful API's.

De validatiemodule maakt gebruik van de **Java Bean Validation API** (`javax.validation`) en biedt integratie met annotaties zoals `@Valid` en `@Validated`.

---

## Hoe werkt Spring Validation?

Spring Validation combineert annotaties en validatielogica om automatisch fouten op te sporen in gebruikersinvoer. De validatie wordt toegepast op objecten, vaak DTO's (Data Transfer Objects), en fouten worden verwerkt via een `BindingResult`-object.

### Stappen om Spring Validation te gebruiken:

1. **Afhankelijkheid toevoegen** Voeg de volgende dependency toe aan je project (bijvoorbeeld in `pom.xml`):
    
    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>
    ```
    
2. **Annotaties toevoegen aan je DTO** Gebruik annotaties om validatieregels toe te passen.
    
3. **Validatie uitvoeren** Pas de validatie toe in je controller met `@Valid` of `@Validated`.
    
4. **Fouten verwerken** Controleer op validatiefouten met behulp van `BindingResult`.
    

---

## Belangrijke annotaties voor validatie

Hier zijn enkele veelgebruikte validatieannotaties:

- **@NotNull**: Zorgt ervoor dat een veld niet `null` is.
- **@NotEmpty**: Controleert of een string niet `null` of leeg is.
- **@NotBlank**: Controleert of een string niet `null`, leeg of alleen witruimte is.
- **@Size**: Controleert de lengte van een string of de grootte van een collectie.
- **@Min** / **@Max**: Controleert op een minimale of maximale waarde.
- **@Email**: Controleert of een string een geldig e-mailadres is.
- **@Pattern**: Controleert of een string voldoet aan een regex.

**Voorbeeld DTO:**

```java
public class UserDTO {

    @NotNull(message = "Naam mag niet null zijn")
    @Size(min = 2, max = 30, message = "Naam moet tussen 2 en 30 karakters zijn")
    private String name;

    @NotNull(message = "Leeftijd mag niet null zijn")
    @Min(value = 18, message = "Leeftijd moet minimaal 18 zijn")
    private Integer age;

    @Email(message = "E-mail moet geldig zijn")
    private String email;

    // Getters en setters
}
```

---

## Validatie in de Controller

Gebruik de `@Valid`-annotatie in de controller om de validatie automatisch uit te voeren.

**Voorbeeld Controller:**

```java
@RestController
@RequestMapping("/users")
public class UserController {

    @PostMapping
    public ResponseEntity<String> createUser(@Valid @RequestBody UserDTO userDTO, BindingResult result) {
        if (result.hasErrors()) {
            return ResponseEntity.badRequest().body(result.getAllErrors().toString());
        }
        return ResponseEntity.ok("Gebruiker succesvol aangemaakt");
    }
}
```

In dit voorbeeld:

1. `@Valid` valideert het `UserDTO`-object.
2. `BindingResult` bevat alle validatiefouten.

---

## Custom Validaties

Naast standaardannotaties kun je aangepaste validatielogica schrijven met een custom validator.

### Custom Validatie Schrijven

1. Maak een annotatie:
    
    ```java
    @Target({ ElementType.FIELD })
    @Retention(RetentionPolicy.RUNTIME)
    @Constraint(validatedBy = MyCustomValidator.class)
    public @interface MyCustomValidation {
        String message() default "Ongeldige waarde";
        Class<?>[] groups() default {};
        Class<? extends Payload>[] payload() default {};
    }
    ```
    
2. Implementeer de validatielogica:
    
    ```java
    public class MyCustomValidator implements ConstraintValidator<MyCustomValidation, String> {
        @Override
        public boolean isValid(String value, ConstraintValidatorContext context) {
            return value != null && value.matches("^[A-Z]+$"); // Alleen hoofdletters toegestaan
        }
    }
    ```
    
3. Gebruik de annotatie in een DTO:
    
    ```java
    public class CustomDTO {
    
        @MyCustomValidation(message = "Moet alleen hoofdletters bevatten")
        private String code;
    
        // Getters en setters
    }
    ```
    

---

## Fouten en Validatieberichten

Foutberichten kunnen worden aangepast in `application.properties` of met resourcebundles.

**Voorbeeld:**

```properties
userDTO.name.NotNull=Naam is verplicht
userDTO.age.Min=Leeftijd moet minimaal {value} zijn
```

Deze foutberichten worden automatisch gebruikt bij validatiefouten.

---

## Conclusie

Spring Validation biedt een krachtige manier om gebruikersinvoer in applicaties te valideren. Met standaardannotaties, eenvoudige integratie en de mogelijkheid om custom validators te maken, helpt het ontwikkelaars om robuuste en veilige applicaties te bouwen.

Heb je verdere vragen over Spring Validation? Laat het me weten!