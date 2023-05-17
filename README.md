# Setup React app with Webpack and Eslint
- `npm init -y`
- `mkdir public`
- `touch public/index.html`

webpack
- `npm i webpack webpack-cli --save-dev`
- `mkdir src`
- `touch src/index.js`
- `touch webpack.config.js`

plugins
- `npm i html-webpack-plugin --save-dev`
- `npm i copy-webpack-plugin --save-dev`
- `npm i mini-css-extract-plugin --save-dev`

loaders
- `npm i style-loader --save-dev`
- `npm i css-loader --save-dev`
- `npm i sass sass-loader --save-dev`
- `npm i url-loader --save-dev`

webpack dev server
- `npm i --save-dev webpack-dev-server`

babel
- `npm i @babel/core @babel/preset-env @babel/preset-react babel-loader --save-dev`
- `touch .babelrc`

react
- `npm i react react-dom react-router-dom --save`
- `npm i @babel/preset-react --save-dev`

eslint
- `npm init @eslint/config`

Add starter code to
- index.html
- index.js
- App.jsx
- webpack.config.js
- .babelrc
- .eslintrc.json

Update scripts on
- package.json

---

## Additional items

dotenv (if using env variables)
- `npm install dotenv-webpack --save-dev`
- in webpack.config.js add the following
- - top of file: `const Dotenv = require("dotenv-webpack");`
- - within module.exports, plugins: []: `new Dotenv({systemvars: true,}),`
- create a .env file
- add .env to gitignore
- add env items as `NAME_OF_THING="the thing"`
- use env items as `process.env.NAME_OF_THING`
- make sure eslint has `"node": true,` within 'env' section or you will get linting errors when you use `process`


---

## Loading env variables that can be used in index.html

I can't find where I sourced this info originally, but if you need to load env variables into the index.html file (e.g. adding a google analytics tag) this is what you need:

- in package.json your scripts need to include the export xargs etc.
```js
  "build": "export $(xargs < ./.env) && webpack --mode production",
  "start": "export $(xargs < ./.env) && webpack serve --mode development",
```

- in webpack.config.js you need to import a file that exports process env and then you can use it in your htmlPlugins
```js
const env = require('./exportProcessEnv');

new HtmlWebpackPlugin({
  template: path.join(__dirname, 'public', 'index.html'),
  favicon: './src/assets/images/favicon.ico',
  gaTokenValue: env.GA_TOKEN,
}),
```

- your exportProcessEnv file needs to contain 
```js
/* eslint-disable dot-notation */
module.exports = process['env'];

/*
 * Webpack’s DefinePlugin only replaces free variables and by avoiding
 * using process.env directly there, you circumvent the Webpack replacement magic
 * So we create this file, then require it in webpack to access the env variables.
 */
```

You may also need some extra work with your Drone setup e.g. one project I have an `extract-env-vars.sh` file that is called in drone.yml as part of the builds `./extract-env-vars.sh ./helm/dev.yaml ./.env`. As part of this file it extrats the env vars from the secrets file in a way that webpack can then use them.