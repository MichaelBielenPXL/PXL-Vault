# Samenvatting Hoofdstuk 3: Collections: Map

## Overzicht van de Map-interface

In Java is de `Map`-interface een belangrijk onderdeel van het Java Collections Framework. Het wordt gebruikt om key-value-paren (sleutel-waarde-paren) op te slaan en te beheren. Veelgebruikte implementaties van de `Map`-interface zijn:

- **HashMap**
- **LinkedHashMap**
- **TreeMap**
- **Hashtable**

De `Map`-interface biedt een gestructureerde manier om unieke sleutels te koppelen aan specifieke waarden.

---

## Generieke klasse HashMap

De `HashMap`-klasse maakt gebruik van generieke parameters om flexibel te zijn in het type sleutel en waarde dat wordt opgeslagen.

### Voorbeeld:

```java
HashMap<String, Integer> scores = new HashMap<>();
scores.put("Alice", 25);
scores.put("Bob", 30);
scores.put("Charlie", 28);

int scoreVanAlice = scores.get("Alice");
System.out.println("Score van Alice: " + scoreVanAlice);
```

Hier slaat de `HashMap` namen op als sleutels en scores als waarden.

---

## Veelgebruikte methoden van de Map-interface

1. **`put(K key, V value)`**: Voegt een sleutel-waarde paar toe.
2. **`get(Object key)`**: Haalt de waarde op die gekoppeld is aan een sleutel.
3. **`containsKey(Object key)`**: Controleert of een bepaalde sleutel aanwezig is.
4. **`containsValue(Object value)`**: Controleert of een bepaalde waarde aanwezig is.
5. **`remove(Object key)`**: Verwijdert een sleutel-waarde paar.
6. **`keySet()`**: Retourneert een set van alle sleutels.
7. **`values()`**: Retourneert een verzameling van alle waarden.

---

## Geavanceerd gebruik van HashMap

### Voorbeeld: Opslag van complexe objecten

In plaats van eenvoudige waarden zoals `Integer`, kun je complexe objecten als waarden opslaan.

```java
public class Player {
    private String name;
    private int score;

    public Player(String name, int score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }
}
```

**Gebruik van een HashMap met `Player`-objecten:**

```java
HashMap<String, Player> playerMap = new HashMap<>();
playerMap.put("Alice", new Player("Alice", 100));
playerMap.put("Bob", new Player("Bob", 85));

Player player = playerMap.get("Bob");
System.out.println("Speler " + player.getName() + " heeft een score van " + player.getScore());
```

---

## Conclusie

Hoofdstuk 3 introduceert de `Map`-interface als een krachtig hulpmiddel binnen Java’s Collections Framework. Door gebruik te maken van implementaties zoals `HashMap` kun je eenvoudig sleutel-waarde paren beheren, van eenvoudige types zoals strings tot complexe objecten.

Heb je specifieke vragen over het gebruik van `Map` of voorbeelden nodig? Laat het me weten!