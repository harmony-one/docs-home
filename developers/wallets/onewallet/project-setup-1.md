---
description: This sections covers how to setup your example project.
---

# Project Setup

For this demo we assume such a project setup:

![](../../../.gitbook/assets/image%20%28302%29.png)

Type the following commands in the truffle project you created before:

```bash
mkdir web
cd web
npm init
mkdir src
cd src
touch hmy.js init.js userWallet.js index.html
cd ..
```

### Install Dependencies

> ```bash
> npm i @harmony-js/contract @harmony-js/core @harmony-js/utils parcel-bundler
> ```

### Add Scripts

```javascript
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "server": "http-server",
    "dev": "parcel src/index.html "
  },
```

Or you can just copy-paste the following into your package.json file:

```javascript
{
  "name": "web",
  "version": "1.0.0",
  "description": "Demo to interact with harmony web wallets",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "server": "http-server",
    "dev": "parcel src/index.html "
  },
  "author": "Rachit Anand",
  "license": "ISC",
  "dependencies": {
    "@harmony-js/contract": "^0.1.55",
    "@harmony-js/core": "^0.1.55",
    "@harmony-js/utils": "^0.1.55",
    "eslint": "^7.13.0",
    "eslint-config-prettier": "^6.15.0",
    "eslint-plugin-import": "^2.22.1",
    "http-server": "^0.12.3",
    "parcel-bundler": "^1.12.4",
    "prettier": "^2.1.2"
  },
  "browserslist": [
    "last 2 Firefox versions",
    "last 2 Chrome versions"
  ]
}

```

### Put this into your index.html file

```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input id="inputt">
    <button id="inputtButton">Wallet</button>
    <script src="./init.js"></script>
</body>
</html>
```

