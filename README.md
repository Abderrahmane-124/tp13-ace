## Description

Ce projet implémente un service web SOAP pour la gestion de comptes bancaires en utilisant **Spring Boot** et **Apache CXF**.

## Technologies Utilisées

- **Java 20**
- **Spring Boot 3.2.0**
- **Apache CXF 4.0.2** (JAX-WS)
- **Spring Data JPA**
- **H2 Database** (base de données en mémoire)
- **Lombok**

## Structure du Projet

```
src/main/java/com/example/demo/
├── DemoApplication.java          # Classe principale
├── config/
│   └── CxfConfig.java            # Configuration Apache CXF
├── entities/
│   ├── Compte.java               # Entité JPA
│   └── TypeCompte.java           # Enum (COURANT, EPARGNE)
├── repositories/
│   └── CompteRepository.java     # Repository JPA
└── ws/
    └── CompteSoapService.java    # Service SOAP
```

## Exécution

### Avec IntelliJ IDEA

1. Ouvrir le projet dans IntelliJ
2. Attendre l'import des dépendances Maven
3. Exécuter `DemoApplication.java`

### Avec Maven

```bash
mvn spring-boot:run
```

## URLs d'Accès

| Service | URL |
|---------|-----|
| **WSDL** | http://localhost:8082/services/ws?wsdl |
| **Console H2** | http://localhost:8082/h2-console |

### Connexion H2

- **JDBC URL** : `jdbc:h2:mem:testdb`
- **Username** : `sa`
- **Password** : *(vide)*

## Service SOAP - BanqueWS

### Opérations Disponibles

| Méthode | Description |
|---------|-------------|
| `getComptes()` | Récupère tous les comptes |
| `getCompteById(id)` | Récupère un compte par ID |
| `createCompte(solde, type)` | Crée un nouveau compte |
| `deleteCompte(id)` | Supprime un compte |

### Exemples de Requêtes SOAP

#### Créer un compte

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" 
                  xmlns:ws="http://ws.demo.example.com/">
   <soapenv:Header/>
   <soapenv:Body>
      <ws:createCompte>
         <solde>5000.0</solde>
         <type>COURANT</type>
      </ws:createCompte>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Récupérer tous les comptes

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" 
                  xmlns:ws="http://ws.demo.example.com/">
   <soapenv:Header/>
   <soapenv:Body>
      <ws:getComptes/>
   </soapenv:Body>
</soapenv:Envelope>
```

## Captures d'ecran
<img width="1794" height="958" alt="Screenshot 2026-01-02 161149" src="https://github.com/user-attachments/assets/01a4023d-d961-498b-aa04-ccf17623496f" />
<img width="1737" height="540" alt="Screenshot 2026-01-02 161223" src="https://github.com/user-attachments/assets/894b7679-fa83-4c14-92bf-894173a79819" />
<img width="1807" height="547" alt="Screenshot 2026-01-02 161236" src="https://github.com/user-attachments/assets/8c202291-a743-4d56-a012-434d7b09c829" />
<img width="1819" height="627" alt="Screenshot 2026-01-02 161214" src="https://github.com/user-attachments/assets/94848fbf-10ae-4dcb-8279-776ecd9f2a60" />

