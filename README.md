* [ ] *Basics - Grammar*
* [ ] *Environment Setup*
* [ ] *Modules*
* [ ] *TestCases*
* [ ] *+Frontend*
# Secure & Cheap
### Tools
*Solidity is a simple programming language. But it is supported by mountains of beautiful assisting tools. Maybe it's simplicity makes that possible. You can boost up your programming using those tools. You will be impressed by effectiveness they brings.*
Type|Func.
-----|---
**VS Extensions**
solidity|
Solidity Debugger|funcSigs
Solidity Visual Developer|diagram(call graph),uml
Solidity Contract Flattener|
**Auditing**
### Syntax
ch.|solidity|javascript
---|--------|-----
pragma|```pragma solidity ^0.4.16;```
**types**|
boolean|bool
int|// 8,16,32,64,128,256
uint(uint256)|// 8,16,32,64,128,256<br>// definition<br>``` uint public amount;```
address|***//tx -> contract***<br>```msg.sender```<br><br>// contract address to receiver<br>```receiver.transfer(amount);```|
array|```bytes32[] proposalNames;```
struct|```contract ContractName {}```|
**modifiers**|*modifier onlySeller() {<br>&nbsp;&nbsp;&nbsp;require(msg.sender == seller);<br>&nbsp;&nbsp;&nbsp;_;<br>}*
public|
private|
extern|
intern|
payable|
view|
**built-in**|
require|
**event**|
**enum**|

### Playground
* [x] https://codedamn.com/online-compiler/solidity
* [ ] https://docs.soliditylang.org/en/latest/
# solidity-analysis
solidity sample codes, patterns, everything for it

```
DeFi: Blockchain + Bank(Lend, Loan)
IPFS: Blockahin + Storage
DEX:  Blockchain + Exchange(opposite-CEX)
NFT:  Blockchain + Asset(Art)
...
```
### How to Build
```
[alias]
alias solc420='function _solc420(){ docker run --rm -v `pwd`:/root ethereum/solc:0.4.20 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc420'

[build]
solc420 test.sol
```
## Metrics
### 1. [Cost/Gas Optimization](https://mudit.blog/solidity-gas-optimization-tips/)
- [Smaller Calculations, the Better](https://mudit.blog/solidity-gas-optimization-tips/)
- [```uint256 value;``` is cheaper than ```uint256 value = 0;```](https://medium.com/coinmonks/gas-optimization-in-solidity-part-i-variables-9d5775e43dde)
- [```f(uint128, uint128, uint256)``` better than ```f(uint128, uint256, uint128)```](https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html#layout-of-state-variables-in-storage)
- Public vs. External: External functions cheaper than public functions.
- Global vs. Local: global/storage/member variables are more expensive than function variables.
- uint8 is not cheaper than unit256
- Packing variables lower costs.
- ...
### 2. Security/Vulnerability
- Re-Entrancy
- Arithmetic Over/Under Flows
- Unexpected Ether
- Delegatecall
- Floating Points and Precision
- ...
## ToolChains
- Remix
- Truffle
- Ganache
- HardHat
## Use Cases
### NFT
keywords: authenticity, royalty
- NFT
- NFT wallet
- NFT marketplace
- NFT lending platfrom

ERC20 | ERC721
------|------
mapping(address => uint256) | tokenURI,tokenId, MetaData

### DeFi
