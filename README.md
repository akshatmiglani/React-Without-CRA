# React App Without Create-React-App

This repository provides a comprehensive guide on launching a React app from scratch, without relying on tools like Create React App (CRA). It delves into core building blocks like Webpack and Babel, empowering you with a deeper understanding and customization capabilities. Explore the code, configuration files, and detailed documentation to gain hands-on experience with manual React app setup.

While tools like Create React App (CRA) streamline project setup, understanding how to build a React app manually offers valuable benefits:

## Deeper Understanding: 
Gain a deeper grasp of the underlying tools and technologies that power your React apps.
## Customization: 
Tailor the build process to your specific needs, integrating different testing frameworks, linters, or bundling configurations.
## Flexibility: 
Adapt your setup to work with legacy projects or specific library requirements that might conflict with CRA defaults.
Essential Building Blocks:

## React & ReactDOM: 
These core libraries form the foundation of your React app, allowing you to create components and interact with the DOM.
## Module Bundler (Webpack): 
Webpack acts as the conductor, bundling your React code, JavaScript modules, CSS, and other assets into a single, optimized file for the browser.
## Babel: 
This transpiler ensures compatibility across different browsers by converting modern JavaScript (e.g., ES6) to older, more widely understood versions.
## HTML Template: 

Finally, an index.html file serves as the entry point for your React app. It provides a container for the bundled JavaScript and a place to reference any external resources.

## Use npm install to directly install dependencies with their required versions

@babel/preset-env: This Babel preset allows you to use the latest JavaScript features without having to worry about compatibility issues. It automatically determines the Babel plugins needed based on the environment you're targeting.

react: React is a JavaScript library for building user interfaces. It allows developers to create reusable UI components and manage their state efficiently.

react-dom: React DOM is a package that provides DOM-specific methods for working with React elements. It's used to render React components in the browser's DOM.

Now, let's move on to the devDependencies:

@babel/core: Babel core is the main engine of Babel. It's responsible for parsing, transforming, and generating code.

@babel/preset-react: This Babel preset is specifically designed to enable the use of JSX syntax in your React applications. It transforms JSX into plain JavaScript that can be understood by browsers.

babel-loader: Babel loader is a webpack loader that allows you to transpile JavaScript files using Babel. It's essential for integrating Babel into your webpack build process.

html-webpack-plugin: This webpack plugin simplifies the creation of HTML files to serve your bundled JavaScript. It automatically generates an HTML file that includes the necessary script tags for your webpack bundles.

webpack: Webpack is a module bundler for JavaScript applications. It takes modules with dependencies and generates static assets representing those modules.

webpack-cli: Webpack CLI provides a command-line interface for webpack. It allows you to run webpack builds and provides various options for configuring your webpack build process.

webpack-dev-server: Webpack Dev Server is a development server that provides live reloading functionality. It allows you to quickly see the changes you make to your code without having to manually refresh the browser.

``` bash
npm install react@^18.3.1 react-dom@^18.3.1 --save
npm install @babel/preset-env@^7.24.6 @babel/core@^7.24.6 @babel/preset-react@^7.24.6 babel-loader@^9.1.3 html-webpack-plugin@^5.6.0 webpack@^5.91.0 webpack-cli@^5.1.4 webpack-dev-server@^5.0.4--save-dev
```
## Webpack Application Configuration

## Entry Point:
The entry property specifies the entry point for your application. In this case, it's set to ./src/index.js, indicating that webpack will start building your dependency graph from the index.js file located in the src directory.
```
entry: './src/index.js',
```
## Output Configuration:
The output property defines the output directory and filename for bundled JavaScript files. It specifies the path where the bundled files will be stored and the filename of the bundled JavaScript file.
```
output: {
    path: path.join(__dirname, '/dist'),
    filename: 'bundle.js'
},
```
## HtmlWebpackPlugin:
The HtmlWebpackPlugin simplifies the creation of HTML files to serve your bundled JavaScript. It generates an HTML file that includes the bundled JavaScript file automatically. The template option specifies the path to the HTML template file.
```
plugins: [
    new HTMLWebpackPlugin({
        template: './src/index.html'
    })
],
```
## Module Rules:
The module property allows you to define how webpack should process different types of files. In this case, it specifies rules for processing JavaScript files. The rules array contains an object that defines the test for matching files (using a regular expression), excludes node_modules directory, and specifies the loader to use (babel-loader). Additionally, it configures Babel options to use the presets @babel/preset-env and @babel/preset-react for transpiling JavaScript and JSX code respectively.

```js
module: {
    rules: [
        {
            test: /.js$/,
            exclude: /node_modules/,
            use: {
                loader: 'babel-loader',
                options: {
                    presets: ['@babel/preset-env', '@babel/preset-react']
                }
            }
        }
    ]
}
```
## Creating Application Files
Next, let's create essential files for our React application:

## index.js:
This is the entry point of our application where we typically render our root React component.
## App.jsx:
Your main React component resides here.
## index.html:
A basic HTML file where your React application will be mounted.
Package.json Configuration
In your package.json file, add scripts for starting the development server and building your production-ready bundle.

## Package.json Configuration
In your package.json file, add scripts for starting the development server and building your production-ready bundle.

```
"scripts": {
    "start": "webpack-dev-server --mode development --open --hot",
    "build": "webpack --mode production"
}
```

## Building Your React Application
Once everything is set up, you can build your React application for production using:
```bash
npm run build
```
