# University Resto Manager

Description
----------
University Resto Manager est une application de gestion pour un restaurant universitaire : gestion des menus, prises de commandes, utilisateurs (étudiants, personnel), paiements et rapports. Le backend est en C# (.NET) et le frontend en TypeScript avec HTML/CSS.

Badges
------
- CI: ![build](https://img.shields.io/badge/build-pending-lightgrey)
- License: ![license](https://img.shields.io/badge/license-MIT-blue)
(Remplace les badges par ceux de ton CI et licence réels.)

Table des matières
------------------
- [Fonctionnalités](#fonctionnalités)
- [Stack technique](#stack-technique)
- [Architecture](#architecture)
- [Prérequis](#prérequis)
- [Installation et exécution](#installation-et-exécution)
  - [Backend](#backend)
  - [Frontend](#frontend)
- [Configuration](#configuration)
- [Base de données](#base-de-données)
- [Docker (optionnel)](#docker-optionnel)
- [Tests](#tests)
- [Contribuer](#contribuer)
- [Licence](#licence)
- [Contact](#contact)

Fonctionnalités
---------------
- Gestion des utilisateurs (inscription, connexion, rôles)
- Gestion des menus et plats (CRUD)
- Prise et suivi des commandes
- Paiement / facturation (intégration possible avec un fournisseur)
- Tableau de bord et rapports (ventes, consommation)
- API REST pour le frontend/mobile

Stack technique
---------------
- Backend : C# (.NET / ASP.NET Core)
- Frontend : TypeScript (framework à préciser : Angular / React / Vue)
- UI : HTML & CSS
- Base de données : SQL (SQL Server / PostgreSQL / SQLite)
- Outils : dotnet CLI, npm/yarn, EF Core, Docker (optionnel)

Architecture
------------
- API REST (backend C#) exposant les endpoints : Users, Menus, Orders, Payments, Reports.
- Frontend TypeScript consommant l'API.
- Base de données relationnelle pour la persistance.
- Authentification par JWT recommandée pour sécuriser l'API.

Prérequis
---------
- .NET SDK (par ex. 6.0 ou 7.0) — préciser la version utilisée dans le projet
- Node.js + npm ou yarn
- Une base de données SQL (ou SQLite pour le dev)
- (Optionnel) Docker & Docker Compose

Installation et exécution
------------------------

Important : adapte les chemins ci‑dessous au layout réel du dépôt (ex : ./backend, ./server, ./api, ./client, ./frontend).

Backend
1. Aller dans le dossier backend
   - cd backend
2. Restaurer les paquets
   - dotnet restore
3. Construire
   - dotnet build
4. Appliquer les migrations (si EF Core)
   - dotnet ef database update
5. Lancer en local
   - dotnet run --project ./Path/To/YourProject.csproj
6. Exemples d'endpoint
   - GET /api/menus
   - POST /api/orders
   - POST /api/auth/login

Frontend
1. Aller dans le dossier frontend
   - cd frontend
2. Installer les dépendances
   - npm install
   - ou yarn install
3. Lancer en mode développement
   - npm run dev
   - ou npm start
4. Configurer l'URL de l'API via un fichier d'environnement (.env, .env.local, etc.)

Configuration
-------------
Variables d'environnement typiques (exemples) :
- ConnectionStrings__DefaultConnection="Server=...;Database=...;User Id=...;Password=..."
- ASPNETCORE_ENVIRONMENT=Development
- JWT__Secret="une_chaine_secrete"
- API__BaseUrl=http://localhost:5000

Exemple minimal appsettings.json (backend)
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=resto;User Id=sa;Password=Your_password123;"
  },
  "JWT": {
    "Secret": "ChangeThisSecret",
    "Issuer": "UniversityResto",
    "Audience": "UniversityRestoUsers",
    "ExpiresInMinutes": 60
  }
}

Base de données
---------------
- Avec EF Core :
  - Ajouter une migration : dotnet ef migrations add InitialCreate
  - Appliquer la migration : dotnet ef database update
- Sinon, placer les scripts SQL de création dans /db ou /sql et les exécuter manuellement.

Docker (optionnel)
------------------
Exemple d'esquisse docker-compose.yml :

version: '3.8'
services:
  api:
    build: ./backend
    ports:
      - "5000:80"
    environment:
      - ConnectionStrings__DefaultConnection=...

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"

Tests
-----
- Backend : dotnet test ./tests/YourProject.Tests
- Frontend : npm test (selon configuration)

Contribuer
---------
1. Fork le dépôt
2. Créer une branche feature/ma-fonctionnalite
3. Ajouter des commits clairs
4. Ouvrir une Pull Request avec description et tests si possible
5. Respecter le style et les conventions du projet

Licence
-------
Ce projet est livré sous licence MIT — adapte si nécessaire.

Contact
-------
- Auteur : MohamedAzizJnayah
- GitHub : https://github.com/MohamedAzizJnayah

Notes finales
-------------
- Remplace les chemins (backend/frontend), versions .NET/Node et variables par les valeurs réelles du projet.
- Ajoute des captures d'écran du frontend dans /docs ou /assets pour améliorer la documentation.
