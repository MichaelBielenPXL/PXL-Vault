### **Databases**

### **PostgreSQL**

- `PGUSER`: Gebruikersnaam voor databaseauthenticatie.
- `PGPASSWORD`: Wachtwoord voor de gebruiker.
- `PGDATABASE`: Naam van de database.
- `PGHOST`: Hostnaam of IP-adres van de database (bijv. `localhost` of `postgres` in Docker).
- `PGPORT`: Poort waarop PostgreSQL luistert (standaard `5432`).

**Voorbeeld (Docker Compose):**

yaml

Copy

```
environment:
  POSTGRES_USER: admin
  POSTGRES_PASSWORD: mysecretpassword
  POSTGRES_DB: mydb
```

---

### **MySQL/MariaDB**

- `MYSQL_ROOT_PASSWORD`: Wachtwoord voor de root-gebruiker.
- `MYSQL_DATABASE`: Standaarddatabase die wordt aangemaakt.
- `MYSQL_USER`: Gebruiker voor de database.
- `MYSQL_PASSWORD`: Wachtwoord voor de gebruiker.
- `MYSQL_HOST`: Host van de database (standaard `localhost`).

---

### **MongoDB**

- `MONGO_INITDB_ROOT_USERNAME`: Root-gebruikersnaam.
- `MONGO_INITDB_ROOT_PASSWORD`: Root-wachtwoord.
- `MONGO_INITDB_DATABASE`: Standaarddatabase.
- `MONGO_HOST`: Host voor connecties (bijv. `mongo` in Docker-netwerken).

---

### **Web Servers & Proxies**

### **Nginx**

- `NGINX_PORT`: Poort waarop Nginx draait (standaard `80`).
- `NGINX_HOST`: Hostnaam (bijv. `example.com`).
- `NGINX_ENVSUBST_TEMPLATE_DIR`: Pad naar templates voor environment variable substitutie.

---

### **Apache HTTP Server**

- `APACHE_PORT`: Poort (standaard `80`).
- `APACHE_DOCUMENT_ROOT`: Pad naar de webroot (bijv. `/var/www/html`).

---

### **Programmeertalen & Frameworks**

### **Node.js**

- `NODE_ENV`: Omgeving (`development`, `production`, `test`).
- `PORT`: Poort waar de applicatie op draait (bijv. `3000`).
- `DATABASE_URL`: Database connection string (bijv. `postgres://user:pass@host:port/db`).

---

### **Python (Django)**

- `SECRET_KEY`: Geheime sleutel voor security (verplicht in Django).
- `DEBUG`: Debug-modus (`True` of `False`).
- `ALLOWED_HOSTS`: Komma-gescheiden lijst van toegestane hosts (bijv. `localhost,example.com`).
- `DATABASE_URL`: Database URL (gebruikt met `dj-database-url`).

---

### **Java (Spring Boot)**

- `SPRING_DATASOURCE_URL`: JDBC URL voor de database.
- `SPRING_DATASOURCE_USERNAME`: Databasegebruiker.
- `SPRING_DATASOURCE_PASSWORD`: Databasewachtwoord.
- `SERVER_PORT`: Applicatiepoort (standaard `8080`).

---

### **Cloud Providers**

### **AWS**

- `AWS_ACCESS_KEY_ID`: Access key voor API-authenticatie.
- `AWS_SECRET_ACCESS_KEY`: Secret key voor API-authenticatie.
- `AWS_REGION`: Regio (bijv. `eu-west-1`).
- `AWS_S3_BUCKET`: Naam van een S3-bucket.

---

### **Google Cloud (GCP)**

- `GOOGLE_APPLICATION_CREDENTIALS`: Pad naar service account JSON-bestand.
- `GCLOUD_PROJECT`: ID van het GCP-project.

---

### **Containerisatie & Orchestratie**

### **Docker**

- `DOCKER_HOST`: URL van de Docker-daemon (bijv. `tcp://docker:2375`).
- `DOCKER_REGISTRY`: URL van een containerregistry (bijv. `docker.io`).

---

### **Kubernetes**

- `KUBECONFIG`: Pad naar het kubeconfig-bestand.
- `KUBERNETES_SERVICE_HOST`: Host van de Kubernetes API-server (automatisch ingesteld in pods).

---

### **CI/CD Tools**

### **GitHub Actions**

- `GITHUB_TOKEN`: Token voor authenticatie met GitHub APIs.
- `GITHUB_REPOSITORY`: Naam van de repository (bijv. `gebruiker/mijn-repo`).

---

### **GitLab CI**

- `CI_PROJECT_DIR`: Pad naar de projectdirectory.
- `CI_REGISTRY_USER`: Gebruiker voor de GitLab Container Registry.
- `CI_REGISTRY_PASSWORD`: Wachtwoord voor de registry.

---

### **Message Brokers & Caching**

### **Redis**

- `REDIS_PASSWORD`: Wachtwoord voor authenticatie.
- `REDIS_HOST`: Hostnaam (bijv. `redis` in Docker-netwerken).
- `REDIS_PORT`: Poort (standaard `6379`).

---

### **RabbitMQ**

- `RABBITMQ_DEFAULT_USER`: Standaardgebruiker.
- `RABBITMQ_DEFAULT_PASS`: Standaardwachtwoord.
- `RABBITMQ_HOST`: Hostnaam (bijv. `rabbitmq` in Docker).

---

### **Monitoring & Logging**

### **Elasticsearch**

- `ELASTICSEARCH_HOST`: Host (bijv. `elasticsearch`).
- `ELASTICSEARCH_PORT`: Poort (standaard `9200`).

---

### **Prometheus**

- `PROMETHEUS_PORT`: Poort voor metrics (standaard `9090`).
- `PROMETHEUS_CONFIG_FILE`: Pad naar configuratiebestand.