# Architecture du Projet

## 🏗️ Modèle choisi : REST API avec MVC

1. **Controllers**  
   - Gèrent les requêtes HTTP et orchestrent la logique métier.  
   - Communiquent avec les services ou modèles pour récupérer ou modifier les données.

2. **Models**  
   - Représentent les données et interagissent avec la base de données.  
   - Implémentent les validations ou les formats spécifiques nécessaires.

3. **Services**  
   - Contiennent la logique métier principale.  
   - Assurent une séparation claire entre la logique métier et les contrôleurs.

4. **Routes**  
   - Définissent les points d’entrée pour accéder aux fonctionnalités du système.  

---

## 📂 Structure des dossiers

src/ 
    ├── controllers/ 
    ├── models/ 
    ├── routes/ 
    ├── services/ 
    └── utils/

- **controllers/** : Contient les fichiers de contrôleurs.  
- **models/** : Définit les modèles de données (exemple : User, Product).  
- **routes/** : Gère le routage des requêtes (exemple : API REST).  
- **services/** : Contient les services pour encapsuler la logique métier.  
- **utils/** : Fournit des fonctions utilitaires réutilisables.

---

## 📊 Diagramme de l’API

Client ---> Routes ---> Controllers ---> Services ---> Models/DB

Exemple de flux :  
1. Un client envoie une requête `POST /users`.  
2. La route `/users` redirige vers le contrôleur `UserController`.  
3. Le contrôleur appelle un service pour gérer la logique métier.  
4. Le service interagit avec le modèle ou la base de données.  

---

### 🛠️ Principes

- **Modularité** : Chaque composant a une responsabilité unique.  
- **Réutilisabilité** : Le code des services et utilitaires est facilement