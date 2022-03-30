- https://docs.soliditylang.org/en/latest/security-considerations.html#security-considerations
- https://github.com/guylando/KnowledgeLists/blob/master/EthereumSmartContracts.md
- https://consensys.github.io/smart-contract-best-practices/
- https://docs.soliditylang.org/en/latest/smtchecker.html
### Patterns
Pattern|Expl.
---|----
Privateness|All data on blockchain is public, even private marked variables
Randomness|?
Re-Entrancy|
Gas Limit and Loops|
Sending and Receiving Ether|
Call Stack Depth|
Authorized Proxies|
tx.origin|```tx.origin```!=```msg.sender```
```Two’s Complement/Underflows/Overflows```|1.```unchecked { ... }```<br>2.use require to limit the size of inputs to a reasonable range<br>3.use the SMT checker with ```pragma experimental SMTChecker;```to find potential overflows
```Clearing Mappings```|
```Checks-Effects-Interactions Pattern```|
```Fail-Safe Mode```|