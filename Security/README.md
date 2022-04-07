- https://docs.soliditylang.org/en/latest/security-considerations.html#security-considerations
- https://github.com/guylando/KnowledgeLists/blob/master/EthereumSmartContracts.md
- https://consensys.github.io/smart-contract-best-practices/
- https://docs.soliditylang.org/en/latest/smtchecker.html
- https://101blockchains.com/solidity-issues/
- https://blog.sigmaprime.io/solidity-security.html
- https://solidity-by-example.org/

### Patterns
Pattern|Expl.|Preventative Tech.
---|--------|---
Privateness|All data on blockchain is public, even private marked variables
Randomness|?
Re-Entrancy|using fallback function to call withdraw recursively|using mutex
Gas Limit and Loops|
Sending and Receiving Ether|
Call Stack Depth|
Authorized Proxies|
tx.origin|```tx.origin```!=```msg.sender```
```Two’s Complement/Underflows/Overflows```|1.```unchecked { ... }```<br>2.use require to limit the size of inputs to a reasonable range<br>3.use the SMT checker with ```pragma experimental SMTChecker;```to find potential overflows
```Clearing Mappings```|
```Checks-Effects-Interactions Pattern```|
```Fail-Safe Mode```|

### https://blog.sigmaprime.io/solidity-security.html
Pattern|Expl.|Preventative Tech.
---|--------|---
Re-Entrancy
Arithmetic Over/Under Flows
Unexpected Ether
Delegatecall
Default Visibilities
Entropy Illusion
External Contract Referencing
Short Address/Parameter Attack
Unchecked CALL Return Values
Race Conditions / Front Running
Denial Of Service (DOS)
Block Timestamp Manipulation
Constructors with Care
Uninitialised Storage Pointers
Floating Points and Numerical Precision
tx.origin Authentication
