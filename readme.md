### Babel with Webpack Exploration

Babel - allows us to use latest javascript syntax (es6,es7,es8, next gen) by converting it to a syntax that most old browsers can understand.(More)[https://babeljs.io/]
Webpack - It bundles javascript,css other static files that you need.(More)[https://webpack.js.org/]

### Getting Started

`npm init -y`

`npm install --save-dev babel-cli`

`npm install --save-dev babel-preset-env` - will use this us our presets, see `.babelrc`

create `.babelrc` inside will be:

```bash
      {
        "presets": ["env"]
      }
```

`.babelrc` used to set configuration for babelrc, can also set inside package.json:

```json
      {
        "babel": {
          //config
        }
      }
```

for more babel config see (here)[https://babeljs.io/docs/usage/api/#options]

will now create directories required:

`mkdir src dist` - will create directory src and dist

now lets add scripts inside our package.json

```json
"scripts": {
  "babel src -d dist"
}
```

`babel src -d dist` - means that all js files inside src will be translated and the output will be put inside dist folder

now we can run `npm run build`

We can now start setting up our webpack to bundle js or css if we have a lot of files so that it will become a single file.

`npm install webpack webpack-cli --save-dev`

create `webpack.config.js` file in root directory of the app.

`touch webpack.config.js`

Inside `webpack.config.js`:

```JavaScript
const path = require('path');

module.exports = {
  // Our root javascript or main file that runs first
  entry: './src/index.js',
  output: {
// the output of the bundled javascript will be named main.js inside dist folder
    filename: 'main.js'
    path: path.resolve(__dirname, 'dist'),
  },
};
```

Now lets update our scripts inside `package.json`

```json
"scripts": {
  "build": "babel src -d dist; webpack"
}
```

Everything now is done, we can now use the javascript outputed by webpack.
We can Also use latest javascript syntax because we have babel.
Everytime we had changes on src files must run `npm run build` so that webpack will generate updated js codes.
