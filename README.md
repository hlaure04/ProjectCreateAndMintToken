# ProjectCreateAndMintToken

# Description
You will write a smart contract to create your own ERC20 token and deploy it using HardHat or Remix. 
Once deployed, you should be able to interact with it for your walk-through video. 
From your chosen tool, the contract owner should be able to mint tokens to a provided address and 
any user should be able to burn and transfer tokens.



# Getting Started
# Executing Program
- To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.
- Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar.
- Save the file with a .sol extension
- Copy and paste the following code into the file
- To compile the code, select the "Solidity Compiler" tab in the left-hand sidebar, change the "Compiler" option to "0.8.20"
- Then click the "Compile ProjectCreateAndMintTokens1.sol" button.
- To deploy the contract, choose the "ProjectCreateAndMintTokens1" contract from the dropdown menu and click the "Deploy" button.
- Interact with the contract by the contract owner should be able to mint tokens to a provided address and 
any user should be able to burn and transfer tokens.


# Code Preview
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;


import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyDeanListToken is ERC20 {
address public owner; 

// Declare owner variable
constructor() ERC20("Deanlist", "DNLST") {
    owner = msg.sender; 
    
    // Assign the deployer as the owner
    
   function mint(address _to, uint256 _amount) public returns (bool success) {
        require(msg.sender == owner, "Only the owner can mint tokens");
        
        _mint(_to, _amount);
        _totalSupply += _amount;
        return true;
    }

    function burn(uint256 _amount) public returns (bool success) {
        _burn(msg.sender, _amount);
        _totalSupply -= _amount;
        return true;
    }

    function transfer(address _to, uint256 _value) public override returns (bool success) {
        _transfer(msg.sender, _to, _value);
        return true;
    }
}

# Authors
Heleana V. Laure
8213709@ntc.edu.ph
