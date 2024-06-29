# Token Creation

This is a Solidity Project "Token Creation" program.

## Description

The TokenCreation project creates a token that may be burned and minted. Users can mint new tokens to a specific address to increase the Total supply of the "Skull" token (SKL)," or burn existing tokens from that address to reduce the total supply.

## Getting Started

### Executing program

To run the program use Remix IDE, an Online Platform https://remix.ethereum.org/.

Once you are on the Remix website, create a new file and save the file with a .sol extension (like TokenCreation.sol). Copy and paste the code into the file:

// SPDX-License-Identifier: MIT
pragma solidity 0.8.25;

contract MyToken {

    // public variables here
    string public TName = "Naman";
    string public TAbbrv = "nam";
    uint public TSupply = 0;

    // mapping variable here
    mapping( address => uint ) public balance;

    // mint function
    function mint (address _addr, uint _val) public {
        TSupply += _val;
        balance[_addr] += _val;
    }

    // burn function
    function burn (address _addr, uint _val) public {
        if ( balance[_addr] >= _val ) {
            TSupply -= _val;
            balance[_addr] -= _val;
        }        
    }
}
Compile the code and then deploy it
Add the address to mint/burn to add or burn the tokens.

## Authors

Naman Sinha

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
