# Boutique Diayma versionning by Omar DIOP

## 2 - Explorez l’application : signalez 2 bugs trouvés

Après avoir exploré l'application, voici les **deux bugs principaux** identifiés :
### **1️⃣ Le stock du produit**
J'ai remarqué apres la validation du commande le stock du produit reste inchangé

### **2️⃣ La langue espagnol**
La langue espagnol ne marche pas 


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
