# Récap des notions qui me trigger

## Les variables
- Déclaration d'objets à la volée (avec des accolades)
```js
const b = 'Les gens'
const person = {
    firstname: 'Marie',
    lastname: 'Curie',
    age: '31',
    notes: [6, 5, 6, 4],
    [b]: 234,
    job: {
        title: 'informaticienne',
        location: 'morges',
        hours: 42.5
    }
}

console.log(`${b}, ${person.age}`) // cool notation !
```
Lorsque l'on assigne un tableau ou un objet à une autre, JS passe une référence ou un pointeur je sais pas, donc que l'on modifie l'une ou l'autre variable, les deux vont être modifiées. Tandis que si on assigne tout autre type d'objet (string, float...) alors une copie sera faite.

## Les conditions

mot clé `var` : ancien, à ne plus utiliser. Problématique liée à sa portée bien trop grande. `let` est limité au scope des accolades, ce qui empêche de faire n'imp et JS a besoin que l'on ne fasse pas n'imp.

Un truc que je n'ai jamais pensé faire : faire de ma condition, une variable, pour une meilleure lisibilité du code. 
Exemple : 
```js
const	age = 17
const	pays = 'FR'
const	canDriveInEurope = pays === 'FR' && age >= 18
const	canDriveInUSA = pays === 'USA' && age >= 16

if (canDriveInEurope) {
    console.log("You can drive in Europe")
}
else if (canDriveInUSA) {
    console.log("You can drive in the USA")
}
else if (canDriveInEurope || canDriveInUSA) {
    console.log("You can drive")
}
else {
    console.log("You can't drive")
}
```

## Les boucles 

`for of` : Permet de parcourir des éléments itérables, comme les éléments d'un tableau, et nous renverra la valeur
`for in` : Permet d'itérer sur les clés (index) d'un tableau ou d'un objet
```js
const greetings = 'Bonjour'
for (let letter of greetings) { // for in permet d'interroger l'index et on aura comme résultat la lettre stockée en mémoire dans cet index là
    console.log(letter)
}
```

Ptit tips : faire * 1 sur une string la converti en int car js ne peut pas concaténer ou faire autre chose que la multiplication voulue.
Exemple la fonction `prompt()` retourne une string, mais si on demande un numéro il faudra le convertir. `Number()` permet cela également.

## Les fonctions

Trois manière de les écrire : 
1. Avec le mot clé function : function est aussi un type. Cette manière permet d'appeler une fonction avant de l'avoir déclarée. JS stocke en premier les fonctions avant d'exécuter le reste du code.
```js
function upNotes (array) {
    array[0]++
}

//---------------------------------------------------------

const a = {
    firstname: 'Marie',
    lastname: 'Curie',
    fullname: function () {
        // console.log(this) // va imprimer toute l'instance de l'objet
        console.log(`${this.firstname} ${this.lastname}`);
    }
}

a.fullname()

//---------------------------------------------------------

function maFonction () {
    console.log(this)
}

maFonction.call('hello')
``` 
2. Avec le mot clé const : attention à l'ordre ici !
```js
const maFonction = function () {
    console.log("Pas d'inspiration")
}
```
3. Fonction fléchée : permet d'aller plus vite.
Différence de cette notation : comportement de this à l'intérieur. On ne peut pas citer l'objet, l'instance, marchera pas.
```js
const maFonctionFlechee = (p1, p2) => {
    console.log(p1, p2)
}
maFonctionFlechee(1, 2)
```

Il est possible d'écrire une fonction fléchée sur une seule ligne si sa seule instruction est de return : 
```js
const somme = (a, b) => a + b
```

Les callbacks :

N'importe quoi ce langage omg on peut définir une fonction dans l'appel d'une fonction
fn est donc un callback (convention : de l'appeler cb)
```js
const isPair = function (a, fn) {
    if (a % 2 === 0)
        fn()
}

isPair(4, function () {
    console.log('Mon nombre est pair')
})
```


