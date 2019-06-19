# MPF Extractor

MPF Extractor (Multi Picture Format Extractor) extracts images stored in images based on the [MPF format](http://www.cipa.jp/std/documents/e/DC-007_E.pdf)

## Installation

Include MPFExtractor.js in your html file or import as a module.

## Usage

See example in `index.html` how this is run. Use either on existing img tags or uploaded files.

Basically, create an `extractor` and call `extract(arrayBuffer, options)` on it with an `arrayBuffer` and an optional `options` object.

`extract()` returns a promise which will resolve to an array of [img elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) or reject with an error message.

### Example
```javascript
  const extractor = new MPFExtractor();
  const options = {
    debug: true,
    extractFII: true
  };

  function onUpload(e) {
    for (const file of e.target.files) {
      let reader = new FileReader();
      reader.onload = () =>
        extractor
          .extract(reader.result, options)
          .then(setImages)
          .catch(setError);
      reader.readAsArrayBuffer(file);
    }
  }

  ...
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://opensource.org/licenses/MIT)