# Contributing

We're delighted to accept pull requests, but would also like to keep the Yadda code base consistent with the following principles and conventions. Feel free to ignore them (especially if you're fixing a bug), but don't be offended if your code gets re-written before it's merged.

### Doing One Thing (Well)
An application should do one thing well. Yadda's "one thing" is to map lines of text to function calls. It's not a test runner, or a test framework, but should be able to integrate with other tools easily. It shouldn't have a ridged "Given, When, Then" syntax either.

### Feature Improvements
Before working on an improvement, consider creating an issue for it. It may be something I (or another contributor) has already given thought to and can help with.

### Zero Dependencies
I don't want to force Yadda's user base to install underscore/lo-dash or async, so even though I like these libraries and would love to use them in the Yadda code base I've resisted.

### Very Small Functions
The average size of a function in the Yadda codebase is around 2.5 lines, I'd like to keep it this way.

### Else considered harmful
I don't mind guard conditions (an if statement near the top of a function that returns immediately or throws an exception), but try very hard to avoid else or switch statements. They are typically hiding a fork in behaviour that is probably better handled with polymorphism. Yadda only has one else statement in the whole codebase.

### Booleans make bad parameters
Passing booleans as parameters leads to else statements. Else statements are bad. Use polymorphism instead.

### Avoid Inheritance
I prefer composition, mixins or duck typing to classic Java style inheritance hierarchies.

### Encapsulate, encapsulate, encapsulate
Did you know that the NASA Mars Climate Orbiter disintegrated because they didn't encapsulate quantities? The system on the ground sent thrust instructions in pound-seconds, but the flight system on the orbiter expected them in newton-seconds. When your software leaks primitives bad things happen. Please keep your behaviour and data as private as possible.

### No Comment
The only valid reason for comments is to explain why confusing code cannot be simplified - maybe you're working around a bug in a 3rd party library or implementing a naturally complicated algorithm (e.g. [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance). If you use comments to explain code for some other reason, then instead of writing the comment, take the time to simplify the code.

### Automated Tests
Yadda's code base is pretty well tested and will continue to be so.

### Syntax
I wrote Yadda just after completing a Ruby course. Hence why the syntax_follows_ruby_coding_conventions more closely than it does JavaScripts. Probably a mistake, but I'd like to keep the code base looking consistent.

