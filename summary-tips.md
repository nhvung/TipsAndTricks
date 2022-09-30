## React

```sh
npm i --save-dev @types/react @types/react-dom react react-dom react-scripts @types/node react-router-dom
```

<b>tsconfig.json</b>

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "sourceMap": true
  },
  "include": [
    "src",
  ]
}
```

## Electron

```sh
npm i --save-dev electron electron-forge
```

## Webpack

```sh
npm i --save-dev @babel/core @babel/preset-env @babel/preset-react css-loader style-loader sass-loader sass webpack webpack-cli
```

<b>webpack.config.js</b>

```js
const path = require('path');
const webpack = require('webpack');

module.exports = {
    mode: 'none',
    entry: {
        app: path.join(__dirname, 'src', 'index.tsx')
    },
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
            }
        ],
    },
    plugins: [
        new webpack.DefinePlugin({
            'process.env.NODE_ENV': '"production"',
        })
    ],
    output: {
        filename: '[name].js',
        path: path.resolve(__dirname, 'dist')
    }
}
```
