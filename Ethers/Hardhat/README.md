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

# Deploy Contract

to deploy contract you create javascript file on scripts folder then you run it

# Deploy contract to hardat

in scripts/deploy.js create a function to deploy the contract

```javascript
const { ethers } = require("hardhat");

async function main() {
  const SimpleStorage = await ethers.getContractFactory("SimpleStorage");
  console.log(`Deploying contract ...`);
  const contract = await SimpleStorage.deploy();
  await contract.deployed();
  console.log("Contract deployed");
  console.log(contract);
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
