# Moify CV

This is the official library for the [moify.me] computer vision (CV)
service. It is used internally by the moifyCv API.

Moify's CV API is a rate-limited service, this library is low-level and
will return a fail if you hit the limit, leaving you to handle this
and/or retry later. In this case, please follow an exponential backoff.

The underlying CV engine is [libccv], using [SURF-Cascade Detection]
and limited to its default face recognition model. For more details
see [cv.moify.me].

## Install

    npm install --save moify-cv

## Usage

```js
let moifyCV = require('moify-cv')

moifyCv.file('/path/to/file.png') // or jpeg, or gif
.then(faces => {})
.catch(console.error)

moifyCv(require('fs').readFileSync('file.jpg'))
.then(faces => {})
```

## API

Promises are native ES6, and may be consumed by any Promise-aware library.

In browser environments, `Blob` is used where `Buffer` is specified below,
and the `.file()` variant is not available. In browsers where native Promises
are not available, they are shimmed using jakearchibald's ES6 Promise polyfill.

### moifyCv.file(filename: String) -> Promise

Convenience function that reads a file asynchronously and hands it over to the
main function below. Only available in Node.js environments.

### moifyCv(image: Buffer | Blob) -> Promise

//

## About

Licensed under [MIT].

[MIT]: http://passcod.mit-license.org
[moify.me]: https://moify.me
[cv.moify.me]: https://cv.moify.me
[libccv]: http://libccv.org/
[SURF-Cascade Detection]: http://libccv.org/doc/doc-scd/
