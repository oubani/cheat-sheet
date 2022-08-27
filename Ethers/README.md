# Ethers

to install ethers run the next command `yarn add ethers `

## Compile contract

to compile solidity contract install solc then create command in script in package.json then run in the terminal

```
    "compile": "yarn solcjs --bin --abi --include-path node_modules/ --base-path . -o . SimpleStorage.sol"
```

then run `yarn compile` that will create two files, the binary and abi

## deploy contract

after installing ethers you have to initial the provider then connect the wallet then you can deploy it

1.

```

```
