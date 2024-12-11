# Clean Code: Meilleures Pratiques

## ✨ Principes de base

1. **Nommez vos variables de manière explicite** :
   - Mauvais : `x`, `y`
   - Bon : `totalPrice`, `userEmail`

2. **Gardez vos fonctions courtes** :
   - Une fonction = Une tâche.
   - Essayez de ne pas dépasser 20 lignes.

3. **Évitez les duplications de code** :
   - Réutilisez des fonctions ou des modules.

4. **Commentez intelligemment** :
   - Expliquez *pourquoi* et non *comment* dans vos commentaires.

5. **Respectez une structure claire** :
   - Ordre logique : importations, variables globales, fonctions, exécution.
   - Organisez vos fichiers par fonctionnalité.

---

## 🌟 Nommage des entités

1. **Variables**

   - Utilisez des noms en camelCase pour les variables et fonctions.
   ```javascript
   let userName = 'John';
   function calculateTax() {}
   ```

2. **Classes**

   - Utilisez PascalCase pour les noms de classes.
   ```javascript
   class ShoppingCart {
     constructor() {}
   }
   ```

3. **Constantes**

   - Utilisez des noms en majuscules avec des underscores.
   ```javascript
   const MAX_USERS = 100;
   ```

---

## 💡 Pratiques pour les fonctions

1. **N'utilisez pas plus de 3 paramètres** :
   - Combinez-les dans un objet si nécessaire.
   ```javascript
   // Mauvais
   function createUser(name, age, email, address) {}

   // Bon
   function createUser({ name, age, email, address }) {}
   ```

2. **Gérez les exceptions** :
   - Utilisez des blocs `try/catch` pour des opérations critiques.
   ```javascript
   try {
     const data = await fetchData();
   } catch (error) {
     console.error('Erreur lors de la récupération des données', error);
   }
   ```

3. **Utilisez des valeurs par défaut** :
   ```javascript
   function greetUser(name = 'Invité') {
     console.log(`Bonjour, ${name}!`);
   }
   ```

---

## 🚀 Optimisation de la lisibilité

1. **Divisez les longues instructions** :
   ```javascript
   // Mauvais
   const result = userList.filter(user => user.isActive).map(user => user.email).join(',');

   // Bon
   const activeUsers = userList.filter(user => user.isActive);
   const emails = activeUsers.map(user => user.email);
   const result = emails.join(',');
   ```

2. **Utilisez des fonctions d'ordre supérieur** (comme `map`, `filter`, `reduce`).
   ```javascript
   const totalPrice = items.reduce((sum, item) => sum + item.price, 0);
   ```

---

## 🌐 Principes SOLID

1. **Single Responsibility Principle (SRP)**
   - Chaque classe ou fonction doit avoir une seule responsabilité.

2. **Open/Closed Principle (OCP)**
   - Le code doit être ouvert aux extensions mais fermé aux modifications.

3. **Liskov Substitution Principle (LSP)**
   - Les classes dérivées doivent pouvoir être utilisées comme leurs classes de base.

4. **Interface Segregation Principle (ISP)**
   - Préférez des interfaces spécifiques aux besoins à des interfaces générales.

5. **Dependency Inversion Principle (DIP)**
   - Les modules de haut niveau ne doivent pas dépendre des modules de bas niveau.

---

## 🎯 Exemples concrets

### Mauvais exemple
```javascript
function calculate(a, b, operation) {
  if (operation === 'add') {
    return a + b;
  } else if (operation === 'subtract') {
    return a - b;
  } else {
    throw new Error('Opération inconnue');
  }
}
```

### Bon exemple
```javascript
const operations = {
  add: (a, b) => a + b,
  subtract: (a, b) => a - b,
};

function calculate(a, b, operation) {
  const func = operations[operation];
  if (!func) throw new Error('Opération inconnue');
  return func(a, b);
}
```