# TypeScript npm modules

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
* lib - contains result of compulation. it is body of npm module. 
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
* push  - test, build and npm publish
and should contains section typings
```javascript
 "typings": "lib/index"
```
which means that definition for your module in lib/index.d.ts

### How typescript compiler resolve npm-style typescript module?
compiler see node_modules -> search in package.json of module section 'typings' -> insert founded module definitions to compilation context.
### What we should have in index.ts? 
In index.ts you should describe export of module. In most sitiations it mean export all files in module
