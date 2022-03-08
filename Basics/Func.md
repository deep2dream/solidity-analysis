Type|Usages
----|----
```default```|```function f(address addr) returns (uint) {}```
```fallback```|*```fallback() external payable {}```<br><br>It is called **when a non-existent function is called** on the contract.<br>It is required to be marked **external**.<br>It has no name, no arguments.<br>It can not return any thing.<br>It can be defined **one per contract**.<br>If not marked **payable**, it will throw exception if contract receives plain ether without data.*
## Q & A
Q|A
-----|------
```function f(){} vs. function _f(){}```|