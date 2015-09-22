В проектах мы используем 
TypeScript 1.6
бла, бла про настройку 
Для сборки TypeScript используется ts-loader и typescript
Webpack
бла бла про наситройку

Сборка возможна в 3х конфигурациях:
Test, Release, Debug.
webpack --configuration=Debug
webpack --configuration=Test
webpack --configuration=Release
Пример файла конфигурации для webpack;
```javascript
var webpack = require('webpack');
var configuration = getCLIParam("configuration", "Release");
console.log("webpack runned in " + configuration + " configuration");
module.exports = {
    context: __dirname,
    entry: './src/MainSearch.tsx',
    output: {
        path: __dirname,
        filename: './../../../AgencyRelease/front-end/public/main-search/app.js'
    },
    resolve: {
        extensions: ['', '.tsx', '.ts', '.js']
    },
    module: {
        loaders: [
            { test: /\.css$/, loader: 'style-loader!css-loader'
            },
            { test: /\.ts(x?)$/, loader: 'ts-loader' }
        ]
    },
    plugins: configuration === "Release" ? [
        new webpack.optimize.UglifyJsPlugin({minimize: true}),
        new webpack.ContextReplacementPlugin(/moment[\/\\]locale$/, /ru/)
    ]: []
}
function isCLIParamExists(nameOfArgument){
   return process.argv.indexOf(nameOfArgument) != -1;
}
function getCLIParam(cliParamName, defaultValue){
     for (var i = 0; i< process.argv.length; i++){
          if (process.argv[i].indexOf(cliParamName)!=-1){
              var configurationParamString = process.argv[i];
              return configurationParamString.slice(configurationParamString.indexOf('=')+1);
          }
          else continue;
     }
     return defaultValue;
}
```
