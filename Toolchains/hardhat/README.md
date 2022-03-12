- https://www.freecodecamp.org/news/solidity-tutorial-hardhat-nfts/
- https://github.com/taisukemino/hardhat-nft-tutorial
- https://hardhat.org/

## What hardhat does? - compile, deploy, test, and debug
trait|desp.
-----|----
```install```|```npm install --save-dev hardhat@2.4.3```
```new.project```|*```mkdir <projectname>;cd <projectname>```<br>```npx hardhat```<br><br>//hardhat.project.structure```|<br>contracts/<br>scripts/<br>test/<br>hardhat.config.js*
```new.contract```|```cd contracts && touch <contractName>.sol```
***compile***|```npx hardhat compile```
***test***|```npx hardhat test```
***deploy***|```touch scripts/deploy.js```<br>```npx hardhat run scripts/deploy.js```
## Guide
step|js|ts
----|---|----
***hardhat.init***
```init```|```npm init --yes```|```yarn init --yes```
```install```|```npm install --save-dev hardhat@2.4.3```|yarn add -D hardhat```
```config```|```hardhat.config.js```|```hardhat.config.ts```<br>```tsconfig.json```
***write.contract***|
```mk.tree```|```mkdir contracts && cd contracts && touch MyCryptoLions.sol```
```add.deps```|```npm install --save-dev @openzeppelin/contracts@3.4.0```|```npm install @openzeppelin/contracts```
```write.file```|```vim MyCryptoLions.sol```
***compile***|```npx hardhat compile```|```yarn hardhat compile```
***test***|```npm install --save-dev @nomiclabs/hardhat-waffle@2.0.1```<br>```..................... @ethereum-waffle@3.3.0 chai@4.3.4```<br>```.................... @nomiclabs/hardhat-ethers@2.0.2 ethers@5.1.4```<br>```mkdir test && cd test && touch test.js```<br>```npx hardhat test```|```npx hardhat test```
***deploy***|```touch scripts/deploy.js```<br>```npx hardhat run scripts/deploy.js```|```yarn hardhat deploy```np
## [Deploy on Different Networks](https://ethereum.stackexchange.com/questions/110271/hardhat-connecting-to-localhost-contract-for-tasks)
network|usage
---|----
```localhost```|*run localhost:```npx hardhat node``` on one terminal<br>run task:```npx hardhat run scripts/deploy.js``` on the other terminal*
```ropsten```|```npx hardhat run scripts/deploy.js --network ropsten```
## Q & A
Q|A
-|-
```npx hardhat console```vs.```npx hardhat node```
### Set Up the Project
```bash
# mkdir nft; cd nft
nft$ npm init --yes
nft$ npm install --save-dev hardhat@2.4.3
nft$ npx hardhat
$ cat hardhat.config.js 
/**
 * @type import('hardhat/config').HardhatUserConfig
 */
module.exports = {
  solidity: "0.7.3",
};
```
### Write and Compile the Contract
```
[write]
nft$ mkdir contracts && cd contracts && touch MyCryptoLions.sol
nft$ npm install --save-dev @openzeppelin/contracts@3.4.0
nft$ vim  MyCryptoLions.sol

[compile]
$ nft/contracts# npx hardhat compile
>>>
Downloading compiler 0.7.3
Compiling 14 files with 0.7.3
contracts/MyCryptoLions.sol: Warning: SPDX license identifier not provided in source file. Before publishing, consider adding a comment containing "SPDX-License-Identifier: <SPDX-License>" to each source file. Use "SPDX-License-Identifier: UNLICENSED" for non-open-source code. Please see https://spdx.org for more information.

@openzeppelin/contracts/introspection/ERC165.sol:24:5: Warning: Visibility for constructor is ignored. If you want the contract to be non-deployable, making it "abstract" is sufficient.
    constructor () internal {
    ^ (Relevant source part starts here and spans across multiple lines).

@openzeppelin/contracts/token/ERC721/ERC721.sol:93:5: Warning: Visibility for constructor is ignored. If you want the contract to be non-deployable, making it "abstract" is sufficient.
    constructor (string memory name_, string memory symbol_) public {
    ^ (Relevant source part starts here and spans across multiple lines).

Compilation finished successfully

```
- MyCryptoLions.sol
```js
pragma solidity ^0.7.3;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "hardhat/console.sol";

contract MyCryptoLions is ERC721 {
    constructor(string memory name, string memory symbol) ERC721(name, symbol) {
        console.log("name", name);
        console.log("symbol", symbol);
        console.log("msg.sender", msg.sender); //msg.sender is the address that initially deploys a contract
    }
}
```
### Test
```js
const { expect } = require("chai");

describe("MyCryptoLions", function () {
  it("Should return the right name and symbol", async function () {
    const MyCryptoLions = await hre.ethers.getContractFactory("MyCryptoLions");
    const myCryptoLions = await MyCryptoLions.deploy("MyCryptoLions", "MCL");

    await myCryptoLions.deployed();
    expect(await myCryptoLions.name()).to.equal("MyCryptoLions");
    expect(await myCryptoLions.symbol()).to.equal("MCL");
  });
});
```
```bash
$ npx hardhat test


  MyCryptoLions
name MyCryptoLions
symbol MCL
msg.sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
    ✓ Should return the right name and symbol (896ms)


  1 passing (899ms)

```
### Deploy
```js
//scripts/deploy.js
async function main() {
  const MyCryptoLions = await hre.ethers.getContractFactory("MyCryptoLions");
  const myCryptoLions = await MyCryptoLions.deploy("MyCryptoLions", "MCL");

  await myCryptoLions.deployed();

  console.log("MyCryptoLions deployed to:", myCryptoLions.address);
}

main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.error(error);
    process.exit(1);
  });
```
```bash
npx hardhat run scripts/deploy.js
>>>
name MyCryptoLions
symbol MCL
msg.sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
MyCryptoLions deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3

```
