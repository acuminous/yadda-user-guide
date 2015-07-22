# Example Tables
```
Scenario: Some title

    Given the current year is 2015
    And [First Name] [Last Name] is [Age]
    Then [First Name] [Last Name]'s year of bith is [Year Of Birth]

Examples:

    | First Name | Last Name | Age | Year Of Birth |
    | John       | Smith     | 41  | 1974          |
@Pending
    | Joe        | Bloggs    | 23  | 1992          |
```
- Example tables cause the assocated scenario to be cloned once for each row in the table.
- Columns are demarcated by the pipe (|) or box drawing (┆) characters.
- Rows support annotations.
- The outer borders are optional.
- Values are left trimmed to the position of the column heading and right trimmed.
- ```Where:``` can be used instead of ```Examples:```

## Multiline Example Tables
```
Scenario: Some title

    The poem [Name]
    Has [Verses] verses
    And [Lines] lines

Examples:

    | Name                    | Verses | Lines | Poem                              |
    |-------------------------|--------|-------|-----------------------------------|
    | Good Times              | 2      | 8     | May we go our separate ways       |
    |                         |        |       | Finding fortune and new friends   |
    |                         |        |       | But let us not forget these days  |
    |                         |        |       | Or let the good times ever end    |
    |                         |        |       |                                   |
    |                         |        |       | A poet with wiser words than mine |
    |                         |        |       | Wrote that nothing gold can stay  |
    |                         |        |       | These are golden days we're in    |
    |                         |        |       | And so are bound to fade away     |
    |-------------------------|--------|-------------------------------------------|
@Pending
    | Ode To British Rail     | 1      | 8     | Should the not so British Rail    |
    |                         |        |       | On occaision come to fail         |
    |                         |        |       | Or the speed of locomotion        |
    |                         |        |       | Be reduced to that of snail       |
    |                         |        |       | Keep a sturdy upper lip           |
    |                         |        |       | In the form you know is true      |
    |                         |        |       | And relieving your frustration    |
    |                         |        |       | By shoving bog roll down the loo  |
```
- Multiline example tables are identified by a horizontal columns separators, starting with an optional column separator followed by three or more dashes.

### Example Tables Meta Data
Yadda decorates the example table with some extra fields, which can be accessed from your steps in the normal way.
```
Scenario: [case] Scenario

    Given I need to transpile [case]
    [EcmaScript6.index] When EcmaScript6 at [EcmaScript6.start.line]:[EcmaScript6.start.column]=[EcmaScript6]
    [EcmaScript5.index] Then EcmaScript5 at [EcmaScript5.start.line]:[EcmaScript5.start.column]=[EcmaScript5]

Where:
    case             | EcmaScript6              | EcmaScript5
    -----------------|--------------------------|-------------------------------
    arrow function   | var r=arr.map((x)=>x*x); | "use strict";
                     |                          |
                     |                          | var r = arr.map(function (x) {
                     |                          |   return x * x;
                     |                          | });
    -----------------|--------------------------|-------------------------------
    template strings | var s=`x=${x}            | "use strict";
                     | y=${y}`;                 |
                     |                          | var s = "x=" + x + "\ny=" + y;
```


