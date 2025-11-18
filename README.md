# Boutique Diayma versionning by Omar DIOP

## 2 - Explorez l’application : signalez 2 bugs trouvés

Après avoir exploré l'application, voici les **deux bugs principaux** identifiés :

### **1️⃣ Mauvaise gestion des exceptions**

Dans plusieurs fonctionnalités, l’application essaie d’afficher des listes **sans gérer le cas où celles-ci seraient nulles**.
C’est notamment le cas pour :

* **La liste des paniers (Carts)** via la méthode `FindProductInCartLines()`
* **La liste des produits**, avec l’expression :

  ```csharp
  First(p => p.Id == productId)
  ```

Si l’élément recherché n’existe pas, cela provoque une **exception non gérée** (ex. `InvalidOperationException`).
L’application devrait utiliser `FirstOrDefault()` ou le `?` et vérifier la nullité avant d’accéder aux données.

---

### **2️⃣ Erreur dans le calcul du total du panier**

La fonction censée calculer le total du panier (`GetTotalValue()`) contient une erreur.
Elle fait la somme des prix **sans prendre en compte correctement la quantité**, notamment lorsque celle-ci est supérieure à 1.

Exemple incorrect trouvé :

```csharp
Sum(x => x.Product.Price * x.Quantity)
```

Le calcul doit être revu pour garantir un total correct en fonction des quantités.

Voici la **version corrigée, claire et professionnelle**, adaptée à un fichier **README.md** :

---

## 5. Quels sont les namespaces, classes et méthodes visités avant l’affichage des produits sur l’écran d’accueil de votre navigateur, en mode “Pas à pas détaillé” ?

En mode *Pas à pas détaillé*, voici les éléments parcourus avant l’affichage de la page des produits :

1. **Namespace : `P2FixAnAppDotNetCode`**

   * **Classe : `Startup`**
   * **Méthode : `Startup()`** (appel au constructeur de configuration)

   C’est le premier point d’entrée chargé par l’application lors de l’initialisation.

2. **Namespace : `P2FixAnAppDotNetCode.Controllers`**

   * **Classe : `ProductController`**
   * **Constructeur : `ProductController(IProductService productService)`**

   Visual Studio entre dans ce contrôleur pour préparer les dépendances nécessaires, notamment `_productService`.

3. **Namespace : `P2FixAnAppDotNetCode.Components`**

   * **Classe : `CartSummaryViewComponent`**
   * **Méthode : `CartSummaryViewComponent()`** (constructeur)

   Ce composant est appelé lors du rendu de la page d’accueil afin d’afficher le résumé du panier.
