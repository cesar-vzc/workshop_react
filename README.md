## Workshop : Découverte du React.js

### Installation et lancement

*Prérequis : Installer node.js et npm sur votre environnement de travail.*

*Windows : https://nodejs.org/en/*

*Linux : https://lesbricodeurs.fr/articles/Comment-installer-npm-proprement/*



La première étape du workshop est de cloner le repo est de lancer l’application React.js :

1. git clone https://github.com/cesar-vzc/workshop_react.git

2. cd workshop_react/web-app

3. npm start



### Créer la page d'accueil

Supprimer l’intégralité du fichier App.js et remplacer par le code ci-dessous :

```
import React, { useState } from 'react';

function App() {

  return (
    <div>
      <h1>Accueil</h1>
      <h2>Bienvenue sur la page d’accueil</h2>

      <div>
        <button>
          Bouton
        </button>
      </div>

    </div>
  );
}

export default App;

```



### Installer et importer axios

Installer axios via npm afin de l’implémenter dans l’application : 

1. npm install axios



*Source : https://www.npmjs.com/package/axios*



Importer axios dans le fichier App.js :

```
import axios from 'axios';
```



### Faire un call API

On créer une fonction async dans la fonction App que l’on appelle fetchData et qui effectue un call API :

```
const [books, setBooks] = useState(null);

const fetchData = async () => {
	const response = await axios.get(
		'https://www.anapioficeandfire.com/api/books?pageSize=30'
	);

	setBooks(response.data);
};

```



On appelle la fonction fetchData sur l’event onClick de notre bouton :

```
<button onClick={fetchData}>
	Bouton
</button>
```



### Utiliser la réponse API

Enfin, on récupère les données que l’API nous renvoie et on les affiche :

```
	<div>
        {books && books.map((book, index) => {
            const cleanedDate = new Date(book.released).toDateString();
            const authors = book.authors.join(', ');
            return (
              <div key={index}>
                <h3>Book {index + 1}</h3>
                <h2>{book.name}</h2>
                <div>
                  <p>👨: {authors}</p>
                  <p>📖: {book.numberOfPages} pages</p>
                  <p>🏘️: {book.country}</p>
                  <p>⏰: {cleanedDate}</p>
                </div>
              </div>
            );
          })}
	</div>
```



### Implémentation du CSS

Créer un fichier style.css dans web-app/ et l’importer dans App.js

```
import './style.css';
```



Utilisation du CSS en React :

```
<div className="bloc">
	<p>👨: {authors}</p>
	<p>📖: {book.numberOfPages} pages</p>
	<p>🏘️: {book.country}</p>
	<p>⏰: {cleanedDate}</p>
</div>

```



Dans le fichier style.css : 

```
.bloc {
    background-color: rgb(224, 224, 224);
    width: 300px;
    border-radius: 20px;
	…
}
```



### Merci d'avoir participé au workshop !

Présenté par César VENZAC