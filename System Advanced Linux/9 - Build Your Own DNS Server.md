# Build Your Own DNS Server

## Wat is een DNS-server?

Een **DNS-server** (Domain Name System) vertaalt menselijke leesbare domeinnamen (bijvoorbeeld `www.example.com`) naar IP-adressen (bijvoorbeeld `192.168.1.1`) die computers kunnen begrijpen. Dit systeem is essentieel voor internetcommunicatie en maakt browsen, e-mail en andere netwerkservices mogelijk.

### Twee soorten DNS-servers:

1. **Recursive DNS Resolver:**
    
    - Stelt vast waar het DNS-record zich bevindt.
    - Verwerkt DNS-query's namens de gebruiker.
2. **Authoritative DNS Server:**
    
    - Bevat de daadwerkelijke DNS-records voor domeinen.
    - Geeft het definitieve antwoord op een DNS-query.

---

## Waarom je eigen DNS-server bouwen?

### Voordelen:

1. **Controle over DNS:**
    
    - Je kunt je eigen records beheren en configureren.
    - Vermijd afhankelijkheid van externe DNS-providers.
2. **Prestatieverbetering:**
    
    - Door caching kun je snellere query-antwoorden leveren.
3. **Beveiliging:**
    
    - Bescherm je netwerk tegen DNS-gevaar zoals spoofing.
4. **Opleidingsdoeleinden:**
    
    - Begrijp hoe DNS werkt door het vanaf de basis te implementeren.

---

## Installeren van een DNS-server

### Stap 1: Vereisten

1. **Besturingssysteem:**
    
    - Linux-distributies zoals Ubuntu of CentOS worden aanbevolen.
2. **Software:**
    
    - `Bind9` is een van de meest gebruikte DNS-serverpakketten.

### Stap 2: Installeren van Bind9

Voor Ubuntu:

```bash
sudo apt update
sudo apt install bind9 bind9utils bind9-doc
```

Controleer of Bind9 draait:

```bash
sudo systemctl status bind9
```

---

## Configureren van een DNS-server

### Stap 1: Configuratiebestanden vinden

De belangrijkste configuratiebestanden van Bind9 bevinden zich meestal in `/etc/bind/`.

- **`named.conf.options`**:
    - Bevat algemene configuraties, zoals forwarding en caching.
- **`named.conf.local`**:
    - Hier definieer je zones voor domeinen.
- **Zonebestanden**:
    - Bevatten specifieke DNS-records.

### Stap 2: Configuratie aanpassen

#### `named.conf.options` aanpassen:

```bash
sudo nano /etc/bind/named.conf.options
```

Voeg de volgende regels toe of wijzig deze:

```plaintext
options {
    directory "/var/cache/bind";

    forwarders {
        8.8.8.8; // Google DNS
        8.8.4.4; // Google DNS
    };

    dnssec-validation auto;

    listen-on { any; };
    allow-query { any; };
};
```

#### Zone toevoegen in `named.conf.local`:

```bash
sudo nano /etc/bind/named.conf.local
```

Voeg een zone toe:

```plaintext
zone "example.com" {
    type master;
    file "/etc/bind/zones/db.example.com";
};
```

### Stap 3: Zonebestand maken

Maak een map voor je zonebestanden:

```bash
sudo mkdir /etc/bind/zones
```

Maak het zonebestand:

```bash
sudo nano /etc/bind/zones/db.example.com
```

Voorbeeld van een zonebestand:

```plaintext
;
; Zone file for example.com
;
$TTL    604800
@       IN      SOA     ns1.example.com. admin.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.example.com.
@       IN      A       192.168.1.100
ns1     IN      A       192.168.1.100
www     IN      A       192.168.1.101
mail    IN      A       192.168.1.102
```

### Stap 4: Controleer de configuratie

Controleer of de configuratie correct is:

```bash
sudo named-checkconf
sudo named-checkzone example.com /etc/bind/zones/db.example.com
```

### Stap 5: Herstart de DNS-server

Herstart Bind9 om de wijzigingen toe te passen:

```bash
sudo systemctl restart bind9
```

---

## Testen van je DNS-server

### Test lokaal

Gebruik `dig` of `nslookup` om je DNS-server te testen:

**Met dig:**

```bash
dig @localhost example.com
```

**Met nslookup:**

```bash
nslookup example.com localhost
```

### Test vanaf een andere machine

Configureer een clientmachine om jouw DNS-server te gebruiken:

- Voeg het IP-adres van de DNS-server toe als primaire DNS-server in de netwerkconfiguratie.

---

## Veelvoorkomende problemen en oplossingen

### 1. DNS-server start niet

- Controleer de logs:
    
    ```bash
    sudo journalctl -u bind9
    ```
    
- Controleer configuratiefouten:
    
    ```bash
    sudo named-checkconf
    sudo named-checkzone example.com /etc/bind/zones/db.example.com
    ```
    

### 2. Geen verbinding met de DNS-server

- Zorg ervoor dat poort 53 openstaat in de firewall:
    
    ```bash
    sudo ufw allow 53
    ```
    
- Controleer of Bind9 luistert:
    
    ```bash
    sudo netstat -plntu | grep named
    ```
    

---

## Beveiliging van je DNS-server

1. **Beperk toegang:**
    
    - Sta alleen specifieke IP-adressen toe om queries uit te voeren:
        
        ```plaintext
        allow-query { 192.168.1.0/24; localhost; };
        ```
        
2. **Implementeer DNSSEC:**
    
    - DNSSEC beschermt tegen DNS-spoofing door digitale handtekeningen toe te voegen aan DNS-records.
3. **Gebruik logbestanden:**
    
    - Schakel logging in om verdachte activiteiten te detecteren.
4. **Houd de software up-to-date:**
    
    - Installeer regelmatig updates om beveiligingslekken te dichten.

---

## Conclusie

Het bouwen van je eigen DNS-server biedt controle, snelheid en veiligheid. Met Bind9 kun je een krachtige en aanpasbare DNS-oplossing implementeren. Door je configuratie te optimaliseren en beveiligingsmaatregelen te nemen, kun je een betrouwbare DNS-server creëren die voldoet aan je specifieke behoeften.