# mocha-automatic-coffeemaker

[![npm version](https://badge.fury.io/js/mocha-automatic-coffeemaker.svg)](http://badge.fury.io/js/mocha-automatic-coffeemaker)
[![Build Status](https://travis-ci.org/kjirou/mocha-automatic-coffeemaker.svg?branch=master)](https://travis-ci.org/kjirou/mocha-automatic-coffeemaker)

Generate a test code of [mocha](https://www.npmjs.com/package/mocha) by the same path structure


## Installation

```bash
npm install -g mocha-automatic-coffeemaker
```


## Example

```bash
$ genmochatest lib/utils.js
Generated successfully!
root: /home/username/your-project
src : lib/utils.js
test: test/lib/utils.js
```

```bash
$ cat test/lib/utils.js
describe('lib/utils', function() {
});
```


## Usage

```
$ genmochatest [options] <target-file-path>


<target-file-path>

  A file path of the code that you want to write a test

  e.g.
    lib/foo.js
    /path/to/lib/x/y/foo.js


[options]

  --extensions, -e
    Default: 'js,es,es6,es7,coffee,ts'

  --force, -f
    Default: false
    Overwrite a test code, even if it already exists

  --omission, -o
    Default: null

  --prefix, -p
    Default: 'test'

  --root, -r
    Default: process.cwd()

  --template, -t
    Default: process.cwd() + '/mocha-automatic-coffeemaker-template.js'
```


## Template Example

You can specify the template of test code like the following code:

```js
module.exports = function(data) {

  var filePath = data.filePath;
  var noExtensionFilePath = data.noExtensionFilePath;
  var fileName = data.fileName;
  var noExtensionFileName = data.noExtensionFileName;

  return [
    "describe('" + noExtensionFilePath + "', function() {",
    "});",
  ].join('\n');
};
```
