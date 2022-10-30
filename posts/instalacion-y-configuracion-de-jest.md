---

title: Instalación y Configuración de Jest para el Frontend en React
menu_order: 1
post_status: publish
post_excerpt: Pasos a seguir para una correcta instalación y configuración de Jest para React.
taxonomy:
    category:
        - Javascript
        - QA Testing
        - Frontend
    post_tag:
        - Jest
        - Babel
        - React
        - instalación
        - configuración
        - frameworks

---


## 1. Instala y configura Jest
---

### 1.1. __Instala Jest, la definición de tipos de Jest y jest-environment-jsdom__
Necesitamos `@types/jest` para que funcione correctamente el IntelliSense. Instalando `jest-environment-jsdom` simulamos un entorno de pruebas para el DOM del navegador, necesario cuando creamos una web app en lugar de una aplicación de servidor (de Node).

```js
npm i -D jest @types/jest jest-environment-jsdom
```

> Si usamos __Fetch API en proyectos anteriores a Node 18__ debemos instalar el siguiente paquete para que no nos de problemas:

```js
npm i -D whatwg-fetch
```

<br>

### 1.2. __Activa el IntelliSense de Jest en VSCode__.
Para ello modifica o crea `jsconfig.json` en la raíz del proyecto:

```json
{	
  "typeAcquisition": {
    "include": ["jest"]
  }
}
```

<br>

### 1.3. __Crea y configura `jest.config.js`__ 
Este archivo debe estar en la raíz del proyecto. También puede llamarse `jest.config.cjs` si en `package.json` tenemos activados los módulos.

> ___RECUERDA___ que si vas a usar __Fetch API en una versión anterior a Node 18__ debes crear también el archivo `jest.setup.js`

***`jest.config.js`*** (en formato `commons.js`)

```js
module.exports = {
    testEnvironment: 'jest-environment-jsdom',
    setupFiles: ['./jest.setup.js']  // Solo para usar Fetch API en versiones anteriores a Node 18
}
```

***`jest.config.js`*** en formato `ES6`
```js
export default {
    testEnvironment: 'jest-environment-jsdom',
    setupFiles: ['./jest.setup.js']  // Solo para usar Fetch API en versiones anteriores a Node 18
}
```

***`jest.setup.js`***

```js
// REPITO Solo para usar Fetch API en versiones anteriores a Node 18
import 'whatwg-fetch';
```

<br>

### 1.4. __Configura `package.json`__
Para monitorizar los cambios en los test y no tener que estar recargando continuamente:

```json
{
  "scripts": {
    "test": "jest --watchAll"
  }
}
```

<br>

## 2. Instala React Testing Library
---
La `Testing Lybrary` es un conjunto de bibliotecas de testing en el entorno de Node. Cada paquete está especializado en un framework, como puede ser `React, Angular, Vue, Cypress, Puppeteer`, etc. En nuestro caso la instalaremos para `React`:

```js
npm i -D @testing-library/react
```

<br>

## 3. Instala y configura Babel (para Jest y React)
---

### 3.1. __Instala las dependencias:__

```js
npm i -D babel-jest @babel/core @babel/preset-env @babel-preset-react
```

### 3.2. __Crea y configura `babel.config.js`:__
También puede llamarse `babel.config.cjs` si en `package.json` tenemos activados los módulos.

[//]: # (Es una de estas dos posibilidades)

```js
module.exports = {
  presets: [['@babel/preset-env', {targets: {node: 'current'}}]],
};
```

```js
module.exports = {
    presets: [
        [ '@babel/preset-env', { targets: { esmodules: true } } ],
        [ '@babel/preset-react', { runtime: 'automatic' } ],
    ],
};
```

> ___RECUERDA___ `babel.config.js` tambien se puede poner en formato `JSON`:

***`babel.config.json`***
```json
{
  "presets": [
    ["@babel/preset-env", {"targets": {"esmodules": true}}],
    ["@babel/preset-react", {"runtime": "automatic"}]
  ]
}
```

<br>

## 4. Por último, crea los test
---

Crea carpeta `test` fuera de `src` a su mismo nivel.  
Crea los archivos de test con el sufijo `.test.js`
