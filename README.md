# TP 13 - Web Service SOAP avec JAX-WS et Spring Boot

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

## Test avec SoapUI

1. Télécharger [SoapUI](https://www.soapui.org/downloads/soapui/)
2. Créer un nouveau projet SOAP
3. Importer le WSDL : `http://localhost:8082/services/ws?wsdl`
4. Tester les différentes opérations

## Auteur

TP réalisé dans le cadre du cours **Architecture Composants d'Entreprise** - 5IIR
