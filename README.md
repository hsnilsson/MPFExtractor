# MPF Extractor (Multi-Picture Format Extractor)

Extracts multiple images (such as iPhone depthmaps) stored in single image files of the [MPF format](assets/DC-007_E.pdf).

### Demo

Hopefully still hosted on [hsnilsson.com/mpfextractor/](https://hsnilsson.com/mpfextractor/) or [mpfextractor.netlify.com](https://mpfextractor.netlify.com).

### Overview

For example iPhone 8 Plus, X, and XSMax stores depth information in portrait/bokeh mode as grayscale images called depthmaps inside the original image files. What gives? Well, especially depthmaps can be fun because those can also be used to view a photo in 3D!

So if you have the depthmap, how can you view the photo in 3D? Try upload one along the original image on Facebook and it'll automatically convert it to a 3D photo! Or try it out in [depthy.me](http://depthy.me)!

The images are stored inside an image file as in shown in Figure 1:

<img src="assets/Individual images overview.png">

## Usage

Include MPFExtractor.js in your html file or import as a module.

(Also see examples in `index.html` how to use the extractor: Either on HTML `<img>` elements, or on uploaded files.)

As below, create an `extractor`, set options if needed, and call `extractor.extract(arrayBuffer, options)` with an `arrayBuffer` representing the MPF image file.

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
