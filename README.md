# myToken
code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // public variables here
    string public Token_name = "NAMAOM";
    string public Token_abbreviation = "NAM";
    uint public Total_supply = 10;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        Total_supply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance.");
        
        Total_supply -= _value;
        balances[_address] -= _value;
    }
    
    // transfer function
    function transfer(address _to, uint _value) public {
        require(balances[msg.sender] >= _value, "Insufficient balance.");
        require(_to != address(0), "Invalid address.");
        
        balances[msg.sender] -= _value;
        balances[_to] += _value;
    }  
   
    
}
