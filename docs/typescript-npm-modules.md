# TypeScript npm modules guide
#### If you have good skils in npm and typescript -  skip this long text stream and see [example of typescript npm module](https://github.com/stepancar/ts-team-npm-module) else ..
## Why typescript npm module?
See [why typescript](https://basarat.gitbooks.io/typescript/content/docs/why-typescript.html)
See [whats great in npm ](https://www.quora.com/Node-js/Whats-so-great-about-npm)

We need to reuse classes, functions in number of projects, which located in the different repositories, and we want to have an opportunity to change the sources of the reused components. npm solves this requirements. It provides versions of packages, easy for edit and install. Ok, why we mix typescript and npm? Typescript provides type checking for our code, it is very important for reused components. For example we change count of function arguments in reused module. Typescript will check call signature and throw compile-time error. We will be notified about problem before runed our application.



Each our npm module should have this structure:

    |-- home
    |   |-- package.json
    |   |-- .npmingnore
    |   |-- lib
    |   |-- src
    |       |-- tsconfig.json
    |       |-- index.ts
    |       |-- tsd.json
    |       |-- typings

* package.json - [standard npm module config](https://docs.npmjs.com/files/package.json)
* .npmignore - [see](https://docs.npmjs.com/misc/developers)
* lib - contains result of compilation. javascript code and d.ts for it
* src - sources of module. Here you can store your ts files

## package.json
example of package.json
```javascript
{
  "name": "http-lite",
  "description": "small http library",
  "version": "0.0.4",
  "main": "lib/index.js",
  "typings": "lib/index",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "tsc --project src",
    "push": "npm run build & npm version patch & npm --registry http://registry.jsteam.sletat.ru publish",
    "commit": "svn commit /sdf/f/sdf/kl/df"
  },
  "author": {
    "name": "sletat.js.team"
  }
}
```
package.json should contains scripts:
* test  - test script for your code
* build - script which build javascript module, which will be available in lib directory
* push  - test, build and npm publish to npm repo

```javascript
npm run test
npm run build
npm run push

```
and should contains section typings
```javascript
 "typings": "lib/index"
```
which means that definition for your module in lib/index.d.ts

### How typescript compiler resolve npm-style typescript module?
compiler see node_modules -> search in package.json of module section 'typings' -> insert founded module definitions to compilation context.

### What we should have in index.ts? 
In index.ts you should describe export of module. In most sitiations it mean export all files in module


### How to use this module in javascript(not typescript)

In javascript you can use this module like in typescript, Cuz typescript just javascrip with typesystem and with additional features support.
