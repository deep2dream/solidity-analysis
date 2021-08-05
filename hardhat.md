- https://www.freecodecamp.org/news/solidity-tutorial-hardhat-nfts/
- https://github.com/taisukemino/hardhat-nft-tutorial
### Set Up the Project
```bash
# mkdir nft; cd nft
nft# npm init --yes
nft# npm install --save-dev hardhat@2.4.3
nft# npx hardhat
>>> Choose Create an empty hardhat.config.js
888    888                      888 888               888
888    888                      888 888               888
888    888                      888 888               888
8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
888    888 .d888888 888    888  888 888  888 .d888888 888
888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888

Welcome to Hardhat v2.2.1

? What do you want to do? … 
▸ Create a sample project
  Create an empty hardhat.config.js
  Quit
  
# cat hardhat.config.js 
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
nft# mkdir contracts && cd contracts && touch MyCryptoLions.sol
nft# npm install --save-dev @openzeppelin/contracts@3.4.0
nft# vim  MyCryptoLions.sol

[compile]
nft/contracts# npx hardhat compile
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
```
npm install --save-dev @nomiclabs/hardhat-waffle@2.0.1 ethereum-waffle@3.3.0 chai@4.3.4 @nomiclabs/hardhat-ethers@2.0.2 ethers@5.1.4
mkdir test && cd test && touch test.js
```
- test.js
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
```
# npx hardhat test


  MyCryptoLions
name MyCryptoLions
symbol MCL
msg.sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
    ✓ Should return the right name and symbol (896ms)


  1 passing (899ms)

```
### Deploy
- scripts/deploy.js
```js
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
```
npx hardhat run scripts/deploy.js
>>>
name MyCryptoLions
symbol MCL
msg.sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
MyCryptoLions deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3

```
