# Extending and Refactoring

This exercise is about extending functionality.
Work on the repository from your previous assignment to extend it (see extensions below). 
Often, code becomes more complex while extending it.
The 'cleanliness' of the code goes down.

The skill of refactoring keeps the code clean and fresh.

This assignment is a continuation in the [BMS domain](bms-domain.md).

## Extensions

Try at least **two** of these extensions on your code.
Mention the extensions you select in your `README.md` file.

### Extension 1: Early Warning
Customers need _early warnings_ to take action,
in addition to the alarm that you print after the limit is breached.
Introduce a 'warning' level with a tolerance of 5% of the upper-limit.

Example: If the SoC needs to be between 20 and 80, the warning-tolerance is `5% of 80` = `4`.
Warnings need to be displayed in these ranges:
- `20` to `20+4` Warning: Approaching discharge
- `80-4` to `80` Warning: Approaching charge-peak

Same for Temperature and Charge-rate.

Keep in mind: Though we are starting with warning levels for all parameters, customers may give feedback to have warnings only for _some_ parameters and not others. Minimize the change needed for such 'tuning'.

### Extension 2: Support a language in addition to English

Our market has expanded to German-speaking countries!
Switch the language of the printed messages based on a global variable.

Use [Google translate](https://translate.google.com/?sl=en&tl=de&op=translate)
if you aren't familiar with German.

Keep in mind: We could add more languages in future. Minimize the code-change required.

### Extension 3: Accept input in different units

Some sensors report the temperature in Fahrenheit.
Make provision to express the unit along with the measurement.
Avoid repeating the limits in different units.

Keep in mind: This time it was temperature in a different unit. Later perhaps other measurements would have variations. Make it possible to **add** compatibility with additional variations, with minimal **modifications** to existing code.

## The starting point

Write a failing test. The asserts will specify the data-design (inputs and outputs). Imagine a consumer and ensure that the asserts reflect the consumer's need.

Experience the places where test / code gets more complex. Think of refactoring opportunities.

## Recommended Approach

Treat the problem as a series of data-transformations.
A chain of transformations is suggested below.

- Translate to common units

- Map the breach to the ranges. Keep the code common across parameters and vary the data.
    
    Example: Design a data-structure with a series of numbers representing the boundary of each condition.
    In the example above: 
    - `0 to 20`: `LOW_SOC_BREACH`
    - `21 to 24`: `LOW_SOC_WARNING`
    - `24 to 75`: `NORMAL`
    - `76 to 80`: `HIGH_SOC_WARNING`
    - `81 to 100`: `HIGH_SOC_BREACH`

- Translate the anomaly to a message in the appropriate language

- Output the resulting message

- Compute overall Battery status. Make logical assumptions in case of warning and error combinations.

Each transformation is one function (or more).
Do not mix different transformations in the same function.
Have one function to chain ('compose') these transformation-functions.
