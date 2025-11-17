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

