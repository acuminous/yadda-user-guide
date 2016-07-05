# Dictionaries
Dictionaries can be used to simplify steps, re-use regular expressions and convert parameters to a desired type.

## Simple Definitions
```js
var dictionary = new Yadda.Dictionary()
    .define('gender', /(male|female)/);

var library = Yadda.localisation.English.library(dictionary)
    .given('A $gender user', function(gender) {
        // Code goes here
    })
```

## Nested Definitions
```js
var dictionary = new Yadda.Dictionary()
    .define('address', '$street, $postcode')
    .define('street', /(\d+) (\w+))
    .define('postcode', /((GIR &0AA)|((([A-PR-UWYZ][A-HK-Y]?[0-9][0-9]?)|(([A-PR-UWYZ][0-9][A-HJKSTUW])|([A-PR-UWYZ][A-HK-Y][0-9][ABEHMNPRV-Y]))) &[0-9][ABD-HJLNP-UW-Z]{2}))/)

var library = Yadda.localisation.English.library(dictionary)
    .given('An $address', function(number, street, postcode) {
        // Code goes here
    })
```

## Converters
```js
var dictionary = new Yadda.Dictionary()
    .define('num', /(\d+)/, Yadda.converters.integer);

var library = Yadda.localisation.English.library(dictionary)
    .given('A whole number $num', function(number) {
        // Number will be an integer rather than a string
    })
```
Yadda providers converters to integers, floats and dates.

## Custom Converters
It's trivial to write your own converters, just define a function which takes the same number of arguments as matching groups plus a callback
```js
function quantity_converter(amount, units, cb) {
    cb(null, { amount: amount, units: units })
};

var dictionary = new Yadda.Dictionary()
    .define('quantity', /(\d+) (\w+)/, quantity_converter);

var library = Yadda.localisation.English.library(dictionary)
    .given('a delay of $quantity', function(quantity) {
        // quantity will be an object with two fields 'amount' and 'units'
    })
```
By combining custom converters with multiline steps you can parse entire documents such as CSV files, XML files or data tables. What's more because converters are asynchronous you can even use them to retrieve entities from remote systems.


