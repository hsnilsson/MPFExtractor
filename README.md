# MPF Extractor (Multi-Picture Format Extractor)

Extracts images stored in images based on the [MPF format](assets/DC-007_E.pdf).
For example iPhone 8 Plus, X, and XSMax stores depth information in portrait/bokeh mode as grayscale images called depthmaps inside the original images. What gives? Well, especially depthmaps can be fun because those can also be used to view a photo in 3D! Or 2.5D rather... Try upload one along the original image on Facebook and it'll automatically convert it to a 3D photo! Or try it out in [depthy.me](http://depthy.me)!

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
