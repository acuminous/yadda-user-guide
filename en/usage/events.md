# Events
Debugging BDD tests is typically harder than debugging unit tests for a number of reasons, not the least of which is because you can't step through a feature file. You can make things a bit easier by adding event listeners, which log the step that is being executed.

```js
var EventBus = require('Yadda').EventBus;
EventBus.instance().on(EventBus.ON_EXECUTE, function(event) {
    console.log(event.name, event.data);
});

```
#### ON_SCENARIO
Fired when the interpreter is about to process a scenario
```
{
  scenario: [
    '100 green bottles',
    'should 1 green bottle...'
  ],
  ctx: context
}```
#### ON_STEP
Fired when the interpreter is about to process a step
```
{
  step: '100 green bottles...',
  ctx: context
}
```
#### ON_EXECUTE
Fired when the interpreter is about to execute the function associated with a step
```js
{
  step: '100 green bottles...',
  pattern: '/(\d+) green bottles.../',
  args: [
    '100'
  ],
  ctx: context
}
```