# Gestion des cliques

Il ne nous reste plus qu'une dernière étape: quand on clique sur un chat, qu'il disparaisse et incrémente de score.

## Création de la fonction dans App.js

On va d'abord créer un nouveau state qu'on nommera `hit`

```js
state = {
	score: 0,
	cat: 0,
	hit: 0,
}
```



Ensuite, en dessous du state, on va créer une nouvelle fonction `hit` avec un argument `clicked`

```js
hit = (clicked) => {
	
}
```



Et on va faire passer la fonction dans le component `Board` en tant que props

```
<Board click={this.hit} cat={this.state.cat}/>
```



[Chapitre Bonus =>](10-bonus.md)