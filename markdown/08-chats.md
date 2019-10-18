# Apparition des chats

On va maintenant faire apparaitre nos chats de manière aléatoire. Dans `app.js`, on va ajouter un nouveau state qu'on appellera cat:

```js
state={
	score: 0,
	cat: 0,
}
```

## Génération du chiffre aléatoire

Ensuite on va ajouter une nouvelle fonction qu'on appellera `changeActiveCat` au dessus de la fonction render.

``` 
changeActiveCat = () => {

}
```

A l'intérieur de cette fonction, on va en un premier temps générer un chiffre aléatoire entre 1 et 9 et on appliquera dans un setState.

```js
chageActiveCat = () => {
	let newNbr
	
	newNbr = Math.floor(Math.random()*9+1)
    
    this.setState({cat: newNbr})
}
```

Le problème ici, c'est qu'il y aura des moments où il générera un même chiffre et le chat pourrait rester sur la même case plus longtemps que prévu, on va donc ajouter un petit `do while`  si le nombre généré est égale à la state

```js
chageActiveCat = () => {
	let newNbr
	
	do{
		newNbr = Math.floor(Math.random()*9+1)
	} while (newNbr === this.state.cat)
    
    this.setState({cat: newNbr})
}
```

Pourquoi `do while` et pas juste `while` vous allez demander? La différence, contrairement à un simple `while`, c'est qu'il va vérifier la condition  à la fin de la boucle au lieu du début.

## Répétition de la fonction

C'est bien qu'on fasse générer un chiffre aléatoire mais il va le faire qu'une fois. Il faudra donc que cette fonction se répète.



On va donc créer une autre fonction au-dessus de la fonction qu'on a créé qu'on appellera `startGame`, et on va mettre à l'intérieur un `setInterval` à 1000ms pour qu'il répète la fonction toutes les secondes.



```js
startGame = () => {
	setInterval(this.changeActiveCat, 1000)
}
```



Il faut ensuite que cette fonction soit enclenchée quand on clique sur le bouton démarrer, on va donc remplacer la fonction passée en prop dans notre component Button

```js
<Button text='Start game!' click={this.startGame.bind(this)}/>
```

## Faire apparaitre les chats

Bon, c'est bien que notre `App.js` génère un chiffre toutes les secondes, mais il ne se passe encore rien visuellement.

Étant donnée que c'est le component `Board` qui gère l'apparition des chats, il faudra passer notre `state.cat ` dans notre board en tant que props.

```
<Board cat={this.state.cat}/>
```



Mais comment ça va se passer pour faire apparaitre les chats? Dans le fichier CSS qu'on vous a fourni, il y a une classe `.visible` qui fait apparaitre les chats. Donc le principe de notre code qui suivra ci-dessous c'est que si le numéro du chat correspond au numéro du trou, il appliquera la classe `.visible`.



Sur `Board.js`, sur la `<div>` qui porte la classe `mole`:

```js
<div className={`mole ${(this.props.mole === nbr) && 'visible'}`}></div>
```

Vous allez sans doute vous sentir perdu sur la façon dont on a écrit

`(this.props.mole === nbr) && 'visible'` veut dire *'si `props.mole` est égale au numéro du trou, alors tu ajoutes "visible"'*



Si tout se passe bien, vous verrez les chats apparaitre aléatoirement dans différents trous.

[Chapitre Bonus =>](09-Bonus.md)