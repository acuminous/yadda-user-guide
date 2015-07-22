# Events
Debugging BDD tests is typically harder than debugging unit tests for a number of reasons, not the least of which is because you can't step through a feature file. You can make things a bit easier by adding event listeners, which log the step that is being executed.

```js
var EventBus = require('Yadda').EventBus;
EventBus.instance().on(EventBus.ON_EXECUTE, function(event) {
    console.log(event.name, event.data);
});

```
The following events are available...
<table>
  <tr>
    <th>Event Name</th><th>Event Data</th>
  </tr>
  <tr>
    <td>ON_SCENARIO</td><td>{ scenario: [ '100 green bottles', 'should 1 green bottle...', ...], ctx: context }</td>
  </tr>
  <tr>
    <td>ON_STEP</td><td>{ step: '100 green bottles...', ctx: context }</td>
  </tr>
  <tr>
    <td>ON_EXECUTE</td><td>{ step: '100 green bottles...', pattern: '/(\d+) green bottles.../', args: ['100'], ctx: context }</td>
  </tr>
</table>