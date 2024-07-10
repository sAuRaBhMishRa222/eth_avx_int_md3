# Error Handling in solidity

This Solidity contract implements a simple ERC20 token creation system, enabling the owner to mint and manage tokens that comply with the ERC20 standard. The contract features a mint function that allows the owner to create new tokens and assign them to a specified address, ensuring that only the owner can perform this action. The contract also includes a burn function that enables the sender to remove tokens from their balance, and a transfer function that allows users to move tokens between accounts, adhering to the ERC20 protocol. Furthermore, the contract provides a mechanism for the owner to maintain control over token creation and management, ensuring that tokens are distributed securely and transparently, while also conforming to the widely-adopted ERC20 standard for token implementation.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. This contract implements a token creation system that adheres to the ERC20 standard, allowing the owner to mint and burn tokens, as well as transfer them between accounts. As an ERC20-compliant token, it includes essential functions such as totalSupply, balanceOf, and transfer, ensuring seamless interaction with other ERC20-compatible contracts and wallets. Additionally, it ensures the integrity of token ownership and maintains a record of token balances, providing a secure and transparent way to manage digital assets on the Ethereum network.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

import "https://github.com/OpenZeppelin/openzeppelin-solidity/contracts/token/ERC20/ERC20.sol";

contract createToken is ERC20 {
    address public owner;

    constructor() ERC20("Saurabh", "SMG") {
        owner = msg.sender;
        _mint(msg.sender, 100 * 10**uint(decimals()));
    }

    function mint(address to, uint256 amount) public {
        require(msg.sender == owner, "Only the owner can mint tokens");
        _mint(to, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfer(address recipient, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }

}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.26" (or another compatible version), and then click on the "Compile myToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "myToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling various functions to manage tokens. Click on the deployed createToken contract in the left-hand sidebar. To mint new tokens, click on the mint function, pass the required parameters (address to and uint amount), and execute the function to create new tokens and assign them to the specified address, but note that only the owner can execute this function. To burn existing tokens, click on the burn function, pass the required parameter (uint amount), and execute the function to remove tokens from the sender's balance. To transfer tokens between accounts, click on the transfer function, pass the required parameters (address recipient and uint amount), and execute the function to move tokens from the sender's balance to the recipient's balance. The contract uses require to ensure only the owner can mint tokens, and override to customize the token transfer functionality, ensuring secure and controlled token management.

## Authors

Saurabh Mishra  


## License

This project is licensed under the MIT License
