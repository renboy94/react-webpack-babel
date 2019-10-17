# React Setup with Webpack and Babel

Setup React using webpack and babel instead of create-react-app

```
# install depenencies
npm install
```

## Summary of how to setup React from scratch

1. Create an empty folder

```
mkdir my-react-project
```

2. Install dependencies

```
# Initialize package.json
npm init -y

# Install React and React Dom
npm install --save react react-dom

# Install Webpack tools as a dev dependency
npm install --save-dev webpack webpack-dev-server webpack-cli

# Install Babel tools and html-webpack-plugin as a dev dependency
npm install --save-dev @babel/core babel-loader @babel/preset-env @babel/preset-react html-webpack-plu
gin

# package.json should look like this after installing dependencies
{
  "name": "my-react-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
      "test": ""
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.10.2",
    "react-dom": "^16.10.2"
  },
  "devDependencies": {
    "@babel/core": "^7.6.4",
    "@babel/preset-env": "^7.6.3",
    "@babel/preset-react": "^7.6.3",
    "babel-loader": "^8.0.6",
    "html-webpack-plugin": "^3.2.0",
    "webpack": "^4.41.2",
    "webpack-cli": "^3.3.9",
    "webpack-dev-server": "^3.8.2"
  }
}
```

3. Create a webpack.config.js in the root folder:

```
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index_bundle.js"
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html"
    })
  ]
};
```
