# <<<<<<<<<<<PARTIE 1 :Initiation>>>>>>>>>>>



------------INTRO-----------

Le point d'entrée de l'application reste le fichier "index.html" (ce qui va être affiché à l'écran).
Par défault quand on utilise Angular, dans le fichier index.html il y a la balise <app-root>"ici s'affichera toute la page Angular"</app-root>
Composant racine qui sera le parent de tous les composants.


Un composant est définit par 3 fichiers.
    
     Composant.component.css
     Composant.component.html // Définit la structure et la présentation du composant.
     Composant.composant.ts
   

Pour créer un composant :
Dans la console "ng generate component nomDuComposant".

Le fichier app.module.ts est la structure centralisée pour définir les composants, modules et services.
Dans ce fichier on déclate les composants dans la section "déclarations".
On fait l'import des modules externes.

### ///////J'ai pas bien compris à quoi sert le "RouterModule".




## ------------Partie 1.1-----------


. Dans l'exemple, il y a 3 composants :
     - app.component
     - app.top-bar.component (enfant de app.component)
     - app.product-list.component (enfant de app.component)

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
<app-product-alerts
  [product]="product">
</app-product-alerts>
me permet de créer une instance du composant dans le template du composant parent.
La liaison de propriété me permet de transmettre la valeur de la propriété du composant parent au composant enfant.

(notify)="onNotify()" : Liaison d'évènement pour écouter un évènement émis par un composant parent.

