# Samenvatting Hoofdstuk 9: Spring Data JPA

## Wat is Spring Data JPA?

Spring Data JPA is een module binnen het Spring Framework die het werken met relationele databases sterk vereenvoudigt. Het bouwt voort op de Java Persistence API (JPA) en biedt een abstractie die boilerplate-code elimineert, zoals het schrijven van SQL-queries of configureren van ORM-mappings.

### Voordelen van Spring Data JPA:

- **Productiviteit:** Minder handmatige configuratie.
- **Querygeneratie:** Automatische querygeneratie op basis van methodenamen.
- **Complexe relaties:** Ondersteuning voor geavanceerde database-relaties zoals One-to-Many en Many-to-Many.
- **Integratie:** Gemakkelijke integratie met andere Spring-componenten.

---

## Belangrijke concepten in Spring Data JPA

### 1. Entities

Een Entity is een klasse die wordt gemapt naar een tabel in de database. Het wordt geannoteerd met `@Entity` en bevat annotaties om kolommen en relaties te definiëren.

**Voorbeeld:**

```java
import jakarta.persistence.*;

@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private Double price;

    // Getters en setters
}
```

### 2. Repositories

Repositories zijn interfaces die verantwoordelijk zijn voor database-operaties. Door `JpaRepository` te extenden, worden standaard CRUD-methoden beschikbaar.

**Voorbeeld:**

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface ProductRepository extends JpaRepository<Product, Long> {
    List<Product> findByName(String name);
}
```

Hier wordt de methode `findByName` automatisch gegenereerd door Spring Data JPA.

### 3. Relaties tussen Entities

Spring Data JPA ondersteunt complexe database-relaties zoals:

- **One-to-One**: Gebruik `@OneToOne`.
- **One-to-Many**: Gebruik `@OneToMany`.
- **Many-to-Many**: Gebruik `@ManyToMany`.

**Voorbeeld: One-to-Many-relatie:**

```java
@Entity
public class Category {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "category", cascade = CascadeType.ALL)
    private List<Product> products = new ArrayList<>();

    // Getters en setters
}

@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToOne
    @JoinColumn(name = "category_id")
    private Category category;

    // Getters en setters
}
```

---

## Querymethoden

### Automatisch gegenereerde queries

Spring Data JPA kan queries genereren op basis van methodenamen.

**Voorbeelden:**

```java
List<Product> findByName(String name);
List<Product> findByPriceLessThan(Double price);
List<Product> findByNameContaining(String keyword);
```

### Custom queries met `@Query`

Voor complexere queries kun je de annotatie `@Query` gebruiken.

**Voorbeeld:**

```java
@Query("SELECT p FROM Product p WHERE p.price > :price")
List<Product> findProductsByPriceGreaterThan(@Param("price") Double price);
```

---

## Transacties in Spring Data JPA

Spring Data JPA ondersteunt transactiebeheer met de annotatie `@Transactional`. Hiermee kun je meerdere database-operaties samenvoegen in één transactie.

**Voorbeeld:**

```java
@Service
public class ProductService {

    @Autowired
    private ProductRepository productRepository;

    @Transactional
    public void updateProductAndCategory(Product product, Category category) {
        productRepository.save(product);
        // Stel dat er hier een exception optreedt
        // Beide operaties worden teruggedraaid
    }
}
```

---

## Voorbeeld: Productbeheer met Spring Data JPA

Hier is een voorbeeld van hoe je Spring Data JPA gebruikt in een eenvoudige 3-lagen architectuur.

### Controller:

```java
@RestController
@RequestMapping("/products")
public class ProductController {

    @Autowired
    private ProductService productService;

    @GetMapping
    public List<Product> getAllProducts() {
        return productService.getAllProducts();
    }

    @PostMapping
    public Product createProduct(@RequestBody Product product) {
        return productService.saveProduct(product);
    }
}
```

### Service:

```java
@Service
public class ProductService {

    @Autowired
    private ProductRepository productRepository;

    public List<Product> getAllProducts() {
        return productRepository.findAll();
    }

    public Product saveProduct(Product product) {
        return productRepository.save(product);
    }
}
```

### Repository:

De repository maakt gebruik van `JpaRepository`, zoals eerder beschreven.

---

## Conclusie

Spring Data JPA is een krachtige module die database-operaties aanzienlijk vereenvoudigt. Door het gebruik van Entities, Repositories en automatische querygeneratie, kunnen ontwikkelaars zich meer richten op bedrijfslogica en minder op boilerplate-code. Dit hoofdstuk biedt een solide basis voor het werken met relationele databases in Java-applicaties.

Heb je verdere vragen? Laat het me weten!