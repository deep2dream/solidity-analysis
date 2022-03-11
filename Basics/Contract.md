- destroy the current contract, sending its funds to the given Address

instruction|expl.
--|---
```this```|*the current contract, explicitly convertible to Address*
```selfdestruct(address payable recipient)```|*destroy the current contract, sending its funds to the given Address*
```type(C).creationCode:```|
```type(C).runtimeCode:```
```address(this).balance```|