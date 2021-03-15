# webpack-config
webpack-config

Webpack - its main purpose is to bundle JavaScript files for usage in a browser, yet it is also capable of transforming, bundling, or packaging just about any resource or asset.

# Install

```bash

mkdir webpack-tutorial
cd webpack-tutorial
```
Now create standard "package.json" file
```bash
yarn init -y 
or
npm init -y 

```

# Install Webpack

```bash
yarn add -D webpack webpack-cli
// or
npm i -D webpack webpack-cli
```

webpack - is a module bundler. 
webpack-cli - offers a variety of commands to make working with webpack easy. 

# Configure webpack 

```bash
touch webpack.config.js
```

`webpack.config.js` will include following sections
* entry point
* output
* loaders
* plugins
* code splitting

Inside `webpack.config.js` first add entry point.
```bash
const path = require("path");

module.exports = {
  entry: { index: path.resolve(__dirname, "src/index.js") }
};
```
Entry point is file which webpack will compile. In our case our entry point is `src/index.js`
Now, add inside `package.json` add script `build`, which runs `webpack`.
```bash
"scripts": {
    "build": "webpack"
}
```

Now run webpack

```bash
yarn build
// или
npm run build
```

As you can see it generated `dist` folder inside which we do have compiled js file.
![image](https://user-images.githubusercontent.com/41279178/111140396-1a75f180-85a4-11eb-847d-7f8e67404404.png)

Now what if we want to change the directory of output file.
Inside `webpack.config.js` update it.

```bash 
const path = require("path");

module.exports = {
  entry: { index: path.resolve(__dirname, "src/index.js") },
  output: {
    path: path.resolve(__dirname, "build")
  }
};
```

Run webpack to see result 
```bash
yarn build
// или
npm run build
```
![image](https://user-images.githubusercontent.com/41279178/111140784-8e17fe80-85a4-11eb-870a-cfcc7f26f910.png)

# Working with HTML 

Currenlty we do have compiled JS file. However, without markup this JS file is useless. That's why we need to configure our `webpack` to work with HTML files.
Add plugin to work with HTML files

```bash
yarn add -D html-webpack-plugin
```

Then update `webpack.config.js` file with following codes

```bash
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
  entry: { index: path.resolve(__dirname, "src/index.js") },
  output: {
        path: path.resolve(__dirname, "build")
    },
  plugins: [
        new HtmlWebpackPlugin({
            template: path.resolve(__dirname, "public/index.html")
        })
    ]
};
```

Here we are telling to webpack to load HTML file from `public/index.html` directory

Since we do not have `public` folder and `index.html` file. We are going to create it inside our project.
![image](https://user-images.githubusercontent.com/41279178/111141874-d84daf80-85a5-11eb-93b2-2ba88a49dbeb.png)


`index.html`
```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Reader</title>
</head>
<body>
    <div id="root"></div>
</body>
</html>
```

# webpack's development server

In order to run webpack in development mode we need ```webpack-dev-server```. 

```bash
yarn add -D webpack-dev-server
```

Now run 
```
npm start
```

![image](https://user-images.githubusercontent.com/41279178/111143965-41cebd80-85a8-11eb-9e87-a414a1172dec.png)


# Webpack's loaders
Webpack enables use of loaders to preprocess files. This allows you to bundle any static resource way beyond JavaScript.

## Working with CSS
To test CSS in webpack create a simple stylesheet in `src/style.css`


Create folder webpack with three files inside.
![image](https://user-images.githubusercontent.com/41279178/111134311-4fcb1100-859d-11eb-8ae4-86c344ab8472.png)
