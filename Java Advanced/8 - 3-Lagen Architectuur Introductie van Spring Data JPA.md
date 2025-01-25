# Samenvatting Hoofdstuk 8: 3-Lagen Architectuur: Introductie van Spring Data JPA

## Wat is een 3-lagen architectuur?

De 3-lagen architectuur is een ontwerpmodel dat softwaretoepassingen verdeelt in drie afzonderlijke lagen:

1. **Presentatielaag (Controller):** Verantwoordelijk voor de interactie met de gebruiker of client.
2. **Servicelaag (Service):** Bevat de bedrijfslogica van de applicatie.
3. **Datalaag (Repository):** Verwerkt de communicatie met de database.

Het doel van deze architectuur is om een duidelijke scheiding van verantwoordelijkheden te creëren, wat onderhoud en schaalbaarheid van de applicatie vergemakkelijkt.

---

## Introductie tot Spring Data JPA

Spring Data JPA is een module van Spring die het werken met relationele databases vereenvoudigt door gebruik te maken van de Java Persistence API (JPA). Het biedt een abstractielaag bovenop JPA en elimineert boilerplate-code voor database-interacties.

### Voordelen van Spring Data JPA

- **Snellere ontwikkeling:** Automatisch gegenereerde queries.
- **Integratie met Spring:** Natuurlijke integratie met andere Spring-modules.
- **Schaalbaarheid:** Ondersteunt complexe relaties en grote datasets.

---

## Configuratie van Spring Data JPA

Om Spring Data JPA te gebruiken, volg je deze stappen:

1. **Voeg afhankelijkheden toe** Voeg de volgende dependencies toe in `pom.xml`:
    
    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>
    ```
    
2. **Configureer de database** Voeg de databaseconfiguratie toe in `application.properties`:
    
    ```properties
    spring.datasource.url=jdbc:h2:mem:testdb
    spring.datasource.driverClassName=org.h2.Driver
    spring.datasource.username=sa
    spring.datasource.password=password
    spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
    ```
    
3. **Creëer een Entity** Gebruik de annotatie `@Entity` om een klasse te koppelen aan een database.
    
    ```java
    import jakarta.persistence.*;
    
    @Entity
    public class User {
    
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
    
        private String name;
        private String email;
    
        // Getters en setters
    }
    ```
    
4. **Creëer een Repository** Gebruik de interface `JpaRepository` om CRUD-operaties te beheren.
    
    ```java
    import org.springframework.data.jpa.repository.JpaRepository;
    
    public interface UserRepository extends JpaRepository<User, Long> {
    }
    ```
    

---

## Gebruik van Spring Data JPA in een 3-lagen architectuur

### 1. Presentatielaag (Controller)

De controller behandelt HTTP-verzoeken en roept methoden aan in de servicelaag.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

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

### 2. Servicelaag (Service)

De servicelaag bevat de bedrijfslogica.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

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

### 3. Datalaag (Repository)

De repositorylaag maakt gebruik van `JpaRepository` om database-interacties te beheren. Dit is al geïmplementeerd in het voorbeeld hierboven.

---

## Querymethoden in Spring Data JPA

Spring Data JPA biedt de mogelijkheid om queries automatisch te genereren op basis van methodenamen.

**Voorbeelden van querymethoden:**

```java
List<User> findByName(String name);
List<User> findByEmailContaining(String emailFragment);
List<User> findByNameAndEmail(String name, String email);
```

Voor complexere queries kun je de annotatie `@Query` gebruiken:

```java
@Query("SELECT u FROM User u WHERE u.email LIKE %:email%")
List<User> searchByEmail(@Param("email") String email);
```

---

## Conclusie

Hoofdstuk 8 introduceert de 3-lagen architectuur en de voordelen van Spring Data JPA. Door een duidelijke scheiding tussen presentatie-, service- en datalaag wordt de code beter onderhoudbaar en schaalbaar. Spring Data JPA vereenvoudigt database-interacties aanzienlijk en verhoogt de productiviteit van ontwikkelaars.

Heb je vragen of verdere uitleg nodig? Laat het me weten!