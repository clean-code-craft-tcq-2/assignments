# Test-driven extensions

Make these extensions on your existing repository. By separating the extension, you can always write tests for an extension of functionality.

Make sure you specify the responsibility of the extension. Be clear about the division of responsibilities between existing code and the extension.

## Try adding: Current-sensing at high fidelity

The current-sensor has a 12-bit A2D converter. The sensor is capable of sensing a maximum temperature of 10 Amps.
A reading of 0 means 0A and a reading of 4094 means 10 Amps.
The readings in-between are linearly scaled.

A reading of 4095 indicates an error.

Your program needs to be compatible with 12-bit input. Assume that the 12-bit numbers are transmitted as an array of integers (_no_ bit-level packing).

### Test driven development

>Add separately, then integrate

Write separate tests for:

- ignoring error-readings
- converting the 12-bit input into Amps. Round-off the result to the nearest integer.

Example: If the A2D reports `1146`, it is `10 Amps * 1146 / 4094 = 2.799 Amps`, which is rounded-off to the nearest integer `3`.

Implement a separate function for this conversion. Note that it's a pure function with well-defined inputs and outputs.

### Test driven integration

First, Write an end-to-end test. Supply an array of 12-bit integers and assert the expected ranges.

Then chain the new implementation to the old one, in order to pass the test.

## One more sensor

This time, the customer brings a sensor capable of detecting both charging and discharging (positive and negative) currents.
This has a 10-bit A2D (reports numbers 0 thru 1023), spanning currents from -15 Amps to +15 Amps.

A reading of 0 means -15 Amps, 1022 means +15 Amps and 511 means no current.

Note that we are only interested in the magnitude (absolute value) of the current to select circuit components, not the direction.
For example, +12 Amps and -12 Amps must be counted in the same range.
