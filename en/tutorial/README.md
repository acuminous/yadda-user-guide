## Tutorial
Yadda's job is translate lines of text into a function call.

    var Yadda = require('yadda');
    var library = new Yadda.Library().define('Some text', function() {
        console.log('Hello World');
    });
    Yadda.createInstance(library).run('Some text');


Running the above from a [Node.js](https://nodejs.org/) shell (after installing Yadda) is the minimum it takes to get Yadda working. However since most people want to use Yadda for automated testing this tutorial demonstrates Yadda with [Node.js](https://nodejs.org/) and [Mocha](http://visionmedia.github.io/mocha/). If you prefer another test runner, see the [examples](https://github.com/acuminous/yadda/tree/master/examples).

### Start a new node project

    mkdir yadda-tutorial
    cd yadda-tutorial
    npm init
    npm i --save-dev yadda mocha

### Create a test directory structure

    mkdir -p test/features test/steps

### Write a feature specification

    Feature: 100 Green Bottles

    Scenario: Should fall from the wall

       Given 100 green bottles are standing on the wall
       When 1 green bottle accidentally falls
       Then there are 99 green bottles standing on the wall

Save it in ```test/features/bottles.feature```

### Implement the steps library

    var assert = require('assert');
    var English = require('yadda').localisation.English;
    var Wall = require('../..'); // The library that you wish to test

    module.exports = English.library()
        .given("$NUM green bottles are standing on the wall", function(number, next) {
            wall = new Wall(number);
            next();
        })
        .when("$NUM green bottle accidentally falls", function(number, next) {
            wall.fall(number);
            next();
        })
        .then("there are $NUM green bottles standing on the wall", function(number, next) {
            assert.equal(number, wall.bottles);
            next();
        });

Save it in ```test/steps/bottles-library.js```. If your test runner & code are synchronous you can omit calls to 'next'.

### Integrate Yadda with Mocha

    var Yadda = require('yadda');
    Yadda.plugins.mocha.StepLevelPlugin.init();

    new Yadda.FeatureFileSearch('./test/features').each(function(file) {

        featureFile(file, function(feature) {

            var library = require('./test/steps/bottles-library');
            var yadda = Yadda.createInstance(library);

            scenarios(feature.scenarios, function(scenario) {
                steps(scenario.steps, function(step, done) {
                    yadda.run(step, done);
                });
            });
        });
    });

### Write the code under test

    module.exports = function(bottles) {
        this.bottles = bottles;
            this.fall = function(n) {
            this.bottles -= n;
        }
    };

Save it in ```./index.js```. By now your project should have the following layout.

    .
    ├── index.js
    ├── package.json
    └── test
        ├── features
        │   └── bottles.feature
        ├── steps
        │   └── bottles-library.js
        └── test.js

### Run your tests

    mocha --reporter spec test.js

    100 Green Bottles
    Should fall from the wall
      ✓ Given 100 green bottles are standing on the wall
      ✓ When 1 green bottle accidentally falls
      ✓ Then there are 99 green bottles standing on the wall

