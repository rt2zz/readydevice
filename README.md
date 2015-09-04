# readydevice
Avoid coordinated bootstrap sequences or singleton pseudo-global devices.

## Usage
It is not particularly pretty, but it works and does not bleed complexity.
```js
var readydevice = require('readydevice')

var getSomething = readydevice((ready) => {
  someAsyncSetup(function(something){
    ready(something)
  })
})

//...later

getSomething(function(something){
  //If the device is already `ready` it will immediately fire the callback.
  //Otherwise the callback will be queued and invoked once the device is ready.
})
```
