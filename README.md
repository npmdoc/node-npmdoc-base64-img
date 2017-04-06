# api documentation for  [base64-img (v1.0.3)](https://github.com/douzi8/base64-img)  [![npm package](https://img.shields.io/npm/v/npmdoc-base64-img.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-base64-img) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-base64-img.svg)](https://travis-ci.org/npmdoc/node-npmdoc-base64-img)
#### Convert img to base64, or convert base64 to img

[![NPM](https://nodei.co/npm/base64-img.png?downloads=true)](https://www.npmjs.com/package/base64-img)

[![apidoc](https://npmdoc.github.io/node-npmdoc-base64-img/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-base64-img_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-base64-img/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-base64-img/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-base64-img/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "douzi",
        "email": "liaowei08@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/douzi8/base64-img/issues"
    },
    "dependencies": {
        "ajax-request": "^1.2.0",
        "file-system": "^2.1.0"
    },
    "description": "Convert img to base64, or convert base64 to img",
    "devDependencies": {
        "grunt": "^0.4.5",
        "grunt-contrib-jshint": "^0.10.0"
    },
    "directories": {},
    "dist": {
        "shasum": "a8c0284900047103421e1f9e0214011333866806",
        "tarball": "https://registry.npmjs.org/base64-img/-/base64-img-1.0.3.tgz"
    },
    "gitHead": "44cd228b37e25a18e93e99a3cb2ab0c56a3a8c2d",
    "homepage": "https://github.com/douzi8/base64-img",
    "keywords": [
        "base64",
        "img",
        "image",
        "img base64"
    ],
    "license": "ISC",
    "main": "base64-img.js",
    "maintainers": [
        {
            "name": "douzi",
            "email": "liaowei08@gmail.com"
        }
    ],
    "name": "base64-img",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/douzi8/base64-img.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "1.0.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module base64-img](#apidoc.module.base64-img)
1.  [function <span class="apidocSignatureSpan">base64-img.</span>base64 (filename, callback)](#apidoc.element.base64-img.base64)
1.  [function <span class="apidocSignatureSpan">base64-img.</span>base64Sync (filename)](#apidoc.element.base64-img.base64Sync)
1.  [function <span class="apidocSignatureSpan">base64-img.</span>img (data, destpath, name, callback)](#apidoc.element.base64-img.img)
1.  [function <span class="apidocSignatureSpan">base64-img.</span>imgSync (data, destpath, name)](#apidoc.element.base64-img.imgSync)
1.  [function <span class="apidocSignatureSpan">base64-img.</span>requestBase64 (url, callback)](#apidoc.element.base64-img.requestBase64)



# <a name="apidoc.module.base64-img"></a>[module base64-img](#apidoc.module.base64-img)

#### <a name="apidoc.element.base64-img.base64"></a>[function <span class="apidocSignatureSpan">base64-img.</span>base64 (filename, callback)](#apidoc.element.base64-img.base64)
- description and source-code
```javascript
base64 = function (filename, callback) {
  if (!callback) callback = util.noop;

  fs.readFile(filename, function(err, data) {
    if (err) return callback(err);

    callback(null, base64(filename, data));
  });
}
```
- example usage
```shell
...
npm install base64-img --save
'''
## test
'''
mocha
'''
## API
### .base64(filename, callback)
Convert image file to image base64 data
* {string} ''filename'' required
The image path
* {function} ''callback(err, data)'' required
Callback with image base64 data
'''js
base64Img.base64('path/demo.png', function(err, data) {})
...
```

#### <a name="apidoc.element.base64-img.base64Sync"></a>[function <span class="apidocSignatureSpan">base64-img.</span>base64Sync (filename)](#apidoc.element.base64-img.base64Sync)
- description and source-code
```javascript
base64Sync = function (filename) {
  var data = fs.readFileSync(filename);

  return base64(filename, data);
}
```
- example usage
```shell
...
The image path
* {function} ''callback(err, data)'' required
Callback with image base64 data
'''js
base64Img.base64('path/demo.png', function(err, data) {})
'''

### .base64Sync(filename)
The api same as base64, but it's synchronous
'''js
var data = base64Img.base64Sync('path/demo.png');
'''

### .requestBase64(url, callback)
* {string} ''url'' required
...
```

#### <a name="apidoc.element.base64-img.img"></a>[function <span class="apidocSignatureSpan">base64-img.</span>img (data, destpath, name, callback)](#apidoc.element.base64-img.img)
- description and source-code
```javascript
img = function (data, destpath, name, callback) {
  var result = img(data);
  var filepath = path.join(destpath, name + result.extname);

  fs.writeFile(filepath, result.base64, { encoding: 'base64' }, function(err) {
    callback(err, filepath);
  });
}
```
- example usage
```shell
...
'''js
var url = 'http://../demo.png';
base64Img.requestBase64(url, function(err, res, body) {

});
'''

### .img(data, destpath, name, callback)
Convert image base64 data to image
* {string} ''data'' required
Image base64 data
* {string} ''destpath'' required
Dest path, if the destpath is root, pass empty string
* {string} ''name'' required
The image's filename
...
```

#### <a name="apidoc.element.base64-img.imgSync"></a>[function <span class="apidocSignatureSpan">base64-img.</span>imgSync (data, destpath, name)](#apidoc.element.base64-img.imgSync)
- description and source-code
```javascript
imgSync = function (data, destpath, name) {
  var result = img(data);
  var filepath = path.join(destpath, name + result.extname);

  fs.writeFileSync(filepath, result.base64, { encoding: 'base64' });
  return filepath;
}
```
- example usage
```shell
...
* {string} ''name'' required
The image's filename
* {function} ''callback(err, filepath)'' required
'''js
base64Img.img('data:image/png;base64,...', 'dest', '1', function(err, filepath) {});
'''

### .imgSync(data, destpath, name)
The api same as img, but it's synchronous
'''js
var filepath = base64Img.imgSync('data:image/png;base64,...', '', '2');
'''
...
```

#### <a name="apidoc.element.base64-img.requestBase64"></a>[function <span class="apidocSignatureSpan">base64-img.</span>requestBase64 (url, callback)](#apidoc.element.base64-img.requestBase64)
- description and source-code
```javascript
requestBase64 = function (url, callback) {
  request({
    url: url,
    isBuffer: true
  }, function (err, res, body) {
    if (err) return callback(err);

    var data = 'data:' + res.headers['content-type'] + ';base64,' + body.toString('base64');
    callback(err, res, data);
  });
}
```
- example usage
```shell
...

### .base64Sync(filename)
The api same as base64, but it's synchronous
'''js
var data = base64Img.base64Sync('path/demo.png');
'''

### .requestBase64(url, callback)
* {string} ''url'' required
* {function} ''callback(err, res, body)'' required
Callback with http request
'''js
var url = 'http://../demo.png';
base64Img.requestBase64(url, function(err, res, body) {
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
