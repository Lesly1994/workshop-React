# Gestion des cliques

Il ne nous reste plus qu'une dernière étape: quand on clique sur un chat, il disparait et incrémente de score.

## Création de la fonction dans App.js

On va d'abord créer un nouveau state qu'on nommera `hit`, il permettra d'afficher une croix si on a bien cliqué sur un chat.

```js
state = {
	score: 0,
	cat: 0,
	hit: 0,
}
```

Ensuite, en-dessous du state, on va créer une nouvelle fonction `hit` avec un argument `clicked`.

```js
hit = (clicked) => {
	
}
```

Et on va faire passer la fonction dans le component `Board` en tant que props.

```js
<Board click={this.hit} cat={this.state.cat}/>
```

## Appeler la fonction depuis Board.js

Comme quand on a fait pour le bouton, on va ajouter un `onClick` sur la div `board-item`, sauf que ici il sera écrit de manière différente étant donné qu'on va faire passer un argument

```js
<div key={nbr} onClick={() => this.props.click(nbr)} className='board-item'>
```

On a du faire un callback pour pouvoir passer le numéro du trou en tant que paramètre.

## Complèter notre fonction dans App.js

Donc, pour rappel, au moment où on clique sur un trou, le numéro du trou cliqué sera passé en paramètre à notre fonction `hit()` qui sera en tant que `clicked`

On voudra alors comparer si le numéro du trou cliqué correspond au numéro où le chat est apparu.

Si tel est le cas, on incrémente le score, on remet le state `cat` à 0 pour qu'il disparaisse et on met le `hit` au numéro du trou cliqué pour faire apparaitre la croix (qui constituera notre prochaine étape).

On remettra `hit` à 0 après 250ms

```
hit = (clicked) => {
	if (this.state.cat === clicked){
		this.setState({
			score: this.state.score + 1,
			cat: 0,
			hit: clicked,
		})
	}
	
	setTimeout( () => this.setState({hit:0}), 250)
}
```


[Chapitre Bonus =>](10-bonus.md)