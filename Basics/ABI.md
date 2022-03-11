- https://docs.soliditylang.org/en/v0.5.4/units-and-global-variables.html#abi-encoding-and-decoding-functions
- https://docs.soliditylang.org/en/latest/abi-spec.html#abi
instruction|expl.
--|---
```abi.decode(bytes memory encodedData, (...)) returns (...)```| ABI-decodes the given data, while the types are given in parentheses as second argument. Example- ```(uint a, uint[2] memory b, bytes memory c) = abi.decode(data, (uint, uint[2], bytes))```
```abi.encode(...) returns (bytes memory)```| ABI-encodes the given arguments
```abi.encodePacked(...) returns (bytes memory)```| Performs packed encoding of the given arguments. Note that packed encoding can be ambiguous!
```abi.encodeWithSelector(bytes4 selector, ...) returns (bytes memory)```| ABI-encodes the given arguments starting from the second and prepends the given four-byte selector
```abi.encodeWithSignature(string memory signature, ...) returns (bytes memory)```| Equivalent to ```abi.encodeWithSelector(bytes4(keccak256(bytes(signature))), ...)```
