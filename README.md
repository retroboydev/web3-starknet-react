# web3-starknet-react 🚀

_A simple, maximally extensible, dependency minimized framework for building Starknet dApps_

_Provides easy access to Starknet Interface all over the React App. Inspired from_ [web3-react](https://github.com/NoahZinsmeister/web3-react/tree/v6)

<br>

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

| Packages                                  | `@latest` version                                                                                                                                                                 | Size                                                                                                                                                                                         | Description                                                            |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 🏝 **Core**                                |                                                                                                                                                                                   |                                                                                                                                                                                              |                                                                        |
| `@web3-starknet-react/core`               | [![npm version](https://img.shields.io/npm/v/@web3-starknet-react/core/latest.svg)](https://www.npmjs.com/package/@web3-starknet-react/core/v/latest)                             | [![minzip](https://img.shields.io/bundlephobia/minzip/@web3-starknet-react/core/latest.svg)](https://bundlephobia.com/result?p=@web3-starknet-react/core@latest)                             | [React](https://reactjs.org/) hooks and context for accessing Starknet |
| 🔌 **Connectors**                         |                                                                                                                                                                                   |                                                                                                                                                                                              |                                                                        |
| _Browser Extension/dApp Browser_          |                                                                                                                                                                                   |                                                                                                                                                                                              |                                                                        |
| `@web3-starknet-react/braavos-connector`  | [![npm version](https://img.shields.io/npm/v/@web3-starknet-react/braavos-connector/latest.svg)](https://www.npmjs.com/package/@web3-starknet-react/braavos-connector/v/latest)   | [![minzip](https://img.shields.io/bundlephobia/minzip/@web3-starknet-react/braavos-connector/latest.svg)](https://bundlephobia.com/result?p=@web3-starknet-react/braavos-connector@latest)   | [Braavos Wallet](https://chrome.google.com/webstore/detail/braavos-wallet/jnlgamecbpmbajjfhmmmlhejkemejdma) connector |
| `@web3-starknet-react/argentx-connector`  | [![npm version](https://img.shields.io/npm/v/@web3-starknet-react/argentx-connector/latest.svg)](https://www.npmjs.com/package/@web3-starknet-react/argentx-connector/v/latest)   | [![minzip](https://img.shields.io/bundlephobia/minzip/@web3-starknet-react/argentx-connector/latest.svg)](https://bundlephobia.com/result?p=@web3-starknet-react/argentx-connector@latest)   | [ArgentX Wallet](https://github.com/argentlabs/argent-x) connector     |
| 🔫 **Low Level**                          |                                                                                                                                                                                   |                                                                                                                                                                                              |                                                                        |
| `@web3-starknet-react/abstract-connector` | [![npm version](https://img.shields.io/npm/v/@web3-starknet-react/abstract-connector/latest.svg)](https://www.npmjs.com/package/@web3-starknet-react/abstract-connector/v/latest) | [![minzip](https://img.shields.io/bundlephobia/minzip/@web3-starknet-react/abstract-connector/latest.svg)](https://bundlephobia.com/result?p=@web3-starknet-react/abstract-connector@latest) | Low Level implementation of connector                                  |
| `@web3-starknet-react/types`              | [![npm version](https://img.shields.io/npm/v/@web3-starknet-react/types/latest.svg)](https://www.npmjs.com/package/@web3-starknet-react/types/v/latest)                           | [![minzip](https://img.shields.io/bundlephobia/minzip/@web3-starknet-react/types/latest.svg)](https://bundlephobia.com/result?p=@web3-starknet-react/types@latest)                           | Shared [TypeScript](https://www.typescriptlang.org/) Types             |

<br />

#

## ⭐️ [Documentation](docs)

## Projects using `web3-starknet-react`

_Open a PR to add your starknet project to the list_

- [JediSwap](https://app.testnet.jediswap.xyz/#/swap)

## Local Development

- Clone repo \
  `git clone https://github.com/dhruvkelawala/web3-starknet-react`

- Install top-level dependencies \
  `yarn`

- Install sub-dependencies \
  `yarn bootstrap`

- Build and watch for changes \
  `yarn start`

## Local testing

There are two possible ways of local testing: by using the [yarn link](https://classic.yarnpkg.com/en/docs/cli/link) command or by manual transferring of built files

### Testing by using the [yarn link](https://classic.yarnpkg.com/en/docs/cli/link) command
Since we use `lerna`, it's a bit tricky.
- run `yarn buid` in the root directory of the project, you should see the `dist` folders after that in all subpackages
- run `yarn start` in the root directory of the project
- open a new tab, go to the folder of the subpackage you want to test and run `yarn link` in the root directory of that package. For example, `cd ./packages/argentx-connector && yarn link`. You should see in the console command for using the linked module, e.g. `yarn link "@web3-starknet-react/argentx-connector"`. You should do the same for all subpackages you want to test. 
- go to the project where we want to test our module, e.g. `jediswap-interface`
- to install our linked subpackage, run `yarn link "@web3-starknet-react/argentx-connector"` (or the similar command for others subpackages) 
- if everything was done right, you would see a success message in the console, and a symlink to our local package will appear in `node_modules/@web3-starknet-react/`
- after that we can start working with our local subpackages, all changes should be updated automatically
- once we're done, go to the folder of the subpackage we tested and run the `yarn unlink` command there. Run `yarn unlink "@web3-starknet-react/argentx-connector" && yarn install --check-files` (or the similar command for others subpackages) in the project where we tested our module after that.

### Testing with manual transferring of built files
This method is less convenient and requires a lot of manual operations
- run `yarn buid` in the root directory of the project, you should see the `dist` folders after that in all subpackages
- run `yarn start` in the root directory of the project
- copy the contents of the `dist` folder to `node_modules/@web3-starknet-react/argentx-connector/dist` (or to the similar directory for other subpackages) of the project in which we want to test our module
- if you are using `vite` in a project, you should add the `--force` flag to the project launch command, for example, `vite --open --force`
- when you change your module, you should copy and past the contents of the `dist` folder again
