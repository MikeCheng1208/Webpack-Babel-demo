## Webpack4 + Babel7 整合範例
相關參考可以點此 [教學連結](https://medium.com/@Mike_Cheng1208/webpack教學-四-javascript-與-babel-1d7acd911e63)

- 開發環境
    - Nodejs:  https://nodejs.org/en/
    - NVM: https://github.com/coreybutler/nvm-windows/releases
    - VSCode: https://code.visualstudio.com/#alt-downloads
    
- NVM指令
    - nvm list：查看已安裝的版本
    - nvm list available：查看有哪些 Node 版本可以裝
    - nvm install v8.11.2：安裝指定的 Node 版本
    - nvm use v8.11.2：指定 Node 版本
    
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
