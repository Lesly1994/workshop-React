# State

## Création du state

Le state est une variable de type objet on l'on crée les différents éléments qu'on souhaite et qu'on pourra mettre à jour.

_Le state se traduit par un état local. Il est similaire aux props sauf qu'il est privé et est entièrement contrôlée par le composant qui l'a créé. Il permet de stocker des données, de contrôler le rendu du composant et comment il se comporte. Un élément du state est accessible de la même manière d'un props: `this.state.monEtat`_

Dans `App.js`, à l'intérieur de notre classe au dessus du render, on va créer notre state avec un élément score.

```js
class App extends Component {
	// Initialisation des states
  	state = {
    	score: 0,
	}

	// render(){
		// [...]
	// }
}
```
---

## setState()

Quand on veut changer un élément contenu dans state, il faudra utiliser la fonction `setState()`, car si on le modifie directement par `this.state.`, React ne refera pas le rendu de la page avec la nouvelle valeur.



De nouveau dans `App.js`, on va créer une fonction qui va incrémenter notre score:

```js
class App extends Component {
	// state = {
	//	score: 0,
	// }

	incrementScore(){
		this.setState({score: this.state.score + 1})
	}

	// render(){
		//[...]
	// }
}
```

Notez cependant que setState() est une fonction asynchrone, c'est à dire que vous n'aurez pas forcément la nouvelle valeur si vous lisez une state directement après un setState()

## Passer la fonction au boutton

Pour rappel, notre `button` est dans un component `Button.js`. On ne pourra pas tout simplement faire un `onClick=incrementScore()` car notre fonction se situe dans `App.js`.

On va donc passer notre fonction dans un prop du `Button`

Dans l'appel du component "Button" dans `App.js`:

```js
<Button text='Start game!' click={this.incrementScore.bind(this)}/>
```

Le `.bind(this)` permet à notre fonction de fonctionner, si on ne met pas ce bind, le script plantera en disant qu'une  valeur est undefined *(avec bind tous les arguments sont automatiquement transmis)*.

Dans `Button.js`, on va tout simplement ajouter notre onClick dans notre bouton:

```js
<button onClick={props.click}>{props.title}</button>
```

Dans notre onClick, on mettra tout simplement `props.click` puisque notre fonction est passé dans un prop qu'on a nommé `click`.

Maintenant, dans le fichier `App.js` il vous faudra rajouter une ligne :

```js
<Button text='Start game!' click={this.incrementScore.bind(this)}/>
<p>Score: {this.state.score}</p>
```

Vous verrez ainsi notre score monter à chaque fois que vous cliquez sur le bouton.

Magique non ?!

![magique](https://media.giphy.com/media/QIiqoufLNmWo8/giphy.gif)

[chapitre suivant =>](07-board.md)