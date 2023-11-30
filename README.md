# <<<<<<<<<<<PARTIE 1: Initiation>>>>>>>>>>>



## ------------Partie 1.1-----------


. Dans l'exemple, il y a 3 composants :
```ts
     - app.component
     - app.top-bar.component (enfant de app.component)
     - app.product-list.component (enfant de app.component)
```
. Un fichier product.ts qui contient la liste des produits avec le détail. (pour simuler les données API)

 

Dans le fichier html du composant "product-list":

On utilise la directive structurelle "*ngFor" qui permet de faire une boucle sur une liste d'éléments. Dans cet exemple, elle itère sur la liste de produits et affiche chaque produit dans une balise.


{{}} : syntaxe d'interpolation, permet d'insérer des valeurs de propriété de composant dans le template.
La valeur {{ product.name }} correspond à la propriété de la class "Product" dans le fichier "product.ts"

[title]="product.name + ' details'" : syntaxe de liaison de propriété, utilisé pour afficher du texte lorqu'un élément est suvollé par la souris.

La directive structurelle "*ngIf" : permet de faire une condition pour l'affichage d'éléments.
Dans l'exemple elle est utilisée dans la boucle qui parcours les produits, si un élément n'a pas de description alors rien ne sera affiché.

Le bouton "Share" est relié à la fonction Share() qui se trouve dans le fichier "product-list.component.ts", elle permet d'ouvrir une fenêtre d'affichage.





## ------------Partie 1.2-----------

Création d'un composant enfant "ProductAlertsComponent" qui peut recevoir les données de son composant parent "ProductListComponent".
Automatiquement un décorateur s'est créé dans la page html du composant. Le décorateur fournit des données.
Le selector qui identifie le composant par convention il commence toujours par app., le template et le style.
Un décorateur permet de changer les méthodes, les propriétés, les fonctionnalités de base...

### /////// c'est encore un peu flou pour moi l'utilisation des décorateurs.


-Transmettre des données entre composants-

@Input(): décorateur Angular qui indique que la propriété annotée est une proprité d'entrée du composant. Cette propriété peut être assignée ou passée au composant depuis son composant parent. Cette fonctionnalité permet une communication entre les composants, où le composant parent peut transmettre des données au composant enfant en utilisant cette propriété d'entrée.

@Ouput(): décorateur utilisé pour définir une propriété de sortie d'un composant. Elle peut émettre des évènements personnalisés que d'autres composants peuvent écouter.

Dans le fichier product-list.component.html(composant parent):
```
<app-product-alerts
  [product]="product">
</app-product-alerts>
```
me permet de créer une instance du composant dans le template du composant parent.
La liaison de propriété me permet de transmettre la valeur de la propriété du composant parent au composant enfant.

(notify)="onNotify()" : Liaison d'évènement pour écouter un évènement émis par un composant parent.



# <<<<<<<<<<<PARTIE 2: Routing>>>>>>>>>>>

[routerLink]="['/products', product.id]" directive qui aide à personnaliser l'élément d'ancrage. Ca me permet de changer de page dans mon composant.


Les composants ont des cycles de vie. Le cycle de vie comprend plusieurs méthodes qui sont appelées à des moments spécifiques de ce cycle.

ngOnInit() : cette méthode est appelée après que le composant ait été inisialisé. C'est généralement l'endroit où on effectue les tâches d'inisialisation tel que la récupération de données. 
Lorsqu'une class implémente "OnInit", elle doit fournir une implémentation de la méthode. Cela signifie que la class est informée lorqu'elle est créée et peut effectuer des tâches d'initialisations.
La méthode OnInit me permet de récupérer les productID, elle recherche le produit correspondant dans le tableau.

ActivatedRoute à ajouter en argument du constructeur, il est spécifique à chaque composant chargé par Angular. On configure le composant pour utiliser un service.
Dans Angular, un service est une instance d'une class qu'on peut mettre à disposition de n'importe qu'elle partie de l'appli à l'aide du système des dépendances.

### //// Si j'ai bien compris, le ActivedRoute (dans le cas du tuto) sert à aller récupérer des données mais j'ai pas bien compris le fonctionnement.



# <<<<<<<<<<<PARTIE 3: Data>>>>>>>>>>>

-Création d'un service panier dans le tuto-

Pour créer un service dans la console "ng generate servie nomDuService"

Le décorateur @Injectable est utilisé pour indiquer qu'une class peut être injectée avec dépendances.
Le paramètre 'providedIn: 'root' pour indiquer que le service sera injecté au niveau du module racine, ce qui le rend accessible partout dans l'application.

```ts
items: Product[] = [];
```
On déclare une propriété 'items' d'un tableau vide de type 'Product'. Ca va nous permettre de stoker les produits dans le panier.
routerLink="/cart" pour les liens de navigation. L'utilisateur click sur le lien, ça entraine l'affichage d'un composant spécifique. (cart)

| currency : directive intégrée Angular qui permet de formater les valeurs numériques. Souvent utilisée pour afficher des montants d'argent de manière plus lisible.

Le dossier 'assets' dans un projet Angular est utilisé pour stocker des fichiers statiques, par exemple des images, des fichiers de style CSS, de configurations ou autre ressources.



# <<<<<<<<<<<PARTIE 4: Formulaire>>>>>>>>>>>


Dans le tuto on va créer un formulaire dans le composant du panier pour que l'utilisateur rentre son nom, adresse et un bouton submit.

Il faut d'abord faire l'import de FormBuilder dans le fichier ts du panier. 
Ensuite il faut ajouter le service formBuilder en paramètre du contructeur du panier.
FormBuilder.group() est la méthode pour définir la propriété sur un modèle de formulaire "nom", "adresse".
Le méthode onSubmit() permet aux utilisateurs de soumettre leur nom et adresse.

Pour créer un imput : 
```ts
<input id="name" type="text" formControlName="name">
```




# Mes observations

Le point d'entrée de l'application reste le fichier "index.html" (ce qui va être affiché à l'écran).
Par défault quand on utilise Angular, dans le fichier index.html il y a la balise 
```ts
<app-root>"ici s'affichera toute la page Angular"</app-root>
```
Composant racine qui sera le parent de tous les composants.

Un composant est définit par 3 fichiers.
    
    * Composant.component.css
    * Composant.component.html // Définit la structure et la présentation du composant.
    * Composant.composant.ts
   

Pour créer un composant :
Dans la console "ng generate component nomDuComposant".

Le fichier app.module.ts est la structure centralisée pour définir les composants, modules et services.
Dans ce fichier on déclare les composants dans la section "déclarations".
On fait l'import des modules externes.
Un projet Angular est composé de plusieurs composants qui intéragissent entre eux.
La méthode onInit() me permet de changer de page et donc de composant.
On peut aussi passer d'un composant à l'autre par un bouton avec un lien de navigation. 
A quoi sert le "RouterModule"?



J'ai pas bien compris comment utiliser HttpClient, ça sert à faire des requête vers une API. Est ce que ça remplace la méthode fetch ?
J'utilise un import HttpClient dans le service du panier, pourquoi est ce que je suis obligée de le mettre dans le fichier app.module.ts?
Pourquoi est ce que les import des nouveaux composants se font automatiquement dans le fichier 'module.ts' mais il faut ajouter à la main les 'path'?

# Mon ressenti

J'aime le coté d'utilisation de composant dans Angular. Ca permet de créer des pages dynamiques. J'attends de voir avec un projet où on part de zéro pour voir si ça facilite l'utilisation. Car hormis le côté composant je trouve que ça fait faire beaucoup d'imports.



![Texte alternatif](./src/assets/confettis.gif)
# Fin
