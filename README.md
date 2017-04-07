# api documentation for  [node-php (v0.0.1)](https://github.com/mkschreder/siteboot_php)  [![npm package](https://img.shields.io/npm/v/npmdoc-node-php.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-node-php) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-node-php.svg)](https://travis-ci.org/npmdoc/node-npmdoc-node-php)
#### Node JS modules for running wordpress in node js

[![NPM](https://nodei.co/npm/node-php.png?downloads=true)](https://www.npmjs.com/package/node-php)

[![apidoc](https://npmdoc.github.io/node-npmdoc-node-php/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-node-php_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-node-php/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-node-php/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-node-php/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Martin K. Schröder"
    },
    "bin": {},
    "bugs": {
        "url": "https://github.com/mkschreder/siteboot_php/issues"
    },
    "dependencies": {},
    "description": "Node JS modules for running wordpress in node js",
    "devDependencies": {
        "cluster": "*",
        "express": "*",
        "request": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "6505546118413d029c349493583ff40a8f154d4c",
        "tarball": "https://registry.npmjs.org/node-php/-/node-php-0.0.1.tgz"
    },
    "engines": {
        "node": "*"
    },
    "homepage": "https://github.com/mkschreder/siteboot_php",
    "main": "./main.js",
    "maintainers": [
        {
            "name": "mullvad",
            "email": "info@sakradorren.se"
        }
    ],
    "name": "node-php",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "url": "git+https://github.com/mkschreder/siteboot_php.git"
    },
    "scripts": {
        "test": "nodeunit tests"
    },
    "version": "0.0.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module node-php](#apidoc.module.node-php)
1.  [function <span class="apidocSignatureSpan">node-php.</span>cgi (phproot)](#apidoc.element.node-php.cgi)



# <a name="apidoc.module.node-php"></a>[module node-php](#apidoc.module.node-php)

#### <a name="apidoc.element.node-php.cgi"></a>[function <span class="apidocSignatureSpan">node-php.</span>cgi (phproot)](#apidoc.element.node-php.cgi)
- description and source-code
```javascript
cgi = function (phproot){
	return function(req, res, next){
    var data = null;

    //req.setEncoding('utf8');
    req.on('data', function(chunk) {
			//data.write(chunk.toString('binary'), data.length, chunk.length, 'binary');
			//console.log(chunk);
			if(!data) data = chunk;
			else data = data+chunk;
			//data = data.concat(chunk);
    });
    req.on('end', function() {
			req.rawBody = data||"";
			//console.log(req.rawBody);
			//console.log("ENCODING: "+req.get("Content-type")+", len: "+req.rawBody.length);
			runPHP(req, res, next, phproot);
    });
	}
}
```
- example usage
```shell
...

	var express = require('express');
	var php = require("php");
	var path = require("path");
	
	var app = express();
	
	app.use("/", php.cgi("/path/to/wordpress"));

	app.listen(9090);

	console.log("Server listening!");

Explanation
-----------
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
