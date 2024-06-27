# MyToken Smart Contract

## Overview
The MyToken project is a basic example of a token on the Ethereum blockchain. It includes simple functions like minting and burning tokens, making it a good starting point for learning about token management on Ethereum.

## Description
The MyToken smart contract lets you create and manage a custom token with a name and abbreviation that you choose. You can mint new tokens to increase the total supply and your balance, or burn tokens to decrease the total supply and your balance. This contract is great for learning purposes or small projects.

## Getting Started

### Installation

#### How to Download and Set Up
1. Make sure you have [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) installed on your computer.
2. Install [Truffle Suite](https://www.trufflesuite.com/):
    ```bash
    npm install -g truffle
    ```
3. Clone the project from GitHub:
    ```bash
    git clone https://github.com/yourusername/MyToken.git
    cd MyToken
    ```

#### File Modifications
1. If needed, update the contract name and parameters in the `MyToken.sol` file.
2. Set up the desired Ethereum network in `truffle-config.js`.

### Running the Program

#### How to Compile and Deploy
1. Compile the smart contract:
    ```bash
    truffle compile
    ```
2. Deploy the smart contract to the chosen Ethereum network:
    ```bash
    truffle migrate --network <network_name>
    ```
    Replace `<network_name>` with the network you set in `truffle-config.js`.

#### How to Interact with the Smart Contract
1. Open the Truffle console:
    ```bash
    truffle console --network <network_name>
    ```
2. Mint tokens:
    ```javascript
    let instance = await MyToken.deployed();
    await instance.mint('0xYourAddress', 1000);
    ```
3. Burn tokens:
    ```javascript
    await instance.burn('0xYourAddress', 500);
    ```

### Troubleshooting

#### Common Issues and Fixes
1. **Not Enough Gas**: Make sure you have enough ETH to pay for gas fees.
2. **Invalid Opcode**: Check for mistakes in your contract code.
3. **Network Problems**: Check the network settings in `truffle-config.js`.

## Authors
- Dominique Pizzie  
  GitHub: @DomPizzie

## License
This project is licensed under the MIT License - see the LICENSE.md file for details.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    string public tokenName;
    string public tokenAbbrv;
    uint256 public totalSupply;

    mapping(address => uint256) public balances;

    constructor(string memory _name, string memory _abbrv) {
        tokenName = _name;
        tokenAbbrv = _abbrv;
    }

    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    function burn(address _from, uint256 _value) public {
        require(balances[_from] >= _value, "Not enough balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
```
