# Creating a react app from scratch

## Step 1: Create a new directory(folder) on your desktop. Name it whatever youd like

## Step 2: Make a package.json inside of the new directory
npm init --y

## Step 3: Install React, Webpack, and Babel
    
```text
npm install react react-dom
npm install webpack webpack-dev-server html-webpack-plugin @babel/core babel-loader @babel/preset-env @babel/preset-react webpack-cli
```

## Step 4: Create some files

    In your main directory create a file named:
    webpack.config.js

    Create a new directory and name it src and create the following files inside
        - index.js
        - index.html
        
## Step 5: Copy the following contents into the files

## webpack.config.js

```text
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  mode: 'development',
  entry: path.resolve(__dirname, 'src', 'index.js'),
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        loader: 'babel-loader',
        options: {
          presets: ["@babel/preset-env", "@babel/preset-react"]
        }
      }
    ]
  },
  plugins: [new HtmlWebpackPlugin({ template: path.resolve(__dirname, 'src', 'index.html') })]
};
```


## src/index.js

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Helloworld React!</h1>, document.getElementById('root'));
```

## src/index.html

```html
<html>
  <head>
    <title>Hello world App</title>
  </head>
  <body>
  <div id="root"></div>
  <script src="bundle.js"></script>
  </body>
</html>
```

## Step 4: Modify package.json scripts property to include the following npm scripts:
 
 ```json
 "scripts": {
    "start": "webpack-dev-server --open",
    "build": "webpack"
  },
  ```

## Step 5: In your terminal execute the following command to start your project

```bash
npm run start
```
