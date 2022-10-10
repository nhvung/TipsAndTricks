## React

```sh
npm i --save-dev @types/react @types/react-dom react react-dom react-scripts @types/node react-router-dom @types/uuid
```

<b>tsconfig.json</b>

```json
{
  "compilerOptions": {
    "outDir": "./dist/",
    "noImplicitAny": true,
    "module": "es6",
    "target": "es5",
    "jsx": "react-jsx",
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "moduleResolution": "node",
    "esModuleInterop": false
  }
}
```
<b>index.tsx</b>

```ts
import React from 'react';
import { createRoot } from 'react-dom/client';
import { v4 } from 'uuid';

const divRootId = v4();
let divRoot = document.getElementById(divRootId);
if (!divRoot) {
    divRoot = document.createElement("div");
    divRoot.id = divRootId;
    document.body.appendChild(divRoot);
}

const root = createRoot(divRoot);
root.render(<React.StrictMode>

</React.StrictMode>);
```

## Electron

```sh
npm i --save-dev electron electron-forge
```

## Webpack

```sh
npm i --save-dev @babel/core @babel/preset-env @babel/preset-react css-loader style-loader sass-loader sass webpack webpack-cli ts-loader
```

<b>webpack.config.js</b>

```js
const path = require('path');
const webpack = require('webpack');

module.exports = {
    mode: 'none',
    entry: path.join(__dirname, './src/index.tsx'),
    target: 'web',
    resolve: {
        extensions: ['.ts', '.tsx', '.js']
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: '/node_modules/'
            },
            {
                test: /\.css$/i,
                use: ['style-loader', 'css-loader'],
            },
            {
                test: /\.(png|jpe?g|gif|svg|eot|ttf|woff|woff2)$/i,
                loader: 'file-loader',
                options: {
                    name: '[path][name].[ext]',
                },
            },
        ],
    },
    plugins: [
        new webpack.DefinePlugin({
            'process.env.NODE_ENV': '"production"',
        }),
        new webpack.SourceMapDevToolPlugin({
            filename: "reactapp1.js.map"
        }),
    ],
    output: {
        filename: 'reactapp1.js',
        path: path.resolve(__dirname, 'dist'),
        publicPath: "/"
    },
}
```
