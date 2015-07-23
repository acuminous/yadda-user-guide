# Example Tables
```
Scenario: Example Table With Outer Borders

    Given the current year is 2015
    And [First Name] [Last Name] is [Age]
    Then [First Name] [Last Name]'s year of bith is [Year Of Birth]

Where:

    ------------------------------------------------
    | First Name | Last Name | Age | Year Of Birth |
    | John       | Smith     | 41  | 1974          |
    | Joe        | Bloggs    | 23  | 1992          |
    ------------------------------------------------
```

- Columns are demarcated by the pipe (|) or box drawing (┆) characters.
- Horizontal borders start with an optional column separator and are followed by three or more dashes (-).
- The outer borders are optional.
- Example tables must contain a single header row.
- There must be no horizontal border after the header row (this will be interpreted as a multiline example table).
- Each data row will be used to generate a new scenario.
- Values are left trimmed to the position of the column heading. All trailing whitespace is removed.
- ```Where:``` and ```Examples:``` are interchangable

## Multiline Example Tables
```
Scenario: Multiline Example Table With Outer Borders

    The poem [Name]
    Has [Verses] verses
    And [Lines] lines

Where:

    --------------------------------------------------------------------------------
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
    |-------------------------|--------|-------|-----------------------------------|
    | Ode To British Rail     | 1      | 8     | Should the not so British Rail    |
    |                         |        |       | On occaision come to fail         |
    |                         |        |       | Or the speed of locomotion        |
    |                         |        |       | Be reduced to that of snail       |
    |                         |        |       | Keep a sturdy upper lip           |
    |                         |        |       | In the form you know is true      |
    |                         |        |       | And relieving your frustration    |
    |                         |        |       | By shoving bog roll down the loo  |
    --------------------------------------------------------------------------------
```
- Columns are demarcated by the pipe (|) or box drawing (┆) characters.
- Horizontal borders start with an optional column separator and are followed by three or more dashes (-).
- The outer borders are optional.
- Example tables must contain a single header row.
- Multiline example tables must have a horizontal border after the header row.
- Data rows are demarcated by horizontal borders
- Each data row will be used to generate a new scenario.

### Annotations
Both single and multiple example table data rows support annotations

```
Where:

    ------------------------------------------------
    | First Name | Last Name | Age | Year Of Birth |
    | John       | Smith     | 41  | 1974          |
@Pending
    | Joe        | Bloggs    | 23  | 1992          |
    ------------------------------------------------
```
or

```
Where:

    --------------------------------------------------------------------------------
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
    |-------------------------|--------|-------|-----------------------------------|
@Pending
    | Ode To British Rail     | 1      | 8     | Should the not so British Rail    |
    |                         |        |       | On occaision come to fail         |
    |                         |        |       | Or the speed of locomotion        |
    |                         |        |       | Be reduced to that of snail       |
    |                         |        |       | Keep a sturdy upper lip           |
    |                         |        |       | In the form you know is true      |
    |                         |        |       | And relieving your frustration    |
    |                         |        |       | By shoving bog roll down the loo  |
    --------------------------------------------------------------------------------
```

### Example Tables Meta Data
Yadda decorates example tables with some extra fields (<name>.index, <name>.start.line and <name>.start.column), which can be accessed from your steps in the normal way.
```
Scenario: [case] Scenario

    Given I need to transpile [case]
    [EcmaScript6.index] When EcmaScript6 at [EcmaScript6.start.line]:[EcmaScript6.start.column]=[EcmaScript6]
    [EcmaScript5.index] Then EcmaScript5 at [EcmaScript5.start.line]:[EcmaScript5.start.column]=[EcmaScript5]

Where:
    --------------------------------------------------------------------------------
    | case             | EcmaScript6              | EcmaScript5                    |
    |------------------|--------------------------|---------------------------------
    | arrow function   | var r=arr.map((x)=>x*x); | "use strict";                  |
    |                  |                          |                                |
    |                  |                          | var r = arr.map(function (x) { |
    |                  |                          |   return x * x;                |
    |                  |                          | });                            |
    |------------------|--------------------------|--------------------------------|
    | template strings | var s=`x=${x}            | "use strict";                  |
    |                  | y=${y}`;                 |                                |
    |                  |                          | var s = "x=" + x + "\ny=" + y; |
    --------------------------------------------------------------------------------
```


