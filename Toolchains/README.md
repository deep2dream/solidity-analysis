## ethereum node apis
api|trait
---|---
```alchemy```|```https://eth-ropsten.alchemyapi.io/v2/7mX5......RAIP```
```infura```|```https://mainnet.infura.io/v3/9aa3d95b3bc440fa88ea12eaa4456161```
```etherscan```|

# toolchains
tool|guide
----|-----
```nvm```|```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh \| bash```<br>```nvm install 12.18.1```
```ganache-cli```|***standalone node** for simulation<br>**installation:**```npm install -g ganache-cli```<br>**run:**```ganache-cli```*
```web3.js```|```npm install web3```or```yarn add web3```or```npm install ethereum/web3.js --save```
[```solidity(vscode extention)```](https://marketplace.visualstudio.com/items?itemName=JuanBlanco.solidity&ssr=false#overview)|
[```metamask(chrome extention)```](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn)|
```ganache-cli & metamask```|```chainid(default):1337```, but you can set its chainid manually when it's starting like this. ```ganache-cli -f <YourNODE> --chainId <newNumber>```
[```openzeppelin```](https://docs.openzeppelin.com/cli/)|```npm install @openzeppelin/contracts```
[hardhat](https://hardhat.org/hardhat-network/)|```npm install --save-dev hardhat@2.4.3```
[```truffle```](https://www.trufflesuite.com/docs/ganache/overview)|```npm install -g truffle```
[```remix```](https://remix-ide.readthedocs.io/en/latest/file_explorer.html)
***Check.vulnerability***
[diligence](https://consensys.net/diligence/tools/)|
[mythril](https://github.com/ConsenSys/mythril)|
[oyente](https://github.com/enzymefinance/oyente)|
[smartbugs](https://smartbugs.github.io/)|
***Code Analyzer***
[slither](https://github.com/crytic/slither)
***Bin Analyzer***
***Test Framework***
[embark](https://github.com/embarklabs/embark)

## Q & A
Q|A
---|---
```truffle vs. hardhat```|
