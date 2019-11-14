# auto-import
This utility was originally written as a tool to dynamically register routes under express.

## Install
```bash
npm i @cosmicdynamo/autoImport
```

## Example Usage
```javascript
const express = require('express');
const autoImport = require("@cosmicdynamo/auto-import");

const app = express();
autoImport("./**/*.route.js", __dirname).then(files => {
  files.forEach(({name, exports}) => {
    const resourceName = name.split(".")[0].toLowerCase();
    app.use('/' + resourceName, exports)
  });
  app.listen(3000);
}, err => console.error('err', err.message, err));
```