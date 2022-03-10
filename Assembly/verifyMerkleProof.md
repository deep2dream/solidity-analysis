```solidity
// Helper to verify a full merkle proof starting from some seedHash (usually commit). "offset" is the location of the proof
// beginning in the calldata.
function verifyMerkleProof(uint seedHash, uint offset) pure private returns (bytes32 blockHash, bytes32 uncleHash) {
    // (Safe) assumption - nobody will write into RAM during this method invocation.
    uint scratchBuf1;  assembly { scratchBuf1 := mload(0x40) }

    uint uncleHeaderLength; uint blobLength; uint shift; uint hashSlot;

    // Verify merkle proofs up to uncle block header. Calldata layout is:
    //  - 2 byte big-endian slice length
    //  - 2 byte big-endian offset to the beginning of previous slice hash within the current slice (should be zeroed)
    //  - followed by the current slice verbatim
    for (;; offset += blobLength) {
        assembly { blobLength := and(calldataload(sub(offset, 30)), 0xffff) }
        if (blobLength == 0) {
            // Zero slice length marks the end of uncle proof.
            break;
        }

        assembly { shift := and(calldataload(sub(offset, 28)), 0xffff) }
        require (shift + 32 <= blobLength, "Shift bounds check.");

        offset += 4;
        assembly { hashSlot := calldataload(add(offset, shift)) }
        require (hashSlot == 0, "Non-empty hash slot.");

        assembly {
            calldatacopy(scratchBuf1, offset, blobLength)
            mstore(add(scratchBuf1, shift), seedHash)
            seedHash := keccak256(scratchBuf1, blobLength)
            uncleHeaderLength := blobLength
        }
    }

    // At this moment the uncle hash is known.
    uncleHash = bytes32(seedHash);

    // Construct the uncle list of a canonical block.
    uint scratchBuf2 = scratchBuf1 + uncleHeaderLength;
    uint unclesLength; assembly { unclesLength := and(calldataload(sub(offset, 28)), 0xffff) }
    uint unclesShift;  assembly { unclesShift := and(calldataload(sub(offset, 26)), 0xffff) }
    require (unclesShift + uncleHeaderLength <= unclesLength, "Shift bounds check.");

    offset += 6;
    assembly { calldatacopy(scratchBuf2, offset, unclesLength) }
    memcpy(scratchBuf2 + unclesShift, scratchBuf1, uncleHeaderLength);

    assembly { seedHash := keccak256(scratchBuf2, unclesLength) }

    offset += unclesLength;

    // Verify the canonical block header using the computed sha3Uncles.
    assembly {
        blobLength := and(calldataload(sub(offset, 30)), 0xffff)
        shift := and(calldataload(sub(offset, 28)), 0xffff)
    }
    require (shift + 32 <= blobLength, "Shift bounds check.");

    offset += 4;
    assembly { hashSlot := calldataload(add(offset, shift)) }
    require (hashSlot == 0, "Non-empty hash slot.");

    assembly {
        calldatacopy(scratchBuf1, offset, blobLength)
        mstore(add(scratchBuf1, shift), seedHash)

        // At this moment the canonical block hash is known.
        blockHash := keccak256(scratchBuf1, blobLength)
    }
}
```