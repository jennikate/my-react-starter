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
loaders
- `npm i style-loader --save-dev`
- `npm i css-loader --save-dev`
- `npm i sass sass-loader --save-dev`
- `npm i url-loader --save-dev`
webpack dev server
- `npm i --save-dev webpack-dev-server`
babel
- `npm i @babel/core @babel/preset-env babel-loader --save-dev`
- `touch .babelrc`
react
- `npm i react react-dom react-router-dom --save`
- `npm i @babel/preset-react --save-dev`
eslint
- `npm i eslint-plugin-react@latest eslint@latest eslint-plugin-jsx-a11y --save-dev`
- `touch .eslintrc.json`

Add starter code to
- index.html
- index.js
- App.jsx
- webpack.config.js
- .babelrc
- .eslintrc.json

Update scripts on
- package.json