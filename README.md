# api documentation for  [prettyjson (v1.2.1)](http://rafeca.com/prettyjson)  [![npm package](https://img.shields.io/npm/v/npmdoc-prettyjson.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-prettyjson) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-prettyjson.svg)](https://travis-ci.org/npmdoc/node-npmdoc-prettyjson)
#### Package for formatting JSON data in a coloured YAML-style, perfect for CLI output

[![NPM](https://nodei.co/npm/prettyjson.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/prettyjson)

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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module prettyjson](#apidoc.module.prettyjson)
1.  [function <span class="apidocSignatureSpan">prettyjson.</span>render (data, options, indentation)](#apidoc.element.prettyjson.render)
1.  [function <span class="apidocSignatureSpan">prettyjson.</span>renderString (data, options, indentation)](#apidoc.element.prettyjson.renderString)
1.  string <span class="apidocSignatureSpan">prettyjson.</span>version



# <a name="apidoc.module.prettyjson"></a>[module prettyjson](#apidoc.module.prettyjson)

#### <a name="apidoc.element.prettyjson.render"></a>[function <span class="apidocSignatureSpan">prettyjson.</span>render (data, options, indentation)](#apidoc.element.prettyjson.render)
- description and source-code
```javascript
function render(data, options, indentation) {
  // Default values
  indentation = indentation || 0;
  options = options || {};
  options.emptyArrayMsg = options.emptyArrayMsg || '(empty array)';
  options.keysColor = options.keysColor || 'green';
  options.dashColor = options.dashColor || 'green';
  options.numberColor = options.numberColor || 'blue';
  options.defaultIndentation = options.defaultIndentation || 2;
  options.noColor = !!options.noColor;
  options.noAlign = !!options.noAlign;

  options.stringColor = options.stringColor || null;

  return renderToArray(data, options, indentation).join('\n');
}
```
- example usage
```shell
...
  projects: ['prettyprint', 'connfu']
};

var options = {
  noColor: true
};

console.log(prettyjson.render(data, options));
'''

And will output:

![Example 4](https://raw.github.com/rafeca/prettyjson/master/images/example1.png)

You can also configure the colors of the hash keys and array dashes
...
```

#### <a name="apidoc.element.prettyjson.renderString"></a>[function <span class="apidocSignatureSpan">prettyjson.</span>renderString (data, options, indentation)](#apidoc.element.prettyjson.renderString)
- description and source-code
```javascript
function renderString(data, options, indentation) {

  var output = '';
  var parsedData;
  // If the input is not a string or if it's empty, just return an empty string
  if (typeof data !== 'string' || data === '') {
    return '';
  }

  // Remove non-JSON characters from the beginning string
  if (data[0] !== '{' && data[0] !== '[') {
    var beginingOfJson;
    if (data.indexOf('{') === -1) {
      beginingOfJson = data.indexOf('[');
    } else if (data.indexOf('[') === -1) {
      beginingOfJson = data.indexOf('{');
    } else if (data.indexOf('{') < data.indexOf('[')) {
      beginingOfJson = data.indexOf('{');
    } else {
      beginingOfJson = data.indexOf('[');
    }
    output += data.substr(0, beginingOfJson) + '\n';
    data = data.substr(beginingOfJson);
  }

  try {
    parsedData = JSON.parse(data);
  } catch (e) {
    // Return an error in case of an invalid JSON
    return colors.red('Error:') + ' Not valid JSON!';
  }

  // Call the real render() method
  output += exports.render(parsedData, options, indentation);
  return output;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
