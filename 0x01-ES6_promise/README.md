#0x01. Promesses ES6
**`Javscript`** **`ES6`**

![meme](./images/meme1.png)

## Ressources
**Lire ou regarder :**

- [Promesse](https://intranet.alxswe.com/rltoken/j_0FTFbkTg42JMcAbNPOVQ)
- [Promesse JavaScript : Une introduction](https://intranet.alxswe.com/rltoken/2Q2LzNFokcUwpA2u3FKG6Q)
- [Attendez](https://intranet.alxswe.com/rltoken/UXb3S2PMBe-SLJ55isMcow)
- [Async](https://intranet.alxswe.com/rltoken/_K0C7pgEjwaIzU9RpwCb8g)
- [Lancer / Essayer](https://intranet.alxswe.com/rltoken/UTjDgvKk5l892Xslh0vqcQ)

## Objectifs d'apprentissage
A la fin de ce projet, vous êtes censé être capable d'expliquer à n'importe qui, sans l'aide de Google :

- Promesses (comment, pourquoi et quoi)
- Comment utiliser les méthodes `then`, `resolve`, `catch`
- Comment utiliser chaque méthode de l'objet Promise
- Lancer / Essayer
- L'opérateur `attendre`
- Comment utiliser une fonction `async`

## Installation
**Installez NodeJS 12.11.x**
(dans votre répertoire personnel):

```bash
curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt installer nodejs -y
```

```
$noeudjs-v
v12.11.1
$npm-v
6.11.3
```

## Installez Jest, Babel et ESLint
dans le répertoire de votre projet :

- Installez Jest en utilisant : `npm install --save-dev jest`
- Installez Babel en utilisant : `npm install --save-dev babel-jest @babel/core @babel/preset-env`
- Installez ESLint en utilisant : `npm install --save-dev eslint`

## Fichiers de configuration
`**package.json**`

```json
{
  "scripts": {
    "lint": "./node_modules/.bin/eslint",
    "check-lint": "lint [0-9]*.js",
    "dev": "npx babel-node",
    "test": "plaisanterie",
    "full-test": "./node_modules/.bin/eslint [0-9]*.js && plaisanterie"
  },
  "dépendances dev": {
    "@babel/core": "^7.6.0",
    "@babel/node": "^7.8.0",
    "@babel/preset-env": "^7.6.0",
    "eslint": "^6.4.0",
    "eslint-config-airbnb-base": "^14.0.0",
    "eslint-plugin-import": "^2.18.2",
    "eslint-plugin-jest": "^22.17.0",
    "blague": "^24.9.0"
  }
}
```

**`babel.config.js`**

```javascript
module.exports = {
  préconfigurations: [
    [
      '@babel/preset-env',
      {
        cibles : {
          nœud : 'actuel',
        },
      },
    ],
  ],
} ;
```

**`utils.js`**
À utiliser lorsque vous accédez à des tâches nécessitant « uploadPhoto » et « createUser ».

```javascript
fonction d'exportation uploadPhoto() {
  retourner Promise.resolve({
    statut : 200,
    corps : 'photo-profil-1',
  });
}


fonction d'exportation createUser() {
  retourner Promise.resolve({
    prénom : 'Guillaume',
    Nom : 'Salva',
  });
}
```

**`.eslintrc.js`**

```javascript
module.exports = {
  env : {
    navigateur : faux,
    es6 : vrai,
    plaisanterie : vrai,
  },
  étend : [
    'base airbnb',
    'plugin:jest/all',
  ],
  globales : {
    Atomique : 'lecture seule',
    SharedArrayBuffer : 'lecture seule',
  },
  parserOptions : {
    ecmaVersion : 2018,
    Type source : 'module',
  },
  plugins : ['plaisanterie'],
  règles: {
    'pas de console' : 'off',
    'pas d'ombre' : 'off',
    'syntaxe sans restriction' : [
      'erreur',
      'DéclarationÉtiquetée',
      'AvecDéclaration',
    ],
  },
  remplacements :[
    {
      fichiers : ['*.js'],
      Fichiers exclus : 'babel.config.js',
    }
  ]
} ;
```

**et…**
N'oubliez pas d'exécuter $ `npm install` lorsque vous avez le `package.json`

**Format des données de réponse**

`uploadPhoto` renvoie une réponse au format

```json
{
  statut : 200,
  corps : 'photo-profil-1',
}
```

`createUser` renvoie une réponse au format

```json
{
  prénom : 'Guillaume',
  Nom : 'Salva',
}
```

## Tâches

### 0. Tenez toutes les promesses que vous faites et ne faites que celles que vous pouvez tenir

Renvoyez une promesse en utilisant ce prototype `function getResponseFromAPI()`

```
bob@dylan :~$ cat 0-main.js
importer getResponseFromAPI depuis "./0-promise.js" ;

const réponse = getResponseFromAPI();
console.log (instance de réponse de Promise);

bob@dylan :~$
bob@dylan :~$ npm run dev 0-main.js
vrai
bob@dylan :~$
```

solution - [0-promise.js](./0-promise.js)

### 1. Ne faites pas de promesse... si vous savez que vous ne pouvez pas la tenir

En utilisant le prototype ci-dessous, renvoyez une « promesse ». Le paramètre est un « booléen ».

```javascript
getFullResponseFromAPI (succès)
```

Lorsque l'argument est :

- 'vrai'
    - résoudre la promesse en passant un objet avec 2 attributs :
        - `statut` : `200`
        - `corps` : ``Succès'`
- 'faux'
    - rejeter la promesse avec un objet d'erreur avec le message "La fausse API ne fonctionne pas actuellement"


Essayez de le tester par vous-même

```
bob@dylan :~$ cat 1-main.js
importer getFullResponseFromAPI depuis './1-promise' ;

console.log(getFullResponseFromAPI(true));
console.log(getFullResponseFromAPI(false));

bob@dylan :~$
bob@dylan :~$ npm run dev 1-main.js
Promesse { statut : 200, corps : 'Succès' } }
Promesse {
  <rejeté> Erreur : la fausse API ne fonctionne pas actuellement
    ...
    ...
bob@dylan :~$
```

solution - [1-promise.js](./1-promise.js)

### 2. Attrape-moi si tu peux !

Utilisation du prototype de fonction ci-dessous

```javascript
fonction handleResponseFromAPI (promesse)
```

Ajoutez trois gestionnaires à la fonction :

- Lorsque la promesse est résolue, renvoyez un objet avec les attributs suivants
    - `statut` : `200`
    - `corps` : `succès`
- Lorsque la promesse est rejetée, renvoie un objet `Erreur` vide
- Pour chaque résolution, enregistrez « Vous avez reçu une réponse de l'API » sur la console

```
bob@dylan :~$ cat 2-main.js
importer handleResponseFromAPI depuis "./2-then" ;

const promesse = Promise.resolve();
handleResponseFromAPI(promesse);

bob@dylan :~$
bob@dylan :~$ npm run dev 2-main.js
J'ai reçu une réponse de l'API
bob@dylan :~$
```

solution - [2-then.js](./2-then.js)

### 3. Gérez plusieurs promesses réussies

Dans ce fichier, importez `uploadPhoto` et `createUser` depuis `utils.js`

Sachant que les fonctions de `utils.js` renvoient des promesses, utilisez le prototype ci-dessous pour résoudre collectivement toutes les promesses et enregistrer `body firstName lastName` dans la console.

```javascript
fonction handleProfileSignup()
```

En cas d'erreur, enregistrez « Système d'inscription hors ligne » sur la console

```
bob@dylan :~$ cat 3-main.js
importer handleProfileSignup depuis "./3-all" ;

handleProfileSignup();

bob@dylan :~$
bob@dylan :~$ npm run dev 3-main.js
photo-profil-1 Guillaume Salva
bob@dylan :~$
```

solution - [3-all.js](./3-all.js)

### 4. Promesse simple

En utilisant le prototype suivant

```javascript
fonction signUpUser (prénom, nom) {
}
```

Cela renvoie une promesse résolue avec cet objet :

```json
{
  prénom : valeur,
  nom : valeur,
}
```

```
bob@dylan :~$ cat 4-main.js
importer signUpUser depuis "./4-user-promise" ;

console.log(signUpUser("Bob", "Dylan"));

bob@dylan :~$
bob@dylan :~$ npm run dev 4-main.js
Promesse { { prénom : 'Bob', nom : 'Dylan' } }
bob@dylan :~$
```

solution - [4-user-promise.js](./4-user-promise.js)

### 5. Rejetez les promesses

Écrivez et exportez une fonction nommée `uploadPhoto`. Il doit accepter un argument `fileName` (chaîne).

La fonction doit renvoyer une promesse de rejet avec une erreur et la chaîne « $fileName ne peut pas être traité »

```javascript
fonction d'exportation par défaut uploadPhoto(nom de fichier) {

}
```

```
bob@dylan :~$ cat 5-main.js
importer uploadPhoto depuis './5-photo-reject' ;

console.log(uploadPhoto('guillaume.jpg'));

bob@dylan :~$
bob@dylan :~$ npm run dev 5-main.js
Promesse {
  <rejeté> Erreur : guillaume.jpg ne peut pas être traité
  ..
    ..
bob@dylan :~$
```

solution - [5-photo-reject.js](./5-photo-reject.js)

### 6. Gérer plusieurs promesses

Importez `signUpUser` depuis `4-user-promise.js` et `uploadPhoto` depuis `5-photo-reject.js`.

Écrivez et exportez une fonction nommée `handleProfileSignup`. Il doit accepter trois arguments `firstName` (chaîne), `lastName` (chaîne) et `fileName` (chaîne). La fonction doit appeler les deux autres fonctions. Lorsque toutes les promesses sont réglées, il doit renvoyer un tableau avec la structure suivante :

```json
[
    {
      statut : statut_of_the_promise,
      value : valeur ou erreur renvoyée par la promesse
    },
    ...
  ]
```

```
bob@dylan :~$ cat 6-main.js
importer handleProfileSignup depuis './6-final-user' ;

console.log(handleProfileSignup("Bob", "Dylan", "bob_dylan.jpg"));

bob@dylan :~$
bob@dylan :~$ npm run dev 6-main.js
Promesse { <en attente> }
bob@dylan :~$
```

solution - [6-final-user.js](./6-final-user.js)

### 7. Équilibreur de charge

Écrivez et exportez une fonction nommée « loadBalancer ». Il doit accepter deux arguments `chinaDownload` (Promesse) et `USdownload` (Promesse).

La fonction doit renvoyer la valeur renvoyée par la promesse qui a résolu la première.

```javascript
exporter la fonction par défaut loadBalancer(chinaDownload, USDownload) {

}
```

```
bob@dylan :~$ cat 7-main.js
importer LoadBalancer depuis "./7-load_balancer" ;

const ukSuccess = 'Le téléchargement depuis le Royaume-Uni est plus rapide';
const frSuccess = 'Le téléchargement depuis FR est plus rapide';

const promiseUK = new Promise (fonction (résolution, rejet) {
    setTimeout(resolve, 100, ukSuccess);
});

const promiseUKSlow = new Promise (fonction (résolution, rejet) {
    setTimeout(resolve, 400, ukSuccess);
});

const promiseFR = new Promise(function(resolve, rejet) {
    setTimeout(resolve, 200, frSuccess);
});

const test = async () => {
    console.log (attendre loadBalancer (promiseUK, promiseFR));
    console.log (attendre loadBalancer (promiseUKSlow, promiseFR));
}

test();

bob@dylan :~$
bob@dylan :~$ npm run dev 7-main.js
Le téléchargement depuis le Royaume-Uni est plus rapide
Le téléchargement depuis FR est plus rapide
bob@dylan :~$
```

solution - [7-load_balancer.js](./7-load_balancer.js)

### 8. Lancer une erreur / essayer de attraper

Écrivez une fonction nommée « DivideFunction » qui acceptera deux arguments : « numérateur » (Nombre) et « dénominateur » (Nombre).

Lorsque l'argument « dénominateur » est égal à 0, la fonction doit générer une nouvelle erreur avec le message ne peut pas « diviser par 0 ». Sinon, il doit renvoyer le numérateur divisé par le dénominateur.

```javascript
exporter la fonction par défaut DivideFunction (numérateur, dénominateur) {

}
```

```
bob@dylan :~$ cat 8-main.js
importer DivideFunction depuis './8-try' ;

console.log(divideFunction(10, 2));
console.log(divideFunction(10, 0));

bob@dylan :~$
bob@dylan :~$ npm run dev 8-main.js
5
..../8-try.js:15
  throw Error('ne peut pas diviser par 0');
  ^
.....

bob@dylan :~$
```

solution - [8-try.js](./8-try.js)

### 9. Générez une erreur

Écrivez une fonction nommée `guardrail` qui acceptera un argument `mathFunction` (Function).

Cette fonction doit créer et renvoyer un tableau nommé « file d'attente ».

Lorsque la fonction `mathFunction` est exécutée, la valeur renvoyée par la fonction doit être ajoutée à la file d'attente. Si cette fonction renvoie une erreur, le message d'erreur doit être ajouté à la file d'attente. Dans tous les cas, le message « Le garde-corps a été traité » doit être ajouté à la file d'attente.

Exemple:

```json
[
  1000,
  'Le garde-corps a été traité',
]
```

```
bob@dylan :~$ cat 9-main.js
importer le garde-corps depuis './9-try' ;
importer DivideFunction depuis './8-try' ;

console.log(guardrail(() => { return DivideFunction(10, 2)}));
console.log(guardrail(() => { return DivideFunction(10, 0)}));

bob@dylan :~$
bob@dylan :~$ npm run dev 9-main.js
[ 5, 'Le garde-corps a été traité' ]
[ 'Erreur : impossible de diviser par 0', 'Le garde-corps a été traité' ]
bob@dylan :~$
```

### 10. Attendre / Asynchrone
#avancé
Importez `uploadPhoto` et `createUser` depuis `utils.js`

Écrivez une fonction asynchrone nommée `asyncUploadUser` qui appellera ces deux fonctions et renverra un objet au format suivant :

```json
{
  photo : réponse_from_uploadPhoto_function,
  utilisateur : réponse_from_createUser_function,
}
```

Si l'une des fonctions asynchrones échoue, renvoyez un objet vide. Exemple:

```
{
  photo : nulle,
  utilisateur : nul,
}
```

```
bob@dylan :~$ cat 100-main.js
importer asyncUploadUser depuis "./100-await" ;

const test = async () => {
    valeur const = attendre asyncUploadUser();
    console.log(valeur);
} ;

test();

bob@dylan :~$
bob@dylan :~$ npm run dev 100-main.js
{
  photo : {statut : 200, corps : 'photo-profile-1' },
  utilisateur : { prénom : 'Guillaume', nom : 'Salva' }
}
bob@dylan :~$
```

solution - [100-await.js](./100-await.js)
