# Learning ReactJS 

*Create React app without Using "create-react-app"*

This tutorial teaches you how to create your own React app by self-configuring your minimum packages and Webpack.

## commands from terminal
```bash
mkdir <my-app>
cd <my-app>

# creates package.json file with default configurations
npm init -y
# Flag -y will tell npm to use all default config option while creating 

# install react and react-dom dependencies
npm install react react-dom

# creates gitigonre file and add the corresponding items
vim .gitignore

# create app folder in your project folder
mkdir app
cd app

# creates and complete three files in app directory
touch index.js index.css index.html

# adding all require depnendincies to the project
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli webpack-dev-server babel-loader css-loader style-loader html-webpack-plugin
# Flag --save-dev to differentiate out build dependencies than our app dependencies

# creating webpack configurations file
touch webpack.config.js

# Add babel preset config to our package.json file

# Add "create" and "start" taps inside "script" tag

```

## File Structure

```
.
+-- _app
|   +-- index.js
|   +-- index.css
|   +-- index.html
+-- webpack.config.js
+-- package.json
```

## Files Content

### `index.html`

```html
<!DOCTYPE html>
<html>
    <head><title>
        my-app
    </title></head>
    <body>
        <div id="app"></div>
    </body>
</html>
```

### `index.js`

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

class App extends React.Component{
    render(){
        return(
            <div>Hello World</div>
        )
    }
}

ReactDOM.render(<App />, document.getElementById('app'))
```

### `webpack.config.js`

```javascript
var path = require('path');
var HtmlWebpackPlugin =  require('html-webpack-plugin');

module.exports = {
    entry : './app/index.js',
    output : {
        path : path.resolve(__dirname , 'dist'),
        filename: 'index_bundle.js'
    },
    module : {
        rules : [
            {test : /\.(js)$/, use:'babel-loader'},
            {test : /\.css$/, use:['style-loader', 'css-loader']}
        ]
    },
    mode:'development',
    plugins : [
        new HtmlWebpackPlugin ({
            template : 'app/index.html'
        })
    ]

};
````

### `package.json`

```json
{
  "name": "ex2-create-react-without-create-react-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "babel":{
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  },
  "scripts": {
    "create": "webpack",
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server --open"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.13.1",
    "react-dom": "^16.13.1"
  },
  "devDependencies": {
    "@babel/core": "^7.11.6",
    "@babel/preset-env": "^7.11.5",
    "@babel/preset-react": "^7.10.4",
    "babel-loader": "^8.1.0",
    "css-loader": "^4.3.0",
    "html-webpack-plugin": "^4.4.1",
    "style-loader": "^1.2.1",
    "webpack": "^4.44.1",
    "webpack-cli": "^3.3.12",
    "webpack-dev-server": "^3.11.0"
  }
}
```

### `.gitignore`

```
node_modules
.DS_Store
dist
```

