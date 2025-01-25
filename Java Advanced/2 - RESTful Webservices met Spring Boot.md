# Samenvatting Hoofdstuk 2: RESTful Webservices met Spring Boot

## Wat is REST?

REST (Representational State Transfer) is een architectuurstijl voor communicatie tussen verschillende softwaretoepassingen. REST maakt gebruik van standaard HTTP-methoden om gegevens te manipuleren en op te halen. De meest gebruikte HTTP-methoden zijn:

- **GET**: Haal gegevens op van een server.
- **POST**: Voeg nieuwe gegevens toe aan een server.
- **PUT**: Werk bestaande gegevens bij.
- **DELETE**: Verwijder gegevens van een server.

RESTful webservices stellen resources beschikbaar via unieke URI’s (Uniform Resource Identifiers) en maken gebruik van JSON of XML als gegevensformaten.

---

## Spring Boot en REST

Spring Boot biedt krachtige ondersteuning voor het bouwen van RESTful webservices via het Spring Web-module. Met behulp van annotaties zoals `@RestController` en `@RequestMapping` kun je eenvoudig REST-API’s implementeren.

### Belangrijke annotaties voor REST

- **@RestController**: Markeert een klasse als een REST-controller die HTTP-verzoeken afhandelt en JSON of XML als antwoord retourneert.
- **@RequestMapping**: Geeft het pad aan waarop de controller reageert.
- **@GetMapping**: Handelt GET-verzoeken af.
- **@PostMapping**: Handelt POST-verzoeken af.
- **@PutMapping**: Handelt PUT-verzoeken af.
- **@DeleteMapping**: Handelt DELETE-verzoeken af.

### Voorbeeld: Een eenvoudige REST-controller

```java
@RestController
@RequestMapping("/greetings")
public class GreetingController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }

    @GetMapping("/goodbye")
    public String sayGoodbye() {
        return "Goodbye, World!";
    }
}
```

In dit voorbeeld:

- `/greetings/hello` retourneert een begroeting.
- `/greetings/goodbye` retourneert een afscheid.

---

## Spring Boot Starter Web

De dependency `spring-boot-starter-web` bevat alle tools die nodig zijn voor het ontwikkelen van RESTful webservices. Dit omvat:

- **Spring MVC**: Voor het afhandelen van webverzoeken.
- **Tomcat**: Een ingebouwde webserver.
- **Jackson**: Voor het serialiseren en deserialiseren van JSON.

### Toevoegen van de Starter Web-dependency

Voeg de volgende dependency toe in `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

Wanneer je de applicatie start, wordt automatisch een embedded Tomcat-server opgestart op poort 8080.

---

## Voorbeeld: Music Playlist API

Laten we een eenvoudige API maken voor het beheren van een muzieklijst.

### Endpoints

- **POST /playlist/songs**: Voeg een nieuw liedje toe.
- **GET /playlist/songs**: Haal alle liedjes op.
- **GET /playlist/songs/{genre}**: Haal liedjes op van een specifiek genre.
- **PUT /playlist/songs/{index}**: Werk een liedje bij op basis van de index.
- **DELETE /playlist/songs/{index}**: Verwijder een liedje op basis van de index.

### Controller

```java
@RestController
@RequestMapping("/playlist/songs")
public class MusicPlaylistController {

    private final MusicPlaylistService service;

    @Autowired
    public MusicPlaylistController(MusicPlaylistService service) {
        this.service = service;
    }

    @PostMapping
    public void addSong(@RequestBody Song song) {
        service.addSong(song);
    }

    @GetMapping
    public List<Song> getSongs() {
        return service.getSongs();
    }

    @GetMapping("/{genre}")
    public List<Song> getSongsByGenre(@PathVariable String genre) {
        return service.getSongsByGenre(genre);
    }

    @PutMapping("/{index}")
    public void updateSong(@PathVariable int index, @RequestBody Song song) {
        service.updateSong(index, song);
    }

    @DeleteMapping("/{index}")
    public void deleteSong(@PathVariable int index) {
        service.deleteSong(index);
    }
}
```

### Service

```java
@Service
public class MusicPlaylistService {
    private final List<Song> songs = new ArrayList<>();

    public void addSong(Song song) {
        songs.add(song);
    }

    public List<Song> getSongs() {
        return songs;
    }

    public List<Song> getSongsByGenre(String genre) {
        return songs.stream()
                    .filter(song -> song.getGenre().equalsIgnoreCase(genre))
                    .collect(Collectors.toList());
    }

    public void updateSong(int index, Song song) {
        songs.set(index, song);
    }

    public void deleteSong(int index) {
        songs.remove(index);
    }
}
```

### Model

```java
public class Song {
    private String title;
    private String artist;
    private String genre;
    private int durationSeconds;

    // Getters and setters...
}
```

---

## Conclusie

Hoofdstuk 2 behandelt het bouwen van RESTful webservices met Spring Boot. Het biedt een krachtige basis om API’s te maken en gegevens uit te wisselen via HTTP. Door gebruik te maken van annotaties en Spring Boot Starter Web kun je snel en eenvoudig robuuste applicaties ontwikkelen.

Heb je specifieke vragen of wil je meer weten over een bepaald aspect? Laat het me weten!