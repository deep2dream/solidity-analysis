- https://docs.soliditylang.org/en/v0.5.4/units-and-global-variables.html#error-handling

instruction|expl.
--|---
```assert(bool condition)```|causes an invalid opcode and thus state change reversion if the condition is not met - to be used **for internal errors**.
```require(bool condition)```|reverts if the condition is not met - to be used **for errors in inputs or external components**.
```require(bool condition, string memory message)```|reverts if the condition is not met - to be used **for errors in inputs or external components**. Also provides an error message.
```revert()```|abort execution and revert state changes
```revert(string memory reason)```|abort execution and revert state changes, **providing an explanatory string**