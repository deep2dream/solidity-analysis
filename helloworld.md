- https://asvin.io/develop-test-and-deploy-your-first-ethereum-smart-contract/
### follow the steps
- node
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
nvm install 12.18.1
```
- truffle
```
npm install -g truffle
```
- Ganache cli
```
npm install -g ganache-cli
```
- helloworld
```
git clone https://github.com/b-rohit/hello-world-smart-contract.git 
cd dapp-hello-world

[run.]
ganache-cli

[interactive]
truffle develop
> compile
> migrate

[test]
truffle test
truffle compile
```
