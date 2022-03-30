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
1. Re-Entrancy
2. Arithmetic Over/Under Flows
3. Unexpected Ether
4. Delegatecall
5. Default Visibilities
6. Entropy Illusion
7. External Contract Referencing
8. Short Address/Parameter Attack
9. Unchecked CALL Return Values
10. Race Conditions / Front Running
11. Denial Of Service (DOS)
12. Block Timestamp Manipulation
13. Constructors with Care
14. Uninitialised Storage Pointers
15. Floating Points and Numerical Precision
16. tx.origin Authentication
