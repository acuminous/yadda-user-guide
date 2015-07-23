# Annotations

```
@Pending
@Browsers=chrome,safari
Feature: Some title

    ...
```
- Annotations must start with the at (@) character and be followed by one or more word characters.
- They can be either tags, e.g. ```@Pending``` or name value pairs separated by the equals (=) character, e.g. ```@Browsers=chrome```.
- Tags are assigned a value of ```true```.
- Annotations are supported on Features, Scenarios and Example Table rows.
- The Mocha and Jasmine plugins supports ```@Pending``` and ```@Only``` annotations.

To access annotations programatically
```js
var feature = new Yadda.parsers.FeatureParser().parse(specification)
// Annotations are converted to lowercase by the parser
if (feature.annotation.pending) {
    // Do stuff
}
```
