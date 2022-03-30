## Tutorials
* [x] Scaffold(hardhat+react+graghql): https://github.com/scaffold-eth/scaffold-eth-examples
* [x] https://solidity-by-example.org/
* [ ] https://etherscan.io/accounts/c?sort=txcount&order=desc

## Plan
* [x] *Basics - Grammar*
* [x] *Environment Setup*
* [x] *Modules*
* [x] *TestCases*
* [ ] *+Frontend - React*
* [ ] *+Backend - GraphQL*
# Secure & Cheap
### Tools
*Solidity is a simple programming language. But it is supported by mountains of beautiful assisting tools. Maybe it's simplicity makes that possible. You can boost up your programming using those tools. You will be impressed by effectiveness they brings.*
Type|Func.
-----|---
**VS Extensions**
solidity|
Solidity Debugger|funcSigs
Solidity Visual Developer|diagram(call graph),uml,auditing
Solidity Contract Flattener|
**Auditing**
### Syntax
ch.|solidity|javascript
---|--------|-----
pragma|```pragma solidity ^0.4.16;```
**types**|https://docs.soliditylang.org/en/v0.5.4/abi-spec.html#types
```bool```|```uint8 == bool```
```int<M>```|```0 < M <= 256, M % 8 == 0```
```uint<M>```|```0 < M <= 256, M % 8 == 0```<br>```uint==uint256```
```bytes<M>```|```0<M<=32```
```bytes```|```byte[]
address|```uint160==address```
```fixed<M>x<N>```|```8 <= M <= 256, M % 8 ==0```,```0 < N <= 80```
```ufixed<M>x<N>```|```8 <= M <= 256, M % 8 ==0```,```0 < N <= 80```
```fixed```|```fixed128x18```
```ufixed```|```ufixed128x18```
```function```|```==bytes24(bytes4+bytes20)```,bytes4 for func.selector, bytes20 for func.address
```<type>[M]```|```fixed array```
```string```|```dynamic sized```
```(T1,T2,...,Tn)```|***tuple***```T1, …, Tn, n >= 0```
```struct```|***```tuple```***
```address payable```|```address```
**function**|*[Functions should be grouped according to their visibility and ordered:](https://docs.soliditylang.org/en/v0.8.12/style-guide.html?highlight=virtual#order-of-functions)<br>```1.constructor, 2.receive function (if exists), 3.fallback function (if exists), 4.external, 5.public, 6.internal, 7.private```<br>Within a grouping, place the view and pure functions last.*
**modifiers**|*The modifier order for a function: 1.Visibility,2.Virtual,3.Mutability,4.Override,5.Custom modifiers*
***visibility & Getter***|https://docs.soliditylang.org/en/v0.5.4/contracts.html#visibility-and-getters
public|*```part of the contract interface```can be either **called internally or via messages***
private|***only visible for the contract they are defined in** and not in derived contracts.*
external|*```part of the contract interface```<br>can be called **from other contracts and via transactions**.<br>can**not** be called **internally** (i.e. ```f()``` does **not** work, but ```this.f()``` works)<br>External functions are **sometimes more efficient when they receive large arrays of data**.*
```internal```|*can only be accessed internally (i.e. from **within the current contract** or **contracts deriving from it**), **without** using ```this```.*
***Mutability***|
```virtual```|*A function that allows an inheriting contract to override its behavior will be marked at ```virtual```<br>```abstract contract A {function spam() public virtual pure;```*
```overload```|*The function that overrides that base function should be marked as ```override```.<br>```contract B is A {function spam() public pure override {}}```*<br>```overload``` over ```virtual overload``` is possible.
***custom modifiers***|*modifier onlySeller() {<br>&nbsp;&nbsp;&nbsp;require(msg.sender == seller);<br>&nbsp;&nbsp;&nbsp;_;<br>}*
**built-in**|
require|
**event**|
**enum**|

### Playground
* [x] https://codedamn.com/online-compiler/solidity
### Tutorials
* [ ] https://docs.soliditylang.org/en/latest/
### Build
cat.|usage
---|----
```docker```|```alias solc420='function _solc420(){ docker run --rm -v `pwd`:/root ethereum/solc:0.4.20 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc420'```<br>```solc420 test.sol```
```local```|```npm install -g solc```
```online```|```use remix```

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
## [IDEs](https://docs.soliditylang.org/en/latest/resources.html)
tool|features
----|---
```Remix```|```compile```online
```Truffle```|
```Ganache```|```Standalone Node```localhost testing
```HardHat```|```develop a project - create, compile, test, deploy```
```ganache-cli + metamask```|
```ganache-cli + truffle```|

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
