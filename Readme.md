PROJECT TITLE: TOKEN MANAGEMENT SMART CONTRACT FOR MINTING AND BURNING

DESCRIPTION: This project involves creating a basic Ethereum smart contract that manages a token named "NamanKunarSinha" with the abbreviation "NKS" and the symbol "N". Written in Solidity, this smart contract facilitates the minting and burning of these tokens.

PUBLIC VARIABLES:

- **fulltokenName**: Stores the name of the token.
- **tokenAbbr**: Stores the abbreviation of the token, set to "NKS".
- **symb**: Stores the symbol of the token, set to "N".
- **totalSupply**: Keeps track of the total number of tokens in circulation. Initially set to 0.

MAPPING **balances**: A mapping that links addresses to their respective token balances, using an address as the key and a uint as the value to store the balance.

MINT FUNCTION: The `mintToken` function is used to create new tokens and assign them to a specified address. It takes two parameters:
- **add**: The address to which the new tokens will be assigned.
- **value**: The number of tokens to be created and added to the total supply.

BURN FUNCTION: The `burnToken` function is used to destroy tokens from a specified address, reducing both the total supply and the balance of the address. It also takes two parameters:
- **add**: The address from which the tokens will be burned.
- **value**: The number of tokens to be burned.
