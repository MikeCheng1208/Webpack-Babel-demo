## Webpack4 + Babel7 整合範例
相關參考可以點此 [教學連結](https://medium.com/@Mike_Cheng1208/webpack教學-四-javascript-與-babel-1d7acd911e63)

---
webpack.config.js
```javascript
var path = require('path');
module.exports = {
    context: path.resolve(__dirname, 'js'),
    entry: {
        index: './index.js'
    },
    output: {
        path: path.resolve(__dirname, 'js'),
        filename: './index.bundle.js',
    },
    module: {
        rules: [
            {
                test: /\.(js)$/,
                exclude: /(node_modules)/,
                use: {
                    loader: 'babel-loader',
                    options: {
                      presets: ['@babel/preset-env']
                    }
                }
            }
        ]
    }
}

```
package.json
```json
{
  "name": "Babel",
  "version": "1.0.0",
  "description": "",
  "main": "webpack.config.js",
  "scripts": {
    "watch": "webpack --mode development --watch",
    "start": "webpack --mode development",
    "deploy": "webpack --mode production"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/core": "^7.0.0",
    "@babel/preset-env": "^7.0.0",
    "babel-loader": "^8.0.2",
    "webpack": "^4.5.0",
    "webpack-cli": "^2.0.14",
    "webpack-dev-server": "^3.1.1"
  }
}

```