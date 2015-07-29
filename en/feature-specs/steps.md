# Steps

## Single Line Steps

```
Scenario: Some title

    Given some precondition
    And another precondition
    When I do something
    Then expect some side effect
    However some other side effect should not occur
```
- Steps do not have to start with Given, When, Then, And or But.
- Steps are trimmed (both right and left).
- Steps do not support annotations.
- Implement steps using Yadda [step libraries](../usage/step-libraries.md) and [dictionaries](../usages/dictionaries.md)


## Multiline Steps
```
Scenario: Some title

    Given a poem
    --------------
    The Loss of the Dredger
    A stormy night, with lashing waves,
    To send the sailors to their graves.
    The howling wind brings mist and fog,
    The captain notes this in his log.
    --------------
    Then expect the poem to have one verse and four lines.
```
- Multiline steps must be preceded by a "leading" single line step, e.g. 'Given a poem'. This is because the contents of the multiline step is appended to the "leading" step, separated with a line break (\n).
- Multiline steps are demarcated by three or more consecutive dashes.
- If the mutiline step is the last step in the scenario, the terminating dashed line is optional.
- Multiline steps are left trimmed to start of the dashed line and right trimmed.

## Structured Multiline Steps
```
Scenario: Some title

    Given some csv
    --------------
    First Name,Last Name,Age
    Joe,Bloggs,23
    John,Smith,41
    --------------
    Then expect Joe to be younger than John
```
Multiline steps can contain structured data such as tables, csv, xml and json, you only need to write a  [converter](../usage/dictionaries.md#converters).


