# dctap.js
Javascript library to parse and manipulate DCTAP CSV files

## Usage:

``` javascript
const { DcTap } = require('dctap');
const dctap = new DcTap();
```

### Command Line

Convert DCTAP CSV to JSON:

``` shell
dctap-to-json examples/allFeatures.csv
```

Convert DCTAP CSV to ShExJ:

``` shell
dctap-to-shexj examples/allFeatures.csv
```

### API

Parse text using a specified URL for relative URL resolution
``` javascript
await dctap.parse(text, new URL('file://' + __dirname));
```

Emit as JSON
``` javascript
console.log(JSON.stringify(dctap.toJson(), null, 2));
```

Emit as ShExJ
``` javascript
console.log(JSON.stringify(dctap.toShExJ(), null, 2));
```

## complete example

``` javascript
const Fs = require('fs');
const { DcTap } = require('dctap');

(async () => {
  const text = Fs.readFileSync('examples/allFeatures.csv');
  const dctap = new DcTap();
  await dctap.parse(text, new URL('file://' + __dirname));
  const schema = dctap.toShExJ();
  console.log(JSON.stringify(schema, null, 2));
})();
```

