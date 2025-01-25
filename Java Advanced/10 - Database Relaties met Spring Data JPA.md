# Samenvatting Hoofdstuk 10: Database Relaties met Spring Data JPA

## Wat zijn database relaties?

Relationele databases maken gebruik van relaties tussen tabellen om gegevens op een gestructureerde manier te organiseren. In Spring Data JPA worden deze relaties gemodelleerd met behulp van annotaties zoals `@OneToOne`, `@OneToMany`, `@ManyToOne`, en `@ManyToMany`. Dit maakt het eenvoudig om complexe datamodellen te implementeren.

---

## Soorten relaties in Spring Data JPA

### 1. One-to-One relatie

Een `One-to-One`-relatie betekent dat één record in een tabel overeenkomt met exact één record in een andere tabel.

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

Hier wordt een `User` gekoppeld aan een `Profile` via de kolom `profile_id`.

---

### 2. One-to-Many relatie

Een `One-to-Many`-relatie betekent dat één record in een tabel kan corresponderen met meerdere records in een andere tabel.

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

Hier kan één `Author` meerdere `Book`-records hebben.

---

### 3. Many-to-Many relatie

Een `Many-to-Many`-relatie betekent dat meerdere records in een tabel kunnen corresponderen met meerdere records in een andere tabel.

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

Hier kunnen meerdere `Student`-records zich inschrijven voor meerdere `Course`-records.

---

## Cascade Types

Spring Data JPA biedt verschillende cascade types die bepalen hoe operaties op een entiteit worden doorgegeven aan de gerelateerde entiteiten:

- **ALL**: Voert alle operaties door.
- **PERSIST**: Alleen `persist`-operaties.
- **MERGE**: Alleen `merge`-operaties.
- **REMOVE**: Alleen `remove`-operaties.
- **REFRESH**: Alleen `refresh`-operaties.
- **DETACH**: Alleen `detach`-operaties.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", cascade = CascadeType.ALL)
private List<Book> books;
```

Hier zorgt `CascadeType.ALL` ervoor dat operaties op `Author` ook worden doorgevoerd naar de gekoppelde `Book`-entiteiten.

---

## Fetch Types

Spring Data JPA ondersteunt twee soorten fetch-strategieën:

1. **EAGER**: Laadt de gerelateerde entiteit direct mee.
2. **LAZY**: Laadt de gerelateerde entiteit alleen wanneer deze expliciet wordt opgevraagd.

**Voorbeeld:**

```java
@OneToMany(mappedBy = "author", fetch = FetchType.LAZY)
private List<Book> books;
```

Standaard is `LAZY` aanbevolen om prestaties te optimaliseren.

---

## Voorbeeld: API met Relaties

Hier is een voorbeeld van een eenvoudige API om `Author` en `Book`-entiteiten te beheren:

### Controller:

```java
@RestController
@RequestMapping("/authors")
public class AuthorController {

    @Autowired
    private AuthorService authorService;

    @GetMapping
    public List<Author> getAllAuthors() {
        return authorService.getAllAuthors();
    }

    @PostMapping
    public Author createAuthor(@RequestBody Author author) {
        return authorService.createAuthor(author);
    }
}
```

### Service:

```java
@Service
public class AuthorService {

    @Autowired
    private AuthorRepository authorRepository;

    public List<Author> getAllAuthors() {
        return authorRepository.findAll();
    }

    public Author createAuthor(Author author) {
        return authorRepository.save(author);
    }
}
```

### Repository:

```java
public interface AuthorRepository extends JpaRepository<Author, Long> {
}
```

---

## Conclusie

Hoofdstuk 10 behandelt de implementatie van database-relaties met Spring Data JPA. Door het gebruik van annotaties zoals `@OneToOne`, `@OneToMany`, en `@ManyToMany` kunnen ontwikkelaars complexe datamodellen eenvoudig en efficiënt implementeren. Dit maakt Spring Data JPA een krachtig hulpmiddel voor applicaties die afhankelijk zijn van relationele databases.

Heb je vragen over dit hoofdstuk? Laat het me weten!