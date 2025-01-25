# Samenvatting Hoofdstuk 7: Lambda Expressies en Streams

## Lambda Expressies in Java

Lambda-expressies, geïntroduceerd in Java 8, bieden een beknopte manier om functies te definiëren en door te geven als objecten. Ze zijn vooral nuttig bij het werken met Java's **Stream API** en maken het eenvoudiger om functionele programmeerconcepten te gebruiken.

### Syntax van Lambda Expressies

Een lambda-expressie heeft de volgende vorm:

```java
(parameters) -> { body }
```

- **Parameters**: De invoerwaarden van de functie.
- **Body**: De implementatie van de functie.

**Voorbeelden:**

1. Een eenvoudige expressie:
    
    ```java
    (int x, int y) -> x + y
    ```
    
2. Zonder typeaanduiding:
    
    ```java
    (x, y) -> x + y
    ```
    
3. Zonder haakjes bij één parameter:
    
    ```java
    x -> x * x
    ```
    
4. Meerdere regels in de body:
    
    ```java
    (x, y) -> {
        int sum = x + y;
        return sum;
    }
    ```
    

---

## Functional Interfaces

Lambda-expressies werken samen met **functional interfaces**, dat zijn interfaces met slechts één abstracte methode. Java biedt enkele ingebouwde functional interfaces in het package `java.util.function`.

### Veelgebruikte Functional Interfaces

1. **Predicate**: Controleert of een voorwaarde waar is.
    
    ```java
    Predicate<String> isLongerThan5 = s -> s.length() > 5;
    ```
    
2. **Function**: Transformeert een invoer naar een uitvoer.
    
    ```java
    Function<Integer, String> intToString = i -> "Nummer: " + i;
    ```
    
3. **Consumer**: Voert een actie uit zonder een resultaat te retourneren.
    
    ```java
    Consumer<String> print = s -> System.out.println(s);
    ```
    
4. **Supplier**: Levert een object zonder invoer.
    
    ```java
    Supplier<Double> randomValue = () -> Math.random();
    ```
    
5. **BiFunction**: Werkt met twee invoerwaarden en retourneert een resultaat.
    
    ```java
    BiFunction<Integer, Integer, Integer> multiply = (a, b) -> a * b;
    ```
    

---

## Stream API

De **Stream API**, geïntroduceerd in Java 8, biedt een krachtige manier om collecties en arrays te verwerken door middel van functionele operaties zoals filteren, mappen en reduceren. Streams zijn lenig, declaratief en maken gebruik van lazy evaluation.

### Kenmerken van Streams

1. **Niet-destructief**: Streams wijzigen de originele bron niet.
2. **Lazy evaluation**: Operaties worden pas uitgevoerd wanneer nodig.
3. **Declaratief**: Beschrijft wat er moet gebeuren, niet hoe.

---

## Veelgebruikte Stream Operaties

1. **`filter`**: Filtert elementen op basis van een voorwaarde.
    
    ```java
    List<String> names = List.of("Alice", "Bob", "Charlie");
    List<String> filtered = names.stream()
        .filter(name -> name.startsWith("A"))
        .collect(Collectors.toList());
    ```
    
2. **`map`**: Transformeert elk element.
    
    ```java
    List<Integer> numbers = List.of(1, 2, 3);
    List<Integer> squared = numbers.stream()
        .map(n -> n * n)
        .collect(Collectors.toList());
    ```
    
3. **`forEach`**: Voert een actie uit op elk element.
    
    ```java
    numbers.stream()
        .forEach(System.out::println);
    ```
    
4. **`reduce`**: Combineert alle elementen tot één resultaat.
    
    ```java
    int sum = numbers.stream()
        .reduce(0, (a, b) -> a + b);
    ```
    
5. **`sorted`**: Sorteert de elementen.
    
    ```java
    List<String> sortedNames = names.stream()
        .sorted()
        .collect(Collectors.toList());
    ```
    

---

## Parallel Streams

Java Streams ondersteunen parallelle verwerking om gebruik te maken van meerdere CPU-kernen. Dit wordt gedaan met de methode `parallelStream()`.

**Voorbeeld:**

```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);
numbers.parallelStream()
    .forEach(n -> System.out.println(Thread.currentThread().getName() + " - " + n));
```

Hoewel parallelle streams de prestaties kunnen verbeteren, is voorzichtigheid geboden bij het verwerken van niet-threadveilige collecties.

---

## Voorbeeld: Gebruik van Lambda's en Streams

Hier is een praktijkvoorbeeld dat lambda's en streams combineert:

```java
List<String> names = List.of("Alice", "Bob", "Charlie", "David");
List<String> filteredAndUppercase = names.stream()
    .filter(name -> name.length() > 3)
    .map(String::toUpperCase)
    .sorted()
    .collect(Collectors.toList());

System.out.println(filteredAndUppercase);
```

**Uitvoer:**

```
[ALICE, CHARLIE, DAVID]
```

---

## Conclusie

Hoofdstuk 7 bespreekt de kracht van lambda-expressies en de Stream API in Java. Deze tools maken Java-programma's compacter, leesbaarder en krachtiger door functionele programmeerconcepten toe te voegen. Ze zijn vooral nuttig voor het verwerken van collecties en het schrijven van declaratieve code.

Heb je vragen over lambda's of streams? Laat het me weten!