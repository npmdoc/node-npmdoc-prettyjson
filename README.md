# npmdoc-prettyjson

#### basic api documentation for  [prettyjson (v1.2.1)](http://rafeca.com/prettyjson)  [![npm package](https://img.shields.io/npm/v/npmdoc-prettyjson.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-prettyjson) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-prettyjson.svg)](https://travis-ci.org/npmdoc/node-npmdoc-prettyjson)

#### Package for formatting JSON data in a coloured YAML-style, perfect for CLI output

[![NPM](https://nodei.co/npm/prettyjson.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/prettyjson)

- [https://npmdoc.github.io/node-npmdoc-prettyjson/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-prettyjson/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-prettyjson/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-prettyjson/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-prettyjson/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-prettyjson/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Rafael de Oleza",
        "url": "https://github.com/rafeca"
    },
    "bin": {
        "prettyjson": "./bin/prettyjson"
    },
    "bugs": {
        "url": "https://github.com/rafeca/prettyjson/issues"
    },
    "dependencies": {
        "colors": "^1.1.2",
        "minimist": "^1.2.0"
    },
    "description": "Package for formatting JSON data in a coloured YAML-style, perfect for CLI output",
    "devDependencies": {
        "coveralls": "^2.11.15",
        "istanbul": "^0.4.5",
        "jshint": "^2.9.4",
        "mocha": "^3.1.2",
        "mocha-lcov-reporter": "^1.2.0",
        "should": "^11.1.1"
    },
    "directories": {},
    "dist": {
        "shasum": "fcffab41d19cab4dfae5e575e64246619b12d289",
        "tarball": "https://registry.npmjs.org/prettyjson/-/prettyjson-1.2.1.tgz"
    },
    "gitHead": "cd2d53156cb9b457133a0eeeadb55913c34d5207",
    "homepage": "http://rafeca.com/prettyjson",
    "keywords": [
        "json",
        "cli",
        "formatting",
        "colors"
    ],
    "license": "MIT",
    "main": "./lib/prettyjson",
    "maintainers": [
        {
            "name": "rafeca"
        }
    ],
    "name": "prettyjson",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/rafeca/prettyjson.git"
    },
    "scripts": {
        "changelog": "git log $(git describe --tags --abbrev=0)..HEAD --pretty='* %s' --first-parent",
        "coverage": "istanbul cover _mocha --report lcovonly -- -R spec",
        "coveralls": "npm run coverage && cat ./coverage/lcov.info | coveralls && rm -rf ./coverage",
        "jshint": "jshint lib/*.js test/*.js",
        "test": "npm run jshint && mocha --reporter spec",
        "testwin": "node ./node_modules/mocha/bin/mocha --reporter spec"
    },
    "version": "1.2.1"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
