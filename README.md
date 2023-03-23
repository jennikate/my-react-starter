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
