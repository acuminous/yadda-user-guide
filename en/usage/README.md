# Using Yadda

Yadda is designed to be used programmatically, and plugged into your application or test runner. The core objects are the interpreter, step libraries and dictionaries.

## The Yadda Interpreter
The interpreter iterates over arrays of strings, executing their associated function with parameters parsed from the strings.
```js
var steps = [
    'Step 1',
    'Step 2',
    'Step 3'
];
Yadda.createInstance(library).run(steps);
```

## Step Libraries
Step libraries hold the mapping between strings and functions. The mapping key is a regular expression which can be used to parse parameters from the incoming string.
```js
var library = new Yadda.library();
library.define(/Step (\\d+)/, function(number) {
    console.log('Step', number);
});
```

## Dictionaries
Dictionaries can be used to simplify steps, re-use regular expressions and convert parameters to a desired type.
```js
var dictionary = new Yadda.Dictionary();
dictionary.define('number', /(\d+/, Yadda.converters.integer);

var library = new Yadda.Library(dictionary);
library.define('Step $number', function(number) {
    // Code goes here
});
```

## The Feature Parser
Yadda's most frequent use case is for BDD testing, where instead of arrays of strings users want to supply feature specifications. The FeatureParser converts text-based feature specifications into a feature object, whose scenarios and steps can be iterated over and passed to the interpreter.
```js
var Yadda = Yadda.createInstance(library);
var specification = fs.readLineSync('path/to/feature.spec');
var feature = new Yadda.parsers.FeatureParser().parse(specification);

console.log(feature.title);
feature.scenarios.forEach(function(scenario) {
    console.log(scenario.title);
    yadda.run(scenario);
});

## Integration With Framework X
Yadda includes various plugins and examples which help you run BDD tests from your test framework of choice. There are also several open source projects built on top of Yadda making it easier to use. See the [Getting Started](../getting-started) section for more details.



