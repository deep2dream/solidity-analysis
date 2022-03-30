- assembly coding using opcode
- using builtin/yul optimizer
- less access(write/read) to state variables, never use it in loop
- use constants and immutables
- Variable packing/order of variables matters (```uint128```,```uint128```,```uint256``` vs. ```uint128```,```uint256```,```uint128```)
- fixed size rather than unfixed size(```bytes32``` instead of ```string``` / ```bytes```,bytesN instead of bytes[])
- use uint256 instead of uint8
- freeup unused storage using ```delete <variable-name>```

## https://yos.io/2021/05/17/gas-efficient-solidity/
## https://ethereum.stackexchange.com/questions/28813/how-to-write-an-optimized-gas-cost-smart-contract
Operation |        Gas  |         Description
-|-|-
ADD/SUB |          3             |Arithmetic operation
MUL/DIV    |       5             |Arithmetic operation
ADDMOD/MULMOD |    8             |Arithmetic operation
AND/OR/XOR    |    3             |Bitwise logic operation
LT/GT/SLT/SGT/EQ | 3             |Comparison operation
POP           |    2             |Stack operation 
PUSH/DUP/SWAP  |   3             |Stack operation
MLOAD/MSTORE  |    3             |Memory operation
JUMP        |      8             |Unconditional jump
JUMPI      |       10            |Conditional jump
SLOAD     |        200           |Storage operation
SSTORE    |        5,000/20,000  |Storage operation
BALANCE  |         400           |Get balance of an account
CREATE   |         32,000        |Create a new account using CREATE
CALL     |         25,000        |Create a new account using CALL

## https://github.com/djrtwo/evm-opcode-gas-costs/blob/master/opcode-gas-costs_EIP-150_revision-1e18248_2017-04-12.csv
- https://docs.google.com/spreadsheets/d/1m89CVujrQe5LAFJ8-YAUCcNK950dUzMQPMJBxRtGCqs/edit#gid=0
- https://github.com/deep2essence/evm-opcode-gas-costs

## https://betterprogramming.pub/15-tips-to-write-better-smart-contracts-abba3e94ddf2
## https://medium.com/joyso/solidity-save-gas-in-smart-contract-3d9f20626ea4
## https://eip2535diamonds.substack.com/p/how-eip2535-diamonds-reduces-gas?s=r
## https://eip2535diamonds.substack.com/p/smart-contract-gas-optimization-with?s=r