# BlockChain Basics

### Smart Contract

    like traditional contracts but written in code and embodied on these decentralized blockchain platforms, and that's also where they are executed

### Ethereum Vs Bitcoin

1. Ethereum
   is a store of value and utility to facilitate decentralized agreement
1. Bitcoin
   is a store of value.

#### Ethereum uses Keccak 256 for hashing

### Words

1. Hash : is unique fixed length string to identify a piece of data
2. Block : list of transactions minde together
3. Decentralized : having no single point of authority
4. Nonce : A "Number used once " to find the "Soluion" to he blockchain problem also used to define the transaction number for an account

### Signing transactions

#### Words

1. Private Key
   Only knowen to the key holder, it's used to "sign" the transactions.
2. Public Key
   is derived from the private key, Anyone can see it, and use it to verify that a transaction came from you.
3. Gas
   the more people use a chain, the more expensive it is to send a transactions.
4. Base Fee : the minimum gas price to send a transaction.
5. the bigger the blockchain, he more secure.

6. Sharding && Rollups needs to be understand

# Solidity

## Data Types

1. Boolean
2. uint : positive numbers
3. int : positive or negative number
4. address
5. bytes

## Functions or methods

execute a subset of code when they called

## file

1. Spdx licence
2. choose the version we want to use.
3. decalre contract
4. initialize date;
5. create functions

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.7;
contract ContractName {
   bool hasFavoriteNumber = false;
   // this gets initialized to zero
   uint256 favoriteNumber;
   string favoriteNumberInText= "five";
   int256 favoriteNumberIntType= -5;
   address myAddress=0xB5f107ac4e2C1F8f5cec1CF7BCa82089f3e408d9;

   function store(_uint256 _favoriteNumber) public {
      favoriteNumber = _favoriteNumber;
   }

}
```
