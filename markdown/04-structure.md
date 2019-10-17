# La structure de base 

Lors de la création d'une application React, la structure de l'application ressemble à comme ci-dessous:

![Structure de l'application](./img/arborescence/arborescence1.png)

## Le dossier public

Le dossier public contien tous les fichiers qui seront placés à la racine du dossier lors de la compilation d'une application React.

![dossier public](./img/arborescence/arborescence-public.png)

Il n'y a qu'un élément important dans le dossier public:

* **Le fichier index.html** est l'unique page internet qui existera dans notre application React, c'est lui qui chargera et affichera notre application React. Il contiens également les éléments de base de tout page html comme le title, meta, favicon et l'import des scripts. C'est donc ici que vous pourrez changer le titre et la description et la favicon de votre application ou autre balises meta et il ne servira qu'à ça.

![public index](./img/arborescence/arborescence-index.png)

## Le dossier src

C'est ici que contiendra tout le coeur de notre application, il n'y a que quelques fichiers importants à prendre en compte:

![dossier src](./img/arborescence/arborescence-src.png)

* **Le fichier index.js** est celui qui s'occupera du rendu de notre application. On y touchera que très peu lors de notre workshop et on y retouchera plus jamais.

![src index](./img/arborescence/arborescence-src1.png)

* **Le fichier app.js** est celui qui accueillera le contenu de notre page, c'est ici qu'on construira notre application.

![src app](./img/arborescence/arborescence-src2.png)

## Nettoyage des fichiers inutiles

Tous les autres fichiers que je n'ai pas cités au dessus sont inutiles pour la création de notre application, je vais quand même vous fournir quelques explications sur ces fichiers:

* Le fichier **manifest.json** n'est pas nécessaire dans notre projet mais il est utilisé lorsque la page est enregistré dans l'écran d'accueil d'un smartphone ou d'un ordinateur, il contiendra le nom de l'application, les différents formats d'icône, la couleurs de fonds etc...

* Le fichier **robot.txt** sert pour le protocole d'exclusion des *web crawlers* (les robots d'exploration)

* Le fichier **serviceWorker.js** est un script qui est exécuté en tâche de fond et qui permet de gérer des notifications push, la synchronisation de arrière-plan, d'intercepter des requêtes réseau et gérer le cache, ce qui est complètement inutile dans notre cas.
*  Le fichier **App.test.js** est utilisé lorsqu'on lance des test dans un environnement isolé, un sujet qui n'est pas du tout abordé dans ce test et qui n'est pas nécessaire dans le fonctionnement d'une application React
* Les fichiers **CSS** ne sont utilisés que pour la mise en page de la page d'introduction généré lors de la création de l'application. Je vous fournirais un CSS déjà créé donc ces fichiers ne sont absolument pas nécessaire
* Les images et logo dans chaque dossier ne sont plus utiles non plus .


![Arborescence de l'application après nettoyage](./img/arborescence/nettoyage.png)

---

# Nettoyage de index.js et App.js

Notez que après nettoyage des fichiers inutiles, notre application sera cassé, il faudra donc supprimer quelques lignes de codes dans `App.js` et `index.js` pour que notre application fonctionne ne nouveau. On va également supprimer les lignes inutiles généré par la création de l'application.

## index.js

![base index](./img/nettoyage/depart-indexjs.png)

Dans ce fichier on supprimera l'importation du fichier CSS et tout ce qui concerne le serviceWorker.js, il ne restera donc plus que 4 lignes de code dans l'index.js

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

## App.js

![base app](./img/nettoyage/depart-appjs.png)

On a supprimé le svg et css , donc on peut supprimer la ligne qui importe ces fichiers à la ligne 2 et 3.

On peut aussi tout ce que contiens la div avec la classe `App`. Vous pouvez aussi ajouter un petit élément `<h1>` pour tester si le rendu fonctionne bien.

Pour que vous compreniez mieux comment le `state`  fonctionne, on va transformer notre fonction en classe et modifier notre importation de React à la première ligne, étant donné que le rendu fonctionne différement dans une classe, il faudra aussi ajouter un `Render(){}` avant le return.

Voici le résultat finale pour notre app.js

```js
import React, {Component} from 'react';

class App extends Component {
  render(){
    return (
      <div className="App">
        <h1>Application React</h1>
      </div>
    );
  }
}

export default App;

```

---

## Ajout des fichiers nécessaire à notre workshop

Vous trouverez dans la branche `fichiers` du dépot de notre workshop un fichier du style CSS et des images dont vous aurez besoin.

Téléchargez le contenu de ce dépot au format ".ZIP", prenez le dossier `static` et déposez-le dans le dossier `src` de votre projet.

Vous devrez ensuite importer notre nouveau fichier CSS en ajoutant une ligne au début du fichier `app.js`

```js
import "./static/style.css";
```

Comme ceci : 

![final appjs](./img/nettoyage/final-appjs.png)

[=> Chapitre suivant](05-component.md)