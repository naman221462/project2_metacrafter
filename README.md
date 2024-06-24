# project2_metacrafter
# MyToken Smart Contract

## Simple Overview
The MyToken project is a basic implementation of a token on the Ethereum blockchain. It includes fundamental functionalities such as minting and burning tokens, serving as an introductory example of how tokens can be managed on Ethereum.

## Description
The MyToken smart contract enables the creation and management of a custom token with a user-defined name and abbreviation. Users can mint new tokens to increase the total supply and their balances, or burn tokens to reduce the total supply and their balances. This contract is suitable for educational purposes or small-scale projects, offering a foundational understanding of token operations on Ethereum.

## Getting Started

### Installing

#### How/Where to Download the Program
1. Ensure [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) are installed on your system.
2. Install [Truffle Suite](https://www.trufflesuite.com/):
    ```bash
    npm install -g truffle
    ```
3. Clone the project repository from GitHub:
    ```bash
    git clone https://github.com/yourusername/MyToken.git
    cd MyToken
    ```

#### Modifications Needed to Be Made to Files/Folders
1. Update the contract name and parameters in the `MyToken.sol` file if necessary.
2. Configure the desired Ethereum network in `truffle-config.js`.

### Executing Program

#### How to Run the Program

1. Compile the smart contract:
    ```bash
    truffle compile
    ```
2. Deploy the smart contract to the chosen Ethereum network:
    ```bash
    truffle migrate --network <network_name>
    ```
    Replace `<network_name>` with the appropriate network specified in `truffle-config.js`.

3. Interact with the deployed smart contract using Truffle console:
    ```bash
    truffle console --network <network_name>
    ```

#### Step-by-Step Execution
1. Mint tokens:
    ```javascript
    let instance = await MyToken.deployed();
    await instance.mint('0xYourAddress', 1000);
    ```
2. Burn tokens:
    ```javascript
    await instance.burn('0xYourAddress', 500);
    ```

### Help
#### Common Problems and Solutions
1. **Insufficient Gas**: Ensure sufficient ETH in your account to cover gas fees.
2. **Invalid Opcode**: Check for syntax or logical errors in the contract.
3. **Network Issues**: Verify network configuration in `truffle-config.js`.

#### Command for Help Information
If a help command is implemented, use the following to get assistance:
```bash
truffle exec scripts/help.js
```

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
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
```
