* [ ] https://remix.ethereum.org/
remixd -s <absolute-path-to-the-shared-folder> --remix-ide <your-remix-ide-URL-instance>

## Playground
## Tutorials
## Traits - Diff with Hardhat, Truffle
- For remix IDE, you don't need to write test javascript codes. It supports UI interaction. You can interact the deployed contract to run it & debug it
- It also support test sol part.
## Syntax
step|expl.
----|---
```install```|```npm install -g @remix-project/remixd```
```connect```|```remixd -s <absolute-path-to-the-shared-folder> --remix-ide <your-remix-ide-URL-instance> for connecting to your local IDE```<br>```remixd -s <absolute-path-to-the-shared-folder> --remix-ide https://remix.ethereum.org``` for connecting to online IDE
```create.project```|```npx create-remix@latest```*# IMPORTANT: Choose "Remix App Server" when prompted*<br>```cd [whatever you named the project]```<br>```npm run dev```