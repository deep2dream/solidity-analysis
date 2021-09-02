### Playground
- https://soliditylang.org/
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
- [uint256 value; is cheaper than uint256 value = 0;](https://medium.com/coinmonks/gas-optimization-in-solidity-part-i-variables-9d5775e43dde)
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
