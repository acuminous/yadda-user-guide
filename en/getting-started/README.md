# Getting Started

Yadda's job is translate arrays of text (often called steps) into a function call.

```js
    var Yadda = require('yadda');
    var steps = [
        'Step 1',
        'Step 2',
        'Step 3'
    ];

    var library = new Yadda.Library()
        .define(/Step (\d+)/, function(number) {
            console.log('Step', number);
        });

    Yadda.createInstance(library).run(steps);
```

Running the above from a [Node.js](https://nodejs.org/) shell (after installing Yadda) is the minimum it takes to get Yadda working, however to get the most out of Yadda you should integrate it with a test framework such as [Mocha](http://visionmedia.github.io/mocha/).
