---
layout: post
title: "Getting started with angular2"
date:   2016-05-09 00:00:00 +0500
categories: angular2 typescript
---

Let's start from zero and build a simple angular2 app.

We can also write angular2 app in javscript, typescript and dart
But in this post, I'm using typescript.

>Typescript is a typed superset of Javascript that compiles to plain javascript

Here is file structure of simple angular2 app
```
angular2-app
|-- app
   |-- app.component.ts
   |-- boot.ts
|-- node_modules ...
|-- typings
   |-- typings.d.ts
|-- index.htm;
|-- typings.json
|-- tsconfig.json
|-- styles.css
|-- system.config.js
```

Create a **new project folder**
	
	mkdir angular2-app
	cd angular2-app

Add a **tsconfig.json** file to the project folder and copy/paste the following:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": false
  },
  "exclude": [
    "node_modules",
    "typings/main",
    "typings/main.d.ts"
  ]
}
```

Add a **typings.json** file to the project folder and copy/paste the following:
```json
{
  "ambientDependencies": {
    "es6-shim": "registry:dt/es6-shim#0.31.2+20160317120654",
    "jasmine": "registry:dt/jasmine#2.2.0+20160412134438"
  }
}
```

Add a **package.json** file to the project folder and copy/paste the following:

```json
{
  "name": "angular2-quickstart",
  "version": "1.0.0",
  "scripts": {
    "start": "tsc && concurrently \"npm run tsc:w\" \"npm run lite\" ",
    "lite": "lite-server",
    "postinstall": "typings install",
    "tsc": "tsc",
    "tsc:w": "tsc -w",
    "typings": "typings"
  },
  "license": "ISC",
  "dependencies": {
    "@angular/common":  "2.0.0-rc.1",
    "@angular/compiler":  "2.0.0-rc.1",
    "@angular/core":  "2.0.0-rc.1",
    "@angular/http":  "2.0.0-rc.1",
    "@angular/platform-browser":  "2.0.0-rc.1",
    "@angular/platform-browser-dynamic":  "2.0.0-rc.1",
    "@angular/router":  "2.0.0-rc.1",
    "@angular/router-deprecated":  "2.0.0-rc.1",
    "@angular/upgrade":  "2.0.0-rc.1",

    "systemjs": "0.19.27",
    "es6-shim": "^0.35.0",
    "reflect-metadata": "^0.1.3",
    "rxjs": "5.0.0-beta.6",
    "zone.js": "^0.6.12",

    "angular2-in-memory-web-api": "0.0.7",
    "bootstrap": "^3.3.6"
  },
  "devDependencies": {
    "concurrently": "^2.0.0",
    "lite-server": "^2.2.0",
    "typescript": "^1.8.10",
    "typings":"^0.8.1"
  }
}
```

Install these packages by running this command
	
	npm install

Create an **app sub-folder** in root directory and make it the current directory

	mkdir app
	cd app

**Add a component file** named **app.component.ts** and paste the following lines:

```
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: '<h1>My First Angular 2 App</h1>'
})
export class AppComponent { }
```

Add a new file **main.ts** to the app/ folder:

```
import { bootstrap }    from '@angular/platform-browser-dynamic';

import { AppComponent } from './app.component';

bootstrap(AppComponent);
```

Navigate to the project root folder:

	cd ..

Create an **index.html** file in this root folder and paste the following lines:

```
<html>
  <head>
    <title>Angular 2 QuickStart</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="styles.css">

    <!-- 1. Load libraries -->
     <!-- Polyfill(s) for older browsers -->
    <script src="node_modules/es6-shim/es6-shim.min.js"></script>

    <script src="node_modules/zone.js/dist/zone.js"></script>
    <script src="node_modules/reflect-metadata/Reflect.js"></script>
    <script src="node_modules/systemjs/dist/system.src.js"></script>

    <!-- 2. Configure SystemJS -->
    <script src="systemjs.config.js"></script>
    <script>
      System.import('app').catch(function(err){ console.error(err);  });
    </script>
  </head>

  <!-- 3. Display the application -->
  <body>
    <my-app>Loading...</my-app>
  </body>
</html>
```

Create **system.config** file for system module loader:

```
(function(global) {

  // map tells the System loader where to look for things
  var map = {
    'app':                        'app', // 'dist',
    'rxjs':                       'node_modules/rxjs',
    'angular2-in-memory-web-api': 'node_modules/angular2-in-memory-web-api',
    '@angular':                   'node_modules/@angular'
  };

  // packages tells the System loader how to load when no filename and/or no extension
  var packages = {
    'app':                        { main: 'main.js',  defaultExtension: 'js' },
    'rxjs':                       { defaultExtension: 'js' },
    'angular2-in-memory-web-api': { defaultExtension: 'js' },
  };

  var packageNames = [
    '@angular/common',
    '@angular/compiler',
    '@angular/core',
    '@angular/http',
    '@angular/platform-browser',
    '@angular/platform-browser-dynamic',
    '@angular/router',
    '@angular/router-deprecated',
    '@angular/testing',
    '@angular/upgrade',
  ];

  // add package entries for angular packages in the form '@angular/common': { main: 'index.js', defaultExtension: 'js' }
  packageNames.forEach(function(pkgName) {
    packages[pkgName] = { main: 'index.js', defaultExtension: 'js' };
  });

  var config = {
    map: map,
    packages: packages
  }

  // filterSystemConfig - index.html's chance to modify config before we register it.
  if (global.filterSystemConfig) { global.filterSystemConfig(config); }

  System.config(config);

})(this);
```

Create a **styles.css** in the root folder and start styling, perhaps with this set:

```
/* Master Styles */
h1 {
  color: #369; 
  font-family: Arial, Helvetica, sans-serif;   
  font-size: 250%;
}
h2, h3 { 
  color: #444;
  font-family: Arial, Helvetica, sans-serif;   
  font-weight: lighter;
}
body { 
  margin: 2em; 
}
body, input[text], button { 
  color: #888; 
  font-family: Cambria, Georgia; 
}
```

Execute this command to compile and run app:
	
	npm start

Hurrah! We done with first angular app.
Our first application doesn't do much. It's basically "Hello, World" for Angular 2.
