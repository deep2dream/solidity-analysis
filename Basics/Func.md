Type|Usages
----|----
```default```|```function f(address addr) returns (uint) {}```
```fallback```|*```fallback() external payable {}```<br><br>It is called **when a non-existent function is called** on the contract.<br>It is required to be marked **external**.<br>It has no name, no arguments.<br>It can not return any thing.<br>It can be defined **one per contract**.<br>If not marked **payable**, it will throw exception if contract receives plain ether without data.*

## [BuiltIn](https://docs.soliditylang.org/en/v0.5.4/units-and-global-variables.html#mathematical-and-cryptographic-functions)
instruction|expl.
--|---
```addmod(uint x, uint y, uint k) returns (uint)```|compute (x + y) % k where the addition is performed with arbitrary precision and does not wrap around at 2**256. Assert that k != 0 starting from version 0.5.0.
```mulmod(uint x, uint y, uint k) returns (uint)```|compute (x * y) % k where the multiplication is **performed with arbitrary precision** and does not wrap around at 2**256. Assert that k != 0 starting from version 0.5.0.
```keccak256(bytes memory) returns (bytes32)```|compute the **Keccak-256 hash** of the input
```sha256(bytes memory) returns (bytes32)```|compute the **SHA-256** hash of the input
```ripemd160(bytes memory) returns (bytes20)```|compute **RIPEMD-160 hash** of the input
```ecrecover(bytes32 hash, uint8 v, bytes32 r, bytes32 s) returns (address)```|**recover the address** associated with the public key from elliptic curve signature or return zero on error (example usage)
## Q & A
Q|A
-----|------
```function f(){} vs. function _f(){}```|