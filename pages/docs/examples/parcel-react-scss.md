import withDoc from '../../../lib/with-doc'

import { sergio } from '../../../lib/data/team'
import Now from '../../../components/now/now'
import { InternalLink } from '../../../components/text/link'
import { TerminalInput } from '../../../components/text/terminal'

export const meta = {
  title: 'Building a Parcel React App',
  description: 'Creating a single page web app with Parcel and SCSS support and deploying it with Now',
  date: '24 Aug 2018',
  authors: [omar2205],
  editUrl: 'pages/docs/examples/parcel-react-scss.md'
}

[Parcel](https://parceljs.org) is a web application bundler, differentiated by its developer experience. It offers blazing fast performance utilizing multicore processing, and requires zero configuration.

In this example, we are goin to build a simple parcel app and deploy it with Now.

Demo: [parcel-react.now.sh](https://parcel-react.now.sh/) 

You can check the source by adding `/_src` to the end of the url or by clicking here

[Source](https://parcel-react.now.sh/_src)

## Setup

Here is our `package.json` you can copy it and `npm i` to install all the dependencies (If you don't want SASS/SCSS support you can remove the line `"node-sass": "^4.9.3",`)

```
{
  "name": "parcel-app",
  "scripts": {
    "start": "parcel index.html --port 8080 --hmr-port 8181",
    "build": "parcel build index.html",
    "clear-dist": "rm dist/*",
    "now-start": "serve ./dist"
  },
  "dependencies": {
    "babel-preset-env": "^1.7.0",
    "babel-preset-react": "^6.24.1",
    "node-sass": "^4.9.3",
    "parcel-bundler": "^1.9.7",
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
    "serve": "^10.0.0"
  }
}
```

Now create `index.html`
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Parcel</title>
</head>
<body>
<noscript>You need to have Javascript enabled.  </noscript>
<div id="app"></div>
<script src="src/index.js"></script>
</body>
</html>
```

and `src/index.js`
```
import React, { Component } from "react";
import ReactDOM from "react-dom";
import App from './App';
import './main.scss';

var mountNode = document.getElementById("app");
ReactDOM.render(<App />, mountNode);
```
also `src/App.js`
```
import React, { Component } from 'react'

export default class App extends Component {
  render() {
    return (
      <div className="container">
          <h1>Hello World</h1>
          <p>Built using Parcel and deployed with Now.sh!</p>
          <a href="https://zeit.co/docs/examples/parcel-react-scss">zeit.co/docs</a>
      </div>
    )
  }
}
```
If you want SASS/SCSS support and you installed the `node-sass` here is the `src/main.scss` 
```
@import url("https://fonts.googleapis.com/css?family=Nunito+Sans");
body {
    margin: 0;
    font-family: 'Nunito Sans';
}
.container {
    margin: 0 auto;
    max-width: 1280px;
    width: 90%;
}
h1 {
    text-align: center;
    font-size: 4.2rem;
    line-height: 110%;
    margin: 2.8rem 0 1.68rem 0;
    font-weight: 400;
}
a {
    text-decoration: none;
    color: #039be5;
    text-decoration: none;
    -webkit-tap-highlight-color: transparent;
}
@media only screen and (min-width: 700px) {
    width: 85%;
}
```

Now we all set, You can test it by running 

<TerminalInput>npm start</TerminalInput> 

and open [localhost:8080](http://localhost:8080)




## Deploying our Application
To deploy our application we are going to run

<TerminalInput>now</TerminalInput>

When Now finishes uploading the files and deployed our application you will the url.

But in the case of a real application (not used for testing purposes), you would now have to <InternalLink href="/docs/features/aliases">assign an alias</InternalLink> to it.

export default withDoc({...meta})(({children}) => <>{children}</>)
