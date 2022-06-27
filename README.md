## LEGACY REACT APP <br> ![React-Logo](public/logo192.png) 

### PURPOSE 🎯
  * The Purpose of this guide is to provide a resource for software developers working with tutorials or legacy code that is deprecated and difficult to install correctly. 

### PROJECT REBUILD ⚙️

  *  Regardless of what version of React you have installed, so long as it is _ahead_ of the legacy version you are hoping to work with. 
  * If you do not already have Node installed, do so using your root package installer like Homebrew. 
  * If you do not have React installed, install it using NPM or Yarn. 
  * Afterwards you will create a react project by running the following code in the directory you would like your application to reside:
    ```npx create-react-app my-app```
  * Assuming you have react V18 installed, you will first want to delete the pre-installed *node_modules* folder that the npx command generated. 

  * Next, review the dependencies installed. You will likely see versions and packages that look something like this:

```js
  "dependencies": {
    "@testing-library/jest-dom": "^5.16.4",
    "@testing-library/react": "^13.3.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
  },
```

  * You will want to replace the code above with this code:

```js
  "dependencies": {
    "@testing-library/jest-dom": "^4.2.4",
    "@testing-library/react": "^9.3.2",
    "@testing-library/user-event": "^7.1.2",
    "react": "^16.13.0",
    "react-dom": "^16.13.0",
    "react-scripts": "3.2.0"
  },
```

  * This will tell node what packages to install when you begin the re-installation. This process has some consequences however. For example, the code to access the ```<div id='root'></div>``` in the react project has changed significantly since react V16. 
  * **NOTE:** This installation method will also work with other legacy dependencies such as ```@material-ui/core``` or ```draft.js^0.10.0``` etc.

## UPDATE THE CODE 👨‍💻
  * Find the following code in your ```app.js``` file and ```index.js``` file. 

  * Replace the app.js content that looks like this:
```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

  * With this:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

  * Then replace this index.js content:

```js
import logo from './logo.svg';
import './App.css';

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

  * With this:

```js
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <p>
          Hello World.
        </p>
      </header>
    </div>
  );
}

export default App;
```

## RUN THE BUILD 🏗️

  * If at this point you are getting errors in your terminal, its expected, and you can ignore them. 
  * Run the following code to install the correct dependencies. 
    * ```npm i --legacy-peer-deps```
    * ```npm i react-scripts```
  * At this point you have a functioning React project. In order to run it in the browser, access the scripts with the following run command:
    * ```npm run start```

## COMMENTS OR QUESTIONS  👈
  * This guide was designed to be used specifically with the Epicodus React course section. If there are any questions feel free to email me: ```jakeedgar1012@gmail.com```