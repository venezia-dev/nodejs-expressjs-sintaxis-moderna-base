Guia para empezar una api de cero con node.js mas Express.js para usar la sintaxis moderna de JavaScript.

Para lograr esto vamos a usar Babel, para escribir código moderno y lo convierte a un código que lo entienda la mayoría de los navegadores.

**Empecemos...**

* Iniciando una Api
`npm init –-y`	

* Instalamos Express.js
`npm i express`	

* Instalamos Babel como "devDependencies"
`npm i @babel/core @babel/cli @babel/node @babel/preset-env @babel/plugin-transform-runtime -D`	

**Que es cada cosa...**
* Core: Modulo principal de babel.
* Cli: Para utilizar babel desde consola.
* Node: Para usar babel adentro de node.
* Preset-env: Para configurar Babel.
* Plugin-transform-runtime: Para no tener problema con códigos async/await.

**Seguimos...**
* Crear un archivo llamado “.babelrc” en la raíz de la api, para escribir las configuraciones.
```javascript
{
    "presets": [
        "@babel/env"
    ],
    "plugins": [
        "@babel/transform-runtime"
    ]
}
```
* Creamos el típico index.js en /src

```javascript
import express from "express";

const app = express();

app.set("port", 3000);

app.listen(app.get("port"));

console.log("Servidor Encendido, en el puerto:", app.get("port"));
```
Usando la sintaxis moderna de “import”

* Para ejecutar la api con babel, hay q modificar el siguiente comando en Scripts del package.json.

```javascript
  "scripts": {
    "start": "babel-node src/index.js"
  },
```

* Ejecutamos
`npm run start`


**Bonus Track:**

* Ya de paso para dejar una buena base, para trabajar con la api y que se actualice automáticamente cada vez que guardamos el código, vamos a agregarle “Nodemon”

`npm install --save-dev nodemon`

* Como ultimo paso tenemos que modificar los comandos de ejecucion en scripts de package.json

```javascript
  "scripts": {
    "babel-node": "babel-node",
    "dev": "nodemon --exec npm run babel-node -- src/index.js",
    "build": "babel src --out-dir dist",
    "start": "node dist/index.js"
  },
```

* Dev: Para ejecutar con babel-node el src/index.js con nodemon.
* Build: Para hacer un build en la carpeta dist de la api para prod.
* Start: Ejecuta la api en prod ya con su build en la carpeta dist.

Con este último punto, finalizamos la guía.

