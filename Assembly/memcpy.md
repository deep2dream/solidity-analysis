```solidity
function memcpy(uint dest, uint src, uint len) pure private {
    // Full 32 byte words
    for(; len >= 32; len -= 32) {
        assembly { mstore(dest, mload(src)) }
        dest += 32; src += 32;
    }

    // Remaining bytes
    uint mask = 256 ** (32 - len) - 1;
    assembly {
        let srcpart := and(mload(src), not(mask))
        let destpart := and(mload(dest), mask)
        mstore(dest, or(destpart, srcpart))
    }
}
```