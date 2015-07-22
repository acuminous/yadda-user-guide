## Feature Specifications

```
Feature: 100 Green Bottles

Background:

   Given a 6ft wall
   With a healthy amount of moss

Scenario: Bottles should fall from the wall

   Given 100 green bottles are standing on the wall
   When 1 green bottles accidentally falls
   Then there are 99 green bottles standing on the wall

@Pending
Scenario: Plastic bottles should not break

   Given 100 plastic bottles are standing on the wall
   When 1 plastic bottles accidentally falls
   It does not break
```

While Yadda can interpret any text you write steps for, it also comes with a Gherkin-like feature specification parser, which supports backgrounds, annotations, multiline steps and example tables. The above feature specification parses to the following structure...

```js
{
    title: '100 Green Bottles',
    scenarios: [
        {
            annotations: {},
            title: 'Bottles should fall from the wall',
            steps: [
                'Given a 6ft wall',
                'With a healthy amount of moss',
                'Given 100 green bottles are standing on the wall',
                'When 1 green bottles accidentally falls',
                'Then there are 99 green bottles standing on the wall'
            ]
        },
        {
            annotations: { pending: true },
            title: 'Plastic bottles should not break',
            steps: [
                'Given a 6ft wall',
                'With a healthy amount of moss',
                'Given 100 plastic bottles are standing on the wall',
                'When 1 plastic bottles accidentally falls',
                'It does not break'
            ]
        }
    ]
}
```
See the [examples](https://github.com/acuminous/yadda/tree/master/examples) for how to parse and execute the feature specification natively or using one of Yaddas plugins.

