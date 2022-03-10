```solidity
// Helper to check the placeBet receipt. "offset" is the location of the proof beginning in the calldata.
// RLP layout: [triePath, str([status, cumGasUsed, bloomFilter, [[address, [topics], data]])]
function requireCorrectReceipt(uint offset) view private {
    uint leafHeaderByte; assembly { leafHeaderByte := byte(0, calldataload(offset)) }

    require (leafHeaderByte >= 0xf7, "Receipt leaf longer than 55 bytes.");
    offset += leafHeaderByte - 0xf6;

    uint pathHeaderByte; assembly { pathHeaderByte := byte(0, calldataload(offset)) }

    if (pathHeaderByte <= 0x7f) {
        offset += 1;

    } else {
        require (pathHeaderByte >= 0x80 && pathHeaderByte <= 0xb7, "Path is an RLP string.");
        offset += pathHeaderByte - 0x7f;
    }

    uint receiptStringHeaderByte; assembly { receiptStringHeaderByte := byte(0, calldataload(offset)) }
    require (receiptStringHeaderByte == 0xb9, "Receipt string is always at least 256 bytes long, but less than 64k.");
    offset += 3;

    uint receiptHeaderByte; assembly { receiptHeaderByte := byte(0, calldataload(offset)) }
    require (receiptHeaderByte == 0xf9, "Receipt is always at least 256 bytes long, but less than 64k.");
    offset += 3;

    uint statusByte; assembly { statusByte := byte(0, calldataload(offset)) }
    require (statusByte == 0x1, "Status should be success.");
    offset += 1;

    uint cumGasHeaderByte; assembly { cumGasHeaderByte := byte(0, calldataload(offset)) }
    if (cumGasHeaderByte <= 0x7f) {
        offset += 1;

    } else {
        require (cumGasHeaderByte >= 0x80 && cumGasHeaderByte <= 0xb7, "Cumulative gas is an RLP string.");
        offset += cumGasHeaderByte - 0x7f;
    }

    uint bloomHeaderByte; assembly { bloomHeaderByte := byte(0, calldataload(offset)) }
    require (bloomHeaderByte == 0xb9, "Bloom filter is always 256 bytes long.");
    offset += 256 + 3;

    uint logsListHeaderByte; assembly { logsListHeaderByte := byte(0, calldataload(offset)) }
    require (logsListHeaderByte == 0xf8, "Logs list is less than 256 bytes long.");
    offset += 2;

    uint logEntryHeaderByte; assembly { logEntryHeaderByte := byte(0, calldataload(offset)) }
    require (logEntryHeaderByte == 0xf8, "Log entry is less than 256 bytes long.");
    offset += 2;

    uint addressHeaderByte; assembly { addressHeaderByte := byte(0, calldataload(offset)) }
    require (addressHeaderByte == 0x94, "Address is 20 bytes long.");

    uint logAddress; assembly { logAddress := and(calldataload(sub(offset, 11)), 0xffffffffffffffffffffffffffffffffffffffff) }
    require (logAddress == addr2uint(address(this)));
}
```