# Consommer des API REST avec Fetch et Axios

> La consommation d'API REST dans une application React peut être effectuée de différentes manières, mais dans ce didacticiel, nous discuterons de la façon dont nous pouvons consommer des API REST à l'aide de deux des méthodes les plus populaires connues sous le nom d' Axios (un client HTTP basé sur la promesse) et Fetch API (une API Web intégrée au navigateur). Je vais discuter et mettre en œuvre chacune de ces méthodes en détail et faire la lumière sur certaines des fonctionnalités intéressantes que chacune d'elles a à offrir.

## Qu'est-Ce Qu'une API REST

> Une API REST est une API qui suit ce qui est structuré conformément à la structure REST pour les API. REST signifie «Representational State Transfer». Il se compose de diverses règles que les développeurs suivent lors de la création d'API.

## LES AVANTAGES DES API REST:

- Très facile à apprendre et à comprendre;
- Il offre aux développeurs la possibilité d'organiser des applications complexes en ressources simples;
- Il est facile pour les clients externes de s'appuyer sur votre API REST sans aucune complication;
- Il est très facile à mettre à l'échelle;
- Une API REST n'est pas spécifique à un langage ou à une plate-forme, mais peut être utilisée avec n'importe quel langage ou s'exécuter sur n'importe quelle plate-forme.

## Consommer Des API À L'aide De L'API Fetch

> L'API fetch() est une méthode JavaScript intégrée pour obtenir des ressources à partir d'un serveur ou d'un point de terminaison d'API. C'est similaire à XMLHttpRequest, mais l' API fetch fournit un ensemble de fonctionnalités plus puissant et plus flexible.

> La fetch()méthode API prend toujours un argument obligatoire, qui est le chemin ou l'URL de la ressource que vous souhaitez récupérer. Il renvoie une promesse qui pointe vers la réponse de la demande, que la demande aboutisse ou non. Vous pouvez également éventuellement transmettre un objet d'options init comme second argument.

> Une fois qu'une réponse a été récupérée, plusieurs méthodes intégrées sont disponibles pour définir le contenu du corps et comment il doit être géré.

### PARAMÈTRES DE L'API FETCH:

- **resource** : Il s'agit du chemin vers la ressource que vous souhaitez récupérer, cela peut être un lien direct vers le chemin de la ressource ou un objet de requête

- **init** : Il s'agit d'un objet contenant tout paramètre personnalisé ou informations d'identification que vous aimeriez fournir pour votre fetch()demande. Voici quelques-unes des options possibles qui peuvent être contenues dans l' initobjet:

  - method : C'est pour spécifier la méthode de requête HTTP, par exemple GET, POST, etc.

  - headers : Ceci permet de spécifier les en-têtes que vous souhaitez ajouter à votre requête, généralement contenus dans un objet ou un littéral d'objet.

  - body : Ceci est pour spécifier un corps que vous souhaitez ajouter à votre demande: cela peut être un Blob, BufferSource, FormData, URLSearchParams, USVStringou ReadableStreamobjet

  - mode : Ceci est pour spécifier le mode que vous souhaitez utiliser pour la demande, par exemple, cors, no-corsou same-origin

  - credentials : Ceci pour spécifier les informations d'identification de la demande que vous souhaitez utiliser pour la demande, cette option doit être fournie si vous envisagez d'envoyer automatiquement des cookies pour le domaine actuel.

### SYNTAXE DE BASE POUR L'UTILISATION DE L'API FETCH ():

