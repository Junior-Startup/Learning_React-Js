# Introdution à React

# Introduction

> React n’est pas à proprement parler un framework mais se présente comme une bibliothèque JavaScript pour créer des interfaces utilisateurs. React est la réponse de Facebook à un problème récurrent : créer des interfaces réutilisables et stateful

# Comment fonctionne React?

> React crée un DOM VIRTUEL en mémoire.
>
> - Le DOM, c'est quoi exactement ?
>   > Le DOM (Document Object Model) est une interface pour vos pages web. C'est une API permettant aux programmes de lire et de manipuler le contenu de la page, sa structure et ses styles.
> - Comment fonctionne le Dom dans React?
>   > Au lieu de manipuler directement le DOM du navigateur, React crée un DOM virtuel en mémoire, où il effectue toutes les manipulations nécessaires, avant d'effectuer les modifications dans le DOM du navigateur.

> React ne change que ce qui doit être changé!

# Utilisation de React

> Pour avoir un aperçu de ce qu'est React, vous pouvez écrire du code React directement en HTML.

> Pour utiliser React en production, vous avez besoin de NPM et Node.js.

1. Réagissez directement en HTML:

> > Le moyen le plus rapide de commencer à apprendre React est d'écrire React directement dans vos fichiers HTML.

> > Commencez par inclure trois scripts, les deux premiers nous permettent d'écrire du code React dans nos JavaScripts, et le troisième, Babel, nous permet d'écrire la syntaxe JSX et ES6 dans les anciens navigateurs.
> > Vous en apprendrez plus sur JSX dans le partie suivate.

- Example:

```html
<!DOCTYPE html>
<html>
  <script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
  <body>
    <div id="mydiv"></div>

    <script type="text/babel">
      class Hello extends React.Component {
        render() {
          return <h1>Hello World!</h1>;
        }
      }

      ReactDOM.render(<Hello />, document.getElementById("mydiv"));
    </script>
  </body>
</html>
```

> Cette façon d'utiliser React peut convenir à des fins de test, mais pour la production, vous devrez configurer un environnement React

> Si vous avez installé NPM et Node.js, vous pouvez créer une application React en installant d'abord l'application create-react-app.

1.  Installez create-react-app en exécutant cette commande dans votre terminal:

```
C:\Users\Your Name>npm install -g create-react-app
```

2.  Ensuite, vous pouvez créer une application React, créons-en une appelée myfirstreact.

Exécutez cette commande pour créer une application React nommée myfirstreact:

```
C:\Users\Your Name>npx create-react-app myfirstreact
```

3. Exécutez l'application React:

Exécutez cette commande pour vous déplacer vers le myfirstreactrépertoire:

```
C:\Users\Your Name>cd myfirstreact
```

4. Exécutez cette commande pour exécuter l'application React myfirstreact:

```
 C:\Users\Your Name\myfirstreact>npm star
```

5. Le résultat:

   ![](assets/screenshot_myfirstreact.png?)

## Modifier l'application React

> Jusqu'ici tout va bien, mais comment changer le contenu?.
> Regardez dans le myfirstreact répertoire et vous trouverez un srcdossier. Dans le srcdossier, il y a un fichier appelé App.js, ouvrez-le et il ressemblera à ceci:

```javascript
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

function App  {

    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <p>
            Edit <code>src/App.js</code> and save to reload.
          </p>
          <a
            className="App-link"
            href="https://reactjs.org"
            target="_blank"
            rel="noopener noreferrer"
          >
            Learn React
          </a>
        </header>
      </div>
    );

}

export default App;
```

- Example:
  > Remplacez tout le contenu à l'intérieur de `<div className="App">`par un `<h1>`élément.
  > Consultez les modifications dans le navigateur lorsque vous cliquez sur Enregistrer.

> Consultez les modifications dans le navigateur lorsque vous cliquez sur Enregistrer.

```javascript
import React, { Component } from "react";

class App extends Component {
  render() {
    return (
      <div className="App">
        <h1>Hello World!</h1>
      </div>
    );
  }
}

export default App;
```

- Le résultat:

  ![](assets/screenshot_helloworld.png?)

Vous disposez maintenant d'un environnement React sur votre ordinateur et vous êtes prêt à en savoir plus sur React.

# JSX

- Qu'est-ce que JSX?

> JSX signifie JavaScript XML.

> JSX nous permet d'écrire du HTML dans React.

> JSX facilite l'écriture et l'ajout de HTML dans React.

- Codage JSX
  > JSX nous permet d'écrire des éléments HTML en JavaScript et de les placer dans le DOM sans aucune méthode createElement() et / ou appendChild().

> JSX convertit les balises HTML en éléments de réaction.

Vous n'êtes pas obligé d'utiliser JSX, mais JSX facilite l'écriture d'applications React.

- Exemple avec JSX:

```jsx
const myelement = <h1>I Love JSX!</h1>;

ReactDOM.render(myelement, document.getElementById("root"));
```

- Exemple 2 sans JSX

```jsx
const myelement = React.createElement("h1", {}, "I do not use JSX!");

ReactDOM.render(myelement, document.getElementById("root"));
```

- Example des Expressions avec JSX:

Avec JSX, vous pouvez écrire des expressions entre accolades { }.

```jsx
const myelement = <h1>React is {5 + 5} times better with JSX</h1>;

const myelement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);

const myelement = (
  <div>
    <h1>I am a Header.</h1>
    <h1>I am a Header too.</h1>
  </div>
);

const myelement = <input type="text" />;
```
