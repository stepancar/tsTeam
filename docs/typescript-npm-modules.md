# TypeScript npm modules

Each our npm module should have this structure:

    |-- home
    |   |-- package.json
    |   |-- .npmingnore
    |   |-- src
    |       |-- tsconfig.json
    |       |-- index.ts
    |       |-- tsd.json
    |       |-- typings

* package.json - [standard npm module config](https://docs.npmjs.com/files/package.json)
* .npmignore - [see](https://docs.npmjs.com/misc/developers)
* src - sources of module
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
* test
* build
* push
and should contains section typings
```javascript
 "typings": "lib/index"
```