```javascript
fetch("https://api.github.com/users/hacktivist123/repos")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

### utilisation du fetch() dans une application react:

> Dans le code ci-dessus, nous récupérons des données à partir d'une URL qui renvoie des données au format JSON, puis nous les imprimons sur la console. La forme la plus simple d'utilisation de fetch () prend souvent un seul argument qui est le chemin d'accès à la ressource que vous voulez récupérer, puis renvoie une promesse contenant la réponse de la demande de récupération. Cette réponse est un objet.

```javascript
import React, { useEffect, useState } from "react";
import "./App.css";
import List from "./components/List";
import withListLoading from "./components/withListLoading";
function App() {
  const ListLoading = withListLoading(List);
  const [appState, setAppState] = useState({
    loading: false,
    repos: null,
  });

  useEffect(() => {
    setAppState({ loading: true });
    const apiUrl = `https://api.github.com/users/hacktivist123/repos`;
    fetch(apiUrl)
      .then((res) => res.json())
      .then((repos) => {
        setAppState({ loading: false, repos: repos });
      });
  }, [setAppState]);
  return (
    <div className="App">
      <div className="container">
        <h1>My Repositories</h1>
      </div>
      <div className="repo-container">
        <ListLoading isLoading={appState.loading} repos={appState.repos} />
      </div>
      <footer>
        <div className="footer">
          Built{" "}
          <span role="img" aria-label="love">
            💚
          </span>{" "}
          with by Shedrack Akintayo
        </div>
      </footer>
    </div>
  );
}
export default App;
```

## Consommer Des API Avec Axios

> Axios est un client HTTP basé sur des promesses facile à utiliser pour le navigateur et node.js. Étant donné qu'Axios est basé sur la promesse.Avec Axios, nous avons la possibilité d'intercepter et d'annuler la demande, il dispose également d'une fonctionnalité intégrée qui offre une protection côté client contre la falsification de demandes intersites.

## CARACTÉRISTIQUES D'AXIOS

- Interception des demandes et des réponses
- Gestion des erreurs simplifiée
- Protection contre XSRF
- Prise en charge de la progression du téléchargement
- Délai de réponse
- La possibilité d'annuler les demandes
- Prise en charge des anciens navigateurs
- Transformation automatique des données JSON

## FAIRE DES REQUÊTES AVEC AXIOS

> Faire des requêtes HTTP avec Axios est assez simple. Le code ci-dessous explique essentiellement comment effectuer une requête HTTP.

```javascript
// Make a GET request
axios({
  method: "get",
  url: "https://api.github.com/users/hacktivist123",
});

// Make a Post Request
axios({
  method: "post",
  url: "/login",
  data: {
    firstName: "shedrack",
    lastName: "akintayo",
  },
});
```

> Axios fournit également un ensemble de méthodes abrégées pour exécuter différentes requêtes HTTP. Les méthodes sont les suivantes:

- axios.request(config)
- axios.get(url[, config])
- axios.delete(url[, config])
- axios.head(url[, config])
- axios.options(url[, config])
- axios.post(url[, data[, config]])
- axios.put(url[, data[, config]])
- axios.patch(url[, data[, config]])

> Axios offre aux développeurs la possibilité de créer et de gérer des requêtes HTTP simultanées à l'aide de la axios.all()méthode. Cette méthode prend un tableau d'arguments et retourne un seul objet de promesse qui ne résout que lorsque tous les arguments passés dans le tableau ont été résolus.

```javascript
axios
  .all([
    axios.get("https://api.github.com/users/hacktivist123"),
    axios.get("https://api.github.com/users/adenekan41"),
  ])
  .then((response) => {
    console.log("Date created: ", response[0].data.created_at);
    console.log("Date created: ", response[1].data.created_at);
  });
```

## Instalation de Axios dans une application React

> Maintenant, installons Axios dans notre application React en exécutant l'une des opérations suivantes:

```
npm install axios

or

yarn add axios
```

> Une fois l'installation terminée, nous devons importer axios dans notre App.js. Dans notre App.js, nous ajouterons la ligne suivante en haut de notre fichier App.js:

```javascript
import axios from "axios";
```

> Après avoir ajouté la ligne de code à notre App.js, tout ce que nous avons à faire à l'intérieur de notre useEffect()est d'écrire le code suivant:

```javascript
useEffect(() => {
  setAppState({ loading: true });
  const apiUrl = "https://api.github.com/users/hacktivist123/repos";
  axios.get(apiUrl).then((repos) => {
    const allRepos = repos.data;
    setAppState({ loading: false, repos: allRepos });
  });
}, [setAppState]);
```

> Vous avez peut-être remarqué que nous avons maintenant remplacé l'API fetch par la méthode abrégée Axios axios.getpour faire une getrequête à l'API.

```javascript
axios.get(apiUrl).then((repos) => {
  const allRepos = repos.data;
  setAppState({ loading: false, repos: allRepos });
});
```

> Dans ce bloc de code, nous faisons une requête GET puis nous retournons une promesse qui contient les données de repos et affectons les données à une variable constante appelée allRepos. Nous définissons ensuite l'état de chargement actuel sur false et transmettons également les données de la demande à la variable d'état du repos.
