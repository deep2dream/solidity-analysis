```solidity
// Assigns a new selector and address to the return variable @fun
function combineToFunctionPointer(address newAddress, uint newSelector) public pure returns (function() external fun) {
    assembly {
        fun.selector := newSelector
        fun.address  := newAddress
    }
}
```