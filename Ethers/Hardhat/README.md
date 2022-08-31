# Hardhat

to create hardhat project create yarn project then install hardhat

1. initial yarn : `yarn init`
2. install hardhat as dev dependencies : `yarn add --dev hardhat`
3. add other dependencies

## compile the contract

to compile the contract you run :

```
    yarn hardhat compile
```

# Deploy Contract using scripts/deploy.js file

to deploy contract you create javascript file on scripts folder then you run it

## Deploy contract to hardat

in scripts/deploy.js create a function to deploy the contract

```javascript
const { ethers } = require("hardhat");

async function main() {
  const SimpleStorage = await ethers.getContractFactory("SimpleStorage");
  console.log(`Deploying contract ...`);
  const contract = await SimpleStorage.deploy();
  await contract.deployed();
  console.log(`Contract deployed to : ${contract.address}`);
}

main()
  .then(() => process.exit(0))
  .catch((error) => {
    console.log("Error");
    console.error(error);
    process.exit(0);
  });
```

## Deploy To other networks "Rinkeby"

in .env file store the private key and rpc url

```env
RINKEBY_RPC_NETWORK=
PRIVATE_ACCOUNT=
```

in hardhat.config.js add network you want to deploy to, you have to install detenv as dev dep

```javascript
require("dotenv").config();

const account = process.env.PRIVATE_ACCOUNT;
const rpcUrl = process.env.RINKEBY_RPC_NETWORK;

module.exports = {
  solidity: "0.8.8",
  networks: {
    rinkeby: {
      accounts: [account],
      chainId: 4,
      url: rpcUrl,
    },
  },
};
```

then you run

```
yarn hardhat run scripts/deploy.js --network rinkeby
```

if you deployed it successfully you can search for it in : [https://rinkeby.etherscan.io](https://rinkeby.etherscan.io)

## Solhint

it hepls to check with you to run it , run the command

```
  yarn solhint contracts/*.sol
```

# Deploy using hardhaat-deploy package.

to install the package you have to run the command

```
  yarn add --dev hardhat-deploy
```

in hardhat.config.js add the package

`require('hardhat-deploy') `

then you create a folder named deploy cause that what our package will lock for, then install hardhatethers by running the command below

```
  yarn add --dev @nomiclabs/hardhat-ethers@npm:hardhat-deploy-ethers ethers
```

in deploy folder create file who make the deploy ` 01-deploy-fund-me.js` needs to be orderd

## Deploy

in '01-deploy-fund-me.js'

```javascript
module.exports = async () => {};
```

then you run

```
 yarn hardhat deploy
```

# to watch later

1. 9:10 hardhat task
