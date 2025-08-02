# TrustFlow Platform

**TrustFlow** è una piattaforma completa per la gestione documentale digitale, firma elettronica e conservazione a norma, progettata con architettura a microservizi per garantire scalabilità, affidabilità e conformità normativa.

## 🏗️ Architettura

La piattaforma è composta da 8 microservizi specializzati:

### Servizi Core
- **🔐 Auth Service** (`trustflow-auth-service`) - Autenticazione e autorizzazione
- **📄 Doc Service** (`trustflow-doc-service`) - Gestione documenti e metadati
- **✍️ Sign Service** (`trustflow-sign-service`) - Firma elettronica e digitale
- **🗄️ Store Service** (`trustflow-store-service`) - Conservazione digitale e storage

### Servizi di Supporto
- **🔄 Flow Service** (`trustflow-flow-service`) - Gestione workflow e processi
- **👥 User Service** (`trustflow-user-service`) - Gestione utenti e profili
- **📊 Audit Service** (`trustflow-audit-service`) - Audit trail e compliance
- **🔧 Common** (`trustflow-common`) - Libreria condivisa

## 🚀 Caratteristiche Principali

### Gestione Documentale
- ✅ Upload e gestione documenti multi-formato
- ✅ Versioning automatico e controllo delle modifiche
- ✅ Categorizzazione gerarchica e tagging
- ✅ Ricerca full-text avanzata
- ✅ Condivisione sicura con controllo accessi
- ✅ Metadati personalizzabili

### Firma Elettronica
- ✅ Firma elettronica semplice e avanzata
- ✅ Firma digitale qualificata
- ✅ Supporto per certificati X.509
- ✅ Timestamping e marcature temporali
- ✅ Verifica automatica delle firme

### Conservazione Digitale
- ✅ Conservazione a norma (AgID)
- ✅ Integrità e autenticità garantite
- ✅ Backup automatici e ridondanza
- ✅ Retention policy configurabili
- ✅ Audit trail completo

### Workflow e Processi
- ✅ Designer workflow drag-and-drop
- ✅ Approvazioni multi-livello
- ✅ Notifiche automatiche
- ✅ Escalation e timeout
- ✅ Integrazione con sistemi esterni

## 🛠️ Stack Tecnologico

### Backend
- **Java 11** - Linguaggio di programmazione
- **Spring Boot 2.7.8** - Framework applicativo
- **Spring Cloud** - Microservizi e service discovery
- **Spring Security** - Sicurezza e autenticazione
- **PostgreSQL** - Database relazionale
- **Apache Kafka** - Message broker
- **MinIO** - Object storage
- **Flyway** - Database migration

### Infrastruttura
- **Docker** - Containerizzazione
- **Kubernetes** - Orchestrazione (opzionale)
- **Eureka** - Service discovery
- **Prometheus** - Monitoring
- **ELK Stack** - Logging centralizzato

## 📋 Prerequisiti

- **Java 11+**
- **Maven 3.6+**
- **Docker & Docker Compose**
- **PostgreSQL 13+**
- **Apache Kafka 2.8+**
- **MinIO** (per storage)

## 🚀 Quick Start

### 1. Clone del Repository
```bash
git clone https://github.com/luca-pappa/trustflow-platform.git
cd trustflow-platform
```

### 2. Avvio Infrastruttura
```bash
# Avvia PostgreSQL, Kafka, MinIO, Eureka
docker-compose up -d infrastructure
```

### 3. Build dei Servizi
```bash
# Build di tutti i servizi
mvn clean install

# Oppure build singolo servizio
cd trustflow-doc-service
mvn clean install
```

### 4. Avvio Servizi
```bash
# Avvia tutti i servizi
docker-compose up -d

# Oppure avvio manuale
java -jar trustflow-auth-service/target/trustflow-auth-service-0.0.1-SNAPSHOT.jar
java -jar trustflow-doc-service/target/trustflow-doc-service-0.0.1-SNAPSHOT.jar
# ... altri servizi
```

### 5. Verifica
- **Eureka Dashboard**: http://localhost:8761
- **API Gateway**: http://localhost:8080
- **Swagger UI**: http://localhost:8080/swagger-ui.html

## 📚 Documentazione Servizi

| Servizio | Porta | Descrizione | Documentazione |
|----------|-------|-------------|----------------|
| Auth Service | 8081 | Autenticazione OAuth2/JWT | [README](trustflow-auth-service/README.md) |
| Doc Service | 8082 | Gestione documenti | [README](trustflow-doc-service/README.md) |
| Sign Service | 8083 | Firma elettronica | [README](trustflow-sign-service/README.md) |
| Audit Service | 8084 | Audit e compliance | [README](trustflow-audit-service/README.md) |
| Flow Service | 8085 | Workflow management | [README](trustflow-flow-service/README.md) |
| Store Service | 8086 | Conservazione digitale | [README](trustflow-store-service/README.md) |
| User Service | 8087 | Gestione utenti | [README](trustflow-user-service/README.md) |

### 📖 Documentazione Completa

- **📋 [Documentazione Generale](docs/README.md)** - Guida completa alla piattaforma
- **🏗️ [Diagrammi Architetturali](diagrams/README.md)** - Diagrammi di sistema e flussi
- **🔧 [Guide di Deployment](docs/deployment/)** - Istruzioni per il deployment
- **🧪 [Guide di Testing](docs/testing/)** - Strategie e procedure di test
- **🔒 [Sicurezza e Compliance](docs/security/)** - Documentazione sicurezza
- **📊 [Monitoring e Observability](docs/monitoring/)** - Metriche e monitoraggio

## 🔧 Configurazione

### Variabili d'Ambiente
```bash
# Database
DB_USERNAME=trustflow
DB_PASSWORD=trustflow123

# Kafka
KAFKA_BOOTSTRAP_SERVERS=localhost:9092

# MinIO
MINIO_ENDPOINT=http://localhost:9000
MINIO_ACCESS_KEY=minioadmin
MINIO_SECRET_KEY=minioadmin

# JWT
JWT_ISSUER_URI=http://localhost:8080/auth/realms/trustflow

# Eureka
EUREKA_URL=http://localhost:8761/eureka
```

### Profili Spring
- **dev** - Sviluppo locale
- **test** - Testing automatizzato
- **prod** - Produzione

## 🧪 Testing

```bash
# Test di tutti i servizi
mvn test

# Test con coverage
mvn test jacoco:report

# Test di integrazione
mvn verify -P integration-tests
```

## 📊 Monitoring

### Health Checks
- **Actuator**: `/actuator/health` su ogni servizio
- **Prometheus**: `/actuator/prometheus`
- **Metrics**: `/actuator/metrics`

### Logging
- **Formato**: JSON strutturato
- **Livelli**: DEBUG (dev), INFO (prod)
- **Destinazione**: Console + File + ELK

## 🔒 Sicurezza

### Autenticazione
- **OAuth2** con Keycloak
- **JWT** tokens
- **Refresh tokens**
- **Multi-factor authentication**

### Autorizzazione
- **RBAC** (Role-Based Access Control)
- **Permissions** granulari
- **Resource-level security**

### Crittografia
- **TLS 1.3** per comunicazioni
- **AES-256** per dati a riposo
- **RSA-4096** per firme digitali

## 🚀 Deployment

### Docker Compose (Sviluppo)
```bash
docker-compose up -d
```

### Kubernetes (Produzione)
```bash
kubectl apply -f k8s/
```

### CI/CD Pipeline
- **GitHub Actions** / **GitLab CI**
- **Build automatico** su push
- **Test automatizzati**
- **Deploy automatico** su staging/prod

## 📈 Scalabilità

### Horizontal Scaling
- **Stateless services**
- **Load balancing**
- **Auto-scaling** con Kubernetes

### Performance
- **Connection pooling**
- **Caching** con Redis
- **Async processing** con Kafka

## 🤝 Contribuire

1. **Fork** del repository
2. **Crea** un branch feature (`git checkout -b feature/amazing-feature`)
3. **Commit** delle modifiche (`git commit -m 'Add amazing feature'`)
4. **Push** del branch (`git push origin feature/amazing-feature`)
5. **Apri** una Pull Request

### Coding Standards
- **Java Code Style**: Google Java Style Guide
- **Commit Messages**: Conventional Commits
- **Testing**: Minimum 80% coverage
- **Documentation**: Javadoc per API pubbliche

## 📄 Licenza

Questo progetto è rilasciato sotto licenza **MIT**. Vedi il file [LICENSE](LICENSE) per i dettagli.


---

**TrustFlow Platform** - *Sicurezza, Conformità e Innovazione nella Gestione Documentale Digitale*