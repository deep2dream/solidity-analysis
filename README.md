### Playground
- https://soliditylang.org/
# solidity-analysis
solidity sample codes, patterns, everything for it

```
Defi: blockchain + bank function(lend, loan)
IPFS: blockahin + storage
DEX:  blockchain + Exchange(opposite-CEX)
NFT:  blockchain + Asset(Art)
...
```
### - Build
```
alias solc420='function _solc420(){ docker run --rm -v `pwd`:/root ethereum/solc:0.4.20 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc420'
alias solc510='function _solc510(){ docker run --rm -v `pwd`:/root ethereum/solc:0.5.10 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc510'
alias solc425='function _solc425(){ docker run --rm -v `pwd`:/root ethereum/solc:0.4.25 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc425'
alias solc424='function _solc424(){ docker run --rm -v `pwd`:/root ethereum/solc:0.4.24 --bin --abi --optimize --overwrite /root/$1 -o /root/build; };_solc424'

```
### - [Cost/Gas Optimization](https://mudit.blog/solidity-gas-optimization-tips/)
- [Smaller Calculations, the Better](https://mudit.blog/solidity-gas-optimization-tips/)
- [uint256 value; is cheaper than uint256 value = 0;](https://medium.com/coinmonks/gas-optimization-in-solidity-part-i-variables-9d5775e43dde)
```
[public vs. external]
external function cheaper than public function.

[global vs. local]
global/storage/member variable is much more expensive than function variable.
```

### - Security/Vulnerability
- https://forum.openzeppelin.com/t/compiled-list-of-solidity-vulnerabilities/1081/5
- https://securityboulevard.com/2020/05/solidity-top-10-common-issues/
- https://miro.com/app/board/o9J_kxZnJOk=/
- https://consensys.github.io/smart-contract-best-practices/known_attacks/
- https://medium.com/hackernoon/hackpedia-16-solidity-hacks-vulnerabilities-their-fixes-and-real-world-examples-f3210eba5148

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

### Defi
