This repo is to reproduce `css-loader` bug https://github.com/webpack-contrib/css-loader/issues/617  

Using node v8.7.0 x64 on Windows 10  
Using npm v5.5.1
 
Simply install doing:  `npm install`  
Then build (uses `laravel-mix`) running: `npm run dev`
 
 
Webpack configuration is injected through the `webpack.mix.js` file, and it's minimal to reproduce the error.

`src/index.css` contains 1 single style  
`src/index.js` simply includes the css file via `import` and nothing else
 
Webpack build fails with following error:

```
 ERROR  Failed to compile with 1 errors
 
 
 error  in ./src/index.css

Module build failed: Unknown word (5:1)

  3 | // load the styles
  4 | var content = require("!!../node_modules/css-loader/index.js!./index.css");
> 5 | if(typeof content === 'string') content = [[module.id, content, '']];
    | ^
  6 | // Prepare cssTransformation
  7 | var transform;
  8 |


 @ ./src/index.css 4:14-148
 @ ./src/index.js
 @ multi ./src/index.js
 ```