# Structure de projet React

Après sa création, votre projet devrait ressembler à ceci:

```
mon-application /
  README.md
  node_modules /
  package.json
  .gitignore
  Publique/
    index.html
    favicon.ico
  src /

    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

1. node_modules:
   > Le dossier node_modules contient les bibliothèques téléchargées depuis npm. Vous ne devriez pas le pousser vers github (vous devriez même l'ajouter à votre .gitignore), car tous ceux qui clonent votre dépôt peuvent le télécharger eux-mêmes (en fonction de votre package.json).

![](assets/node_module.png?)

2. package.json:

> La configuration globale du projet React est décrite dans le package.json. Voici à quoi cela ressemble.

![](assets/package.json.png?)

Nous pouvons voir les attributs suivants:

- name - Représente le nom de l'application qui a été transmis à create-react-app.

- version - Affiche la version actuelle.
  dépendances - Liste de tous les modules / versions requis pour notre application. Par défaut, npm installerait la version majeure la plus récente.

- devDependencies - Répertorie tous les modules / versions pour exécuter l'application dans un environnement de développement.
  Pour ajouter un package à cette liste, lors de l'installation, utilisez --save-dev.
  Par exemple, npm install <package-name> --save-dev
  De cette façon, il est ajouté à la liste des fichiers devDependencies.

- scripts - Liste de tous les alias qui peuvent être utilisés pour accéder aux commandes react-scripts de manière efficace:

  - **Start**
    > React utilise Node.js lors du développement pour ouvrir l'application , ainsi le script vous permet de démarrer le serveur.http://localhost:3000start

  > Vous pouvez exécuter la startcommande de script sur le terminal avec npm ou yarn.

  ```
  npm start
  ```

  ou

  ```
  yarn start
  ```

  - **build**

  > C'est l'un des principaux avantages du buildscript. L'autre est la performance; comme vous le savez, un mode de développement n'est pas optimisé. Et React utilise le buildscript pour s'assurer que le projet fini est regroupé, réduit et optimisé avec les meilleures pratiques.build est utiliser lors de l'hébergement sur un serveur pour optimiser le code.

  > Le script peut être exécuté avec les commandes suivantes.

  ```
  npm build
  ```

  ou

  ```
  yarn build
  ```

* **build**

> create-react-apputilise Jest comme testeur. Le testscript vous permet de lancer le test runner en mode veille interactive. Je ne vais pas plonger trop profondément dans le test des applications React , mais gardez à l'esprit que tout fichier avec ou extensions sera exécuté lorsque le script est lancé..test.js.spec.js

> Le testscript peut être exécuté sur le terminal avec les commandes suivantes.

```
npm test
```

ou

```
yarn test
```

- **eject**
  > Ce script c'est une "opération à sens unique" et avertit que "une fois que vous éjectez, vous ne pouvez pas revenir en arrière!"create-react-app

> create-react-appest livré avec une excellente configuration et vous aide à créer votre application React en tenant compte des meilleures pratiques pour l'optimiser. Cependant, l'exécution du ejectscript supprimera la dépendance de génération unique de votre projet. Cela signifie qu'il copiera les fichiers de configuration et les dépendances transitives (par exemple, Webpack, Babel, etc.) en tant que dépendances dans le fichier. Si vous faites cela, vous devrez vous assurer que les dépendances sont installées avant de générer votre projet.package.json

> Après avoir exécuté la ejectcommande, il ne sera pas possible de l'exécuter à nouveau car tous les scripts seront disponibles à l'exception de celui- ejectci. N'utilisez cette commande que si vous en avez besoin. Sinon, respectez la configuration par défaut. C'est mieux, de toute façon.

> Pour exécuter la commande sur le terminal, tapez la commande suivante.

```
npm eject
```

ou

```
yarn eject
```

3. **.gitignore**

> Ce fichier est le fichier standard qui est utilisé par l'outil de contrôle de source git pour identifier les fichiers et dossiers qui doivent être ignorés lors de la validation du code. Tant que ce fichier n’existe pas, la commande create-react-app ne créera pas de dépôt git dans ce dossier.

![](assets/gitignore.png?)

4. **public / index.html**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    ...
    <title>Sandbox</title>
  </head>
  <body>
    <script>
      You need to enable JavaScript to run this app.
    </script>
    <div id="root"></div>
    <!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->
  </body>
</html>
```

> lorsque l'application démarre, c'est la première page qui est chargée. Ce sera le seul fichier html de toute l'application puisque React est généralement écrit en utilisant JSX que je couvrirai plus tard. De plus, ce fichier a une ligne de code `<div id = ”root”> </div>` . Cette ligne est très significative car tous les composants de l'application sont chargés dans cette div.

5. **src / index.js**

```javascript
import React from "react";
import ReactDOM from "react-dom";
import "./index.css";
import App from "./App";
import * as serviceWorker from "./serviceWorker";

ReactDOM.render(<App />, document.getElementById("root"));
```

> il s'agit du fichier javascript correspondant à index.html. Ce fichier a la ligne de code suivante qui est très significative. ReactDOM.render (<App />, document.getElementById ('racine'));

> La ligne de code ci-dessus indique que App Component (couvrira bientôt App Component) doit être chargé dans un élément html avec id root . Ce n'est rien d'autre que l' élément div présent dans index.html.

6. src / index.css

   > Le fichier CSS correspondant à index.js.

7. **src / App.js**

```javascript
import React from "react";
import logo from "./logo.svg";
import "./App.css";

function App() {
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

> il s'agit du fichier pour App Component. Le composant App est le composant principal de React qui agit comme un conteneur pour tous les autres composants.

> Changez le contenu de la balise <p> de Edit <code>src/App.js</code> and save to reload. à Hello, world et enregistrez vos changements.

```javascript
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>Hello, world</p>
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
```

Allez sur votre navigateur et vous verrez le changement :

![](assets/appchangement.png?)
Vous avez maintenant fait votre première mise à jour vers un composant React

8. src / App.css

   > Le fichier CSS correspondant à App.js.
