# BlockChain Basics

### Smart Contract

    like traditional contracts but written in code and embodied on these decentralized blockchain platforms, and that's also where they are executed

### Ethereum Vs Bitcoin

1. Ethereum
   is a store of value and utility to facilitate decentralized agreements
1. Bitcoin
   is a store of value.

#### Ethereum uses Keccak256 for hashing

### Words

1. Hash : is unique fixed length string to identify a piece of data
2. Block : list of transactions minde together
3. Decentralized : having no single point of authority
4. Nonce : A "Number used once " to find the "Solution" to he blockchain problem also used to define the transaction number for an account

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

6. Sharding && Rollups needs to be understand latter.

# Solidity

## Data Types

1. Boolean
2. uint : positive numbers
3. int : positive or negative number
4. address
5. bytes

## Functions or methods

execute a subset of code when they called

### functions visibility

```
   function myFunction () <visiblity specifier > returns (bool) {
      return true
   }
```

#### public

visible externally and internally (creates a getter function for storage /state variables)

#### private

only visible in the current contract

#### external

only visible externally (only for functions) can only be message-called(via this.func)

#### internal

only visible internally

## file

1. Spdx licence
2. choose the version we want to use.
3. decalre contract
4. initialize data;
5. create functions
6. import contract in contact

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.7;
import "./secondContractName.sol"

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

   // mapping

   mapping (string => uint256) public nameToFavoriteNumber;

   // getter

   function read() public view returns (uint256) {
      return favoriteNumber;
   }

   // create array of people with favorite number and add person to array

   struct People {
      uint256 favoriteNumber;
      string name;
   }

   People[] public people;

   function addPerson (string memory _name, uint _favoriteNumber) public {
      people.push(People(_favoriteNumber,_name));
      nameToFavoriteNumber[_name]=_favoriteNumber
   }

}
```

# Basic solidity

## Memry, Storage,& calldata

EVM can access and store information in six places

1. Stack
2. Memory : for temporary variable can be modified.
3. Storage
4. Calldata : temporary variable can't be modified.
5. Code
6. Logs

## Mappings

is a data structure where a key is "mapped" to a single value

## Tips

- You can Create array of contracts

* import Contract

```
import './SimpleStorage';

contract StorageFactory {

SimpleStorage[] public simpleStorageArray;

// call store function in SimpleStoreProduct
function sfStore(uint256 _SimpleStorageIndex,uint256 _simpleStorageNumber) public {
   simpleStorageArray[_simpleStorageIndex].store(_simpleStorageNumber)
}
// read Favorite number in SimpleStorage
function fsRead(uint256 _simpleStorageIndex) public view returns (uint256) {
   return simpleStorageArray[_simpleStorageIndex].read();
}


}


```

- Inheritance && Overriding
  make the function you want to override virtual, and add override to the function

```
...
// in parent function we add virtual
import './SimpleStorage.sol'
contract  SimpleStorage  {
   function store(uint256 _favoriteNumber) public virtual {
      favoriteNumber =_favoriteNumber;
   }
}
contract ExtraStorage is SimpleStorage  {
   function store(uint256 _favoriteNumber) public override {
      favoriteNumber =_favoriteNumber+120;
   }
}

```

## Payable functions

you add payable word to the function

```
   function fund() public payable {
      // if you want to get the payied amount
      msg.value;

   }
```

## Reverting

undo all the action before, and send remaining gas back, if the first params of require is false;

```
   // to use
     require(msg.value>1e18,"You don't have enough!");
```

## chainLink

i will fill it later

## Library

doesn't contain state, all function have internal instead of public , after importing it you have to use it <br/>
exemple : <br/>
/LibraryName.sol

```
....
library PriceConverter {
   function convertionRate (uint ethAmount) internal view returns (uint256) {
      .....
   }
}
```

/Fund.sol

```
....
import './LibraryName.sol';

contract Fund {
   using LibraryName for uint256;
}
```

## refresh or resetting an array

`funders = new address[](0);`

## withdraw funds

```
/* actually withdraw the funds */
        //transfer : throws error if fail revert the transaction
        payable(msg.sender).transfer(address(this).balance);
        // send : return bool
        bool sendSuccess = payable(msg.sender).send(address(this).balance);
        require(sendSuccess,"Send Faild");
        // call
        (bool callSuccess, ) = payable(msg.sender).call{value:address(this).balance}("");

        require(callSuccess,"Call faild");
```
