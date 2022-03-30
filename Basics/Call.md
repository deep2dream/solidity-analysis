- https://docs.soliditylang.org/en/v0.5.4/units-and-global-variables.html#members-of-address-types

instruction|expl.
--|---
```<address>.call(bytes memory) returns (bool, bytes memory)```|issue low-level **CALL** with the given payload, returns success condition and return data, forwards all available gas, adjustable
```<address>.delegatecall(bytes memory) returns (bool, bytes memory)```|issue low-level **DELEGATECALL** with the given payload, returns success condition and return data, forwards all available gas, adjustable
```<address>.staticcall(bytes memory) returns (bool, bytes memory)```|issue low-level **STATICCALL** with the given payload, returns success condition and return data, forwards all available gas, adjustable