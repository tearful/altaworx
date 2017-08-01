# altaworx
this is imitate altaworx project

## First edition - setup webpack
```
     ### simple webpack - Getting Strarted
     1. create Folder, for example - altaworx
     2. cd altaworx
     3. npm init -y
     4. npm install --save-dev webpack
```
We've added wepack to the project. Now, directory structure:
```
    altaworx
        | - package.json
        | - node_modules
```
Next, we'll create some files into the project, directory structure: 
```
    altaworx
        | - package.json
        | - node_modules
      + | - /dist
        + | - index.html
      + | - /src
        + | - index.js 
```
dist/index.html
```
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>Getting Started</title>
        <link rel="stylesheet" href="">
    </head>
    <body>
        <script src="bundle.js"></script>
    </body>
    </html>
```
src/index.js
```
     function component() {
        var element = document.createElement('div');

        // Lodash, now imported by this script
        element.innerHTML = _.join(['Hello', 'wepack'], ' ');

        return element;
    }

    document.body.appendChild(component());

```
Now, we need to do:
```
    $ npm install --save lodash
```
These are not enough. We need to create `webpack.config.js`. Directory structure: 
```
    altaworx
        | - package.json
        | - node_modules
      + | - webpack.config.js
        | - /dist
          | - index.html
        | - /src
          | - index.js 
```
webpack.config.js
```
    const path = require('path');

    module.exports = {
      entry: './src/index.js',
      output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
      }
    };
```
Now, we need to run `webpack --config webpack.config.js` command. But, we have a simpler command. Before that, we need to change `package.json` file:
```
    {
        ...
        "script": {
            ...
            "build": "webpack"
            ...
        }
        ...
    }
```
OK, now, we run `npm run build` command. Opean `index.html` for browser. You can see Hello webpack.