
| `POO` | `JavaScript` | 'ES6' |

## Ressources
**Lire ou regarder :**

- [Cours](https://intranet.alxswe.com/rltoken/ke2dSL31JbpAUBW0qWE9WA)
- [Métaprogrammation](https://intranet.alxswe.com/rltoken/6OgF5QGbYclp_cwATfq-0g)


## Objectifs d'apprentissage
A la fin de ce projet, vous êtes censé être capable d'expliquer à n'importe qui, sans l'aide de Google :

- Comment définir une classe
- Comment ajouter des méthodes à une classe
- Pourquoi et comment ajouter une méthode statique à une classe
- Comment prolonger une classe d'une autre
- Métaprogrammation et symboles

## Exigences
**Général**

- Tous vos fichiers seront exécutés sur Ubuntu 18.04 LTS en utilisant NodeJS 12.11.x
- Éditeurs autorisés : `vi`, `vim`, `emacs`, `Visual Studio Code`
- Tous vos fichiers doivent se terminer par une nouvelle ligne
- Un fichier `README.md`, à la racine du dossier du projet, est obligatoire
- Votre code doit utiliser l'extension js
- Votre code sera testé à l'aide du [`Jest Testing Framework`](https://intranet.alxswe.com/rltoken/ECZpKsJ3fm1qRA7lDyhd_Q)
- Votre code sera analysé à l'aide du linter [`ESLint`](https://intranet.alxswe.com/rltoken/Ttd9w5jERwTErJW3DDbVoQ) ainsi que des règles spécifiques que nous vous fournirons
- Toutes vos fonctions doivent être exportées

## Installation
**Installez NodeJS 12.11.x**
(dans votre répertoire personnel):

```
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

```
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

```
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

**`.eslintrc.js`**

```
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

## Enfin…
N'oubliez pas d'exécuter `npm install` depuis le terminal de votre dossier de projet pour installer toutes les dépendances nécessaires du projet.

## Tâches
### 0. Vous aviez l'habitude de fréquenter un endroit comme celui-ci à un moment donné

Implémentez une classe nommée `ClassRoom` :

- Prototype : `exporter la classe par défaut ClassRoom`
- Il doit accepter un attribut nommé `maxStudentsSize` (Nombre) et attribué à `_maxStudentsSize`

```
bob@dylan :~$ cat 0-main.js
importer ClassRoom depuis "./0-classroom.js" ;

const room = new ClassRoom(10);
console.log(room._maxStudentsSize)

bob@dylan :~$
bob@dylan :~$ npm run dev 0-main.js
dix
bob@dylan :~$
```

solution - [0-classroom.js](./0-classroom.js)

### 1. Créons quelques salles de classe

Importez la classe `ClassRoom` depuis `0-classroom.js`.

Implémentez une fonction nommée `initializeRooms`. Il doit renvoyer un tableau de 3 objets `ClassRoom` avec les tailles 19, 20 et 34 (dans cet ordre).

```
bob@dylan :~$ cat 1-main.js
importer initializeRooms depuis './1-make_classrooms.js' ;

console.log(initializeRooms());

bob@dylan :~$
bob@dylan :~$ npm run dev 1-main.js
[
  Salle de classe { _maxStudentsSize : 19 },
  Salle de classe { _maxStudentsSize : 20 },
  Salle de classe { _maxStudentsSize : 34 }
]
bob@dylan :~$
```

solution - [1-make_classrooms.js](./1-make_classrooms.js)

### 2. Un cours, des getters et des setters

Implémentez une classe nommée « HolbertonCourse » :

- Attributs du constructeur :
  - `nom` (Chaîne)
  - `longueur` (Nombre)
  - `étudiants` (tableau de chaînes)

- Assurez-vous de vérifier le type d'attributs lors de la création de l'objet

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Implémenter un getter et un setter pour chaque attribut.

```
bob@dylan :~$ cat 2-main.js
importer HolbertonCourse depuis "./2-hbtn_course.js" ;

const c1 = nouveau Cours Holberton("ES6", 1, ["Bob", "Jane"])
console.log(c1.name);
c1.nom = "Python 101" ;
console.log(c1);

essayer {
    c1.nom = 12 ;
}
attraper (erreur) {
    console.log(err);
}

essayer {
    const c2 = new HolbertonCourse("ES6", "1", ["Bob", "Jane"]);
}
attraper (erreur) {
    console.log(err);
}

bob@dylan :~$
bob@dylan :~$ npm run dev 2-main.js
ES6
Cours Holberton {
  _nom : 'Python 101',
  _longueur : 1,
  _étudiants : [ 'Bob', 'Jane' ]
}
TypeError : le nom doit être une chaîne
    ...
TypeError : la longueur doit être un nombre
    ...
bob@dylan :~$
```

solution - [2-hbtn_course.js](./2-hbtn_course.js)

### 3. Méthodes, méthodes statiques, noms de méthodes calculées..... ARGENT

Implémentez une classe nommée `Currency` :

- -Attributs du constructeur :
  - `code` (Chaîne)
  - `nom` (Chaîne)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)
- Implémenter un getter et un setter pour chaque attribut.
- Implémentez une méthode nommée `displayFullCurrency` qui renverra les attributs au format suivant `name (code)`.

```
bob@dylan :~$ cat 3-main.js
importer la devise depuis "./3-currency.js" ;

const dollar = nouvelle devise('$', 'Dollars');
console.log(dollar.displayFullCurrency());

bob@dylan :~$
bob@dylan :~$ npm run dev 3-main.js
Dollars ($)
bob@dylan :~$
```

### 4. Tarifs

Importez la classe `Currency` depuis `3-currency.js`

Implémentez une classe nommée `Pricing` :

- Attributs du constructeur :
  - `montant` (Nombre)
  - `monnaie` (Devise)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Implémenter un getter et un setter pour chaque attribut.

- Implémentez une méthode nommée `displayFullPrice` qui renvoie les attributs au format suivant `amount monnaie_name (currency_code)`.

- Implémentez une méthode statique nommée `convertPrice`. Il doit accepter deux arguments : `amount` (Nombre), `conversionRate` (Nombre). La fonction doit renvoyer le montant multiplié par le taux de conversion.

```
bob@dylan :~$ cat 4-main.js
importer les prix depuis './4-pricing.js' ;
importer la devise depuis './3-currency.js' ;

const p = nouveau prix (100, nouvelle devise ("EUR", "Euro"))
console.log(p);
console.log(p.displayFullPrice());

bob@dylan :~$
bob@dylan :~$ npm run dev 4-main.js
Tarif {
  _montant : 100,
  _currency : Devise { _code : 'EUR', _name : 'Euro' }
}
100 euros (EUR)
bob@dylan :~$
```

solution - [4-pricing.js](./4-pricing.js)

### 5. Un bâtiment

Implémentez une classe nommée `Building` :

- Attributs du constructeur :
  - `sqft` (Nombre)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Implémentez un getter pour chaque attribut.

- Considérez cette classe comme une classe abstraite. Et assurez-vous que toute classe qui en découle doit implémenter une méthode nommée « evacuationWarningMessage ».
  - Si une classe qui s'étend à partir de celle-ci n'a pas de méthode `evacuationWarningMessage`, renvoie une erreur avec le message `La classe étendant le bâtiment doit remplacer `evacuationWarningMessage`

```
bob@dylan :~$ cat 5-main.js
importer le bâtiment depuis './5-building.js' ;

const b = nouveau bâtiment (100) ;
console.log(b);

la classe TestBuilding étend le bâtiment {}

essayer {
    nouveau bâtiment de test (200)
}
attraper (erreur) {
    console.log(err);
}

bob@dylan :~$
bob@dylan :~$ npm run dev 5-main.js
Bâtiment { _sqft : 100 }
Erreur : la classe étendant le bâtiment doit remplacer l'évacuationWarningMessage
    ...
bob@dylan :~$
```

solution - [5-building.js](./5-building.js)

### 6. Héritage

Importez « Building » depuis « 5-building.js ».

Implémentez une classe nommée « SkyHighBuilding » qui s'étend de « Building » :

- Attributs du constructeur :
  - `sqft` (Number) (doit être attribué à la classe parent Building)
  - `étages` (Nombre)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Implémentez un getter pour chaque attribut.

- Remplacez la méthode nommée evacuationWarningMessage et renvoyez la chaîne suivante « Évacuez lentement les NUMBER_OF_FLOORS étages ».

```
bob@dylan :~$ cat 6-main.js
importer SkyHighBuilding depuis './6-sky_high.js' ;

bâtiment const = nouveau SkyHighBuilding (140, 60);
console.log (bâtiment. sqft);
console.log(bâtiment.étages);
console.log(building.evacuationWarningMessage());

bob@dylan :~$
bob@dylan :~$ npm run dev 6-main.js
140
60
Évacuer lentement les 60 étages
bob@dylan :~$
```

solution - [6-sky_high.js](./6-sky_high.js)

### 7. Aéroport

Implémentez une classe nommée `Airport` :

- Attributs du constructeur :
  - `nom` (Chaîne)
  - `code` (Chaîne)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- La chaîne de description par défaut de la classe doit renvoyer le « code » de l'aéroport (exemple ci-dessous).

```
bob@dylan :~$ cat 7-main.js
importer l'aéroport depuis "./7-airport.js" ;

const aéroportSF = nouvel aéroport('Aéroport de San Francisco', 'SFO');
console.log(aéroportSF);
console.log(airportSF.toString());

bob@dylan :~$
bob@dylan :~$ npm run dev 7-main.js
Aéroport [SFO] { _name : 'Aéroport de San Francisco', _code : 'SFO' }
[objet OFS]
bob@dylan :~$
```

solution - [7-airport.js](./7-airport.js)

### 8. Primitif - Classe Holberton

Implémentez une classe nommée HolbertonClass :

- Attributs du constructeur :
  - `taille` (Nombre)
  - `emplacement` (Chaîne)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Lorsque la classe est convertie en « Nombre », elle doit renvoyer la taille.

- Lorsque la classe est convertie en `String`, elle doit renvoyer l'emplacement.

```
bob@dylan :~$ cat 8-main.js
importer HolbertonClass depuis "./8-hbtn_class.js" ;

const hc = new HolbertonClass(12, "Mezzanine")
console.log(Nombre(hc));
console.log(String(hc));

bob@dylan :~$
bob@dylan :~$ npm run dev 8-main.js
12
Mezzanine
bob@dylan :~$
```

solution - [8-hbtn_class.js](./8-hbtn_class.js)

### 9. Levage

Corrigez ce code et faites-le fonctionner.

```
const class2019 = new HolbertonClass(2019, 'San Francisco');
const class2020 = new HolbertonClass(2020, 'San Francisco');

classe d'exportation HolbertonClass {
  constructeur (année, localisation) {
    this._year = année ;
    this._location = emplacement ;
  }

  obtenir l'année() {
    retourner this._year;
  }

  obtenir l'emplacement() {
    renvoie this._location ;
  }
}

const student1 = new StudentHolberton('Guillaume', 'Salva', class2020);
const student2 = new StudentHolberton('John', 'Doe', class2020);
const student3 = new StudentHolberton('Albert', 'Clinton', classe2019);
const student4 = new StudentHolberton('Donald', 'Bush', class2019);
const student5 = new StudentHolberton('Jason', 'Sandler', class2019);

classe d'exportation StudentHolberton {
  constructeur (prénom, nom) {
    this._firstName = prénom;
    this._lastName = nom de famille ;
    this._holbertonClass = holbertonClass;
  }

  obtenir fullName() {
    return `${this._firstName} ${this._lastName}` ;
  }

  obtenir HolbertonClass() {
    renvoie this.holbertonClass ;
  }

  obtenir fullStudentDescription() {
    return `${self._firstName} ${self._lastName} - ${self._holbertonClass.year} - ${self._holbertonClass.location}` ;
  }
}


export const listOfStudents = [étudiant1, étudiant2, étudiant3, étudiant4, étudiant5];
```

Résultat:

```
bob@dylan :~$ cat 9-main.js
importer listOfStudents depuis "./9-hoisting.js" ;

console.log(listOfStudents);

const listPrinted = listOfStudents.map(
    étudiant => étudiant.fullStudentDescription
);

console.log(listPrinted)

bob@dylan :~$
bob@dylan :~$ npm run dev 9-main.js
[
  ÉtudiantHolberton {
    _prénom : 'Guillaume',
    _lastName : 'Salva',
    _holbertonClass : HolbertonClass { _année : 2020, _emplacement : 'San Francisco' }
  },
  ÉtudiantHolberton {
    _firstName : 'Jean',
    _lastName : 'Biche',
    _holbertonClass : HolbertonClass { _année : 2020, _emplacement : 'San Francisco' }
  },
  ÉtudiantHolberton {
    _prénom : 'Albert',
    _nom de famille : 'Clinton',
    _holbertonClass : HolbertonClass { _année : 2019, _emplacement : 'San Francisco' }
  },
  ÉtudiantHolberton {
    _firstName : 'Donald',
    _lastName : 'Bush',
    _holbertonClass : HolbertonClass { _année : 2019, _emplacement : 'San Francisco' }
  },
  ÉtudiantHolberton {
    _firstName : 'Jason',
    _lastName : 'Sandler',
    _holbertonClass : HolbertonClass { _année : 2019, _emplacement : 'San Francisco' }
  }
]
[
  'Guillaume Salva - 2020 - San Francisco',
  "John Doe - 2020 - San Francisco",
  "Albert Clinton - 2019 - San Francisco",
  "Donald Bush - 2019 - San Francisco",
  "Jason Sandler - 2019 - San Francisco"
]
bob@dylan :~$
```

solution - [9-hoisting.js](./9-hoisting.js)

### 10. Vroom

Implémentez une classe nommée `Car` :

- Attributs du constructeur :
  - `marque` (Chaîne)
  - `moteur` (Chaîne)
  - `couleur` (Chaîne)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`

- Ajoutez une méthode nommée `cloneCar`. Cette méthode doit renvoyer un nouvel objet de la classe.

Astuce : symboles dans ES6

```
bob@dylan :~$ cat 10-main.js
importer une voiture depuis "./10-car.js" ;

la classe TestCar étend Car {}

const tc1 = new TestCar("Nissan", "Turbo", "Rose");
const tc2 = tc1.cloneCar();

console.log(tc1);
console.log (instance tc1 de TestCar);

console.log(tc2);
console.log (instance tc2 de TestCar);

console.log(tc1 == tc2);

bob@dylan :~$
bob@dylan :~$ npm run dev 10-main.js
TestCar { _marque : 'Nissan', _moteur : 'Turbo', _couleur : 'Rose' }
vrai
TestCar { _brand : non défini, _moteur : non défini, _color : non défini }
vrai
FAUX
bob@dylan :~$
```

```
bob@dylan :~$ cat 10-main.js
importer une voiture depuis "./10-car.js" ;

la classe TestCar étend Car {}

const tc1 = new TestCar("Nissan", "Turbo", "Rose");
const tc2 = tc1.cloneCar();

console.log(tc1);
console.log (instance tc1 de TestCar);

console.log(tc2);
console.log (instance tc2 de TestCar);

console.log(tc1 == tc2);

bob@dylan :~$
bob@dylan :~$ npm run dev 10-main.js
TestCar { _marque : 'Nissan', _moteur : 'Turbo', _couleur : 'Rose' }
vrai
TestCar { _brand : non défini, _moteur : non défini, _color : non défini }
vrai
FAUX
bob@dylan :~$
```

solution - [10-car.js](./10-car.js)

### 11. Voiture électrique

Importez « Car » depuis « 10-car.js ».

Implémentez une classe nommée « EVCar » qui étend la classe « Car » :

- Attributs du constructeur :
  - `marque` (Chaîne)
  - `moteur` (Chaîne)
  - `couleur` (Chaîne)
  - `plage` (Chaîne)

- Chaque attribut doit être stocké dans une version d'attribut « underscore » (ex : `name` est stocké dans `_name`)

- Pour des raisons de confidentialité, lorsque `cloneCar` est appelé sur un objet EVCar, l'objet renvoyé doit être une instance de `Car` au lieu de `EVCar`.

```
bob@dylan :~$ cat 100-main.js
importer EVCar depuis './100-evcar.js' ;

const ec1 = new EVCar("Tesla", "Turbo", "Rouge", "250");
console.log(ec1);

const ec2 = ec1.cloneCar();
console.log(ec2);

bob@dylan :~$
bob@dylan :~$ npm run dev 100-main.js
EVVoiture {
  _marque : 'Tesla',
  _moteur : 'Turbo',
  _La couleur rouge',
  _plage : '250'
}
Voiture { _brand : non défini, _moteur : non défini, _color : non défini }
bob@dylan :~$
```

solution - [100-evcar.js](./100-evcar.js)
