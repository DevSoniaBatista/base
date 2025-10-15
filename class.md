base

entrar no VisualStudio, Cursor ou WindSurf

Instalar Foundry
curl -L https://foundry.paradigm.xyz | bash
foundryup
forge init

entrar no alchemy para pegar RPC 

chains/sepolia
app - sepolia

https://base-sepolia.g.alchemy.com/v2/NRHdzgu7amEcHNHFbYGxeUFVOlkItB15

App Dashboard / Connect or Node RPC/ Mudar network / base Sepolia
copy Endpoint
https://base-sepolia.g.alchemy.com/v2/NRHdzgu7amEcHNHFbYGxeUFVOlkItB15

BAck to foundry and create .env file
BASE_SEPOLIA_RPC_URL="[copy endpoint here]"

escrever Greeting.sol no src
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

contract Greeting {
    string public greeting;

    constructor(string memory _greeting) {
        greeting = _greeting;
    }

    function setGreeting(string memory _greeting) public {
        greeting = _greeting;
    }

    function greet() public view returns (string memory) {
        return greeting;
    }
}
====

forge build
===

fazer deploy 
===
incluir Base no metamask - buscar chainList
https://chainlist.org/?search=base+&testnets=true
===
pegar private key no metamask e colocar no .env

==
source .env
forge create src/Greeting.sol:Greeting --rpc-url $BASE_SEPOLIA_RPC_URL --broadcast --private-key $PRIVATE_KEY --constructor-args "Hello Base Buiderls-Brazil Sonia"

will show the contract address
 go to scan base - blockexplorer 
 
 https://sepolia.basescan.org/
 
 ---- create a api key em sepolia
 e use this apikey on .env to verify contract
 
forge verify-contract --chain base-sepolia --verifier etherscan --etherscan-api-key $BASESCAN_API_KEY --constructor-args $(cast abi-encode "constructor(string)" "New greeting") [contract-address] src/Greeting.sol:Greeting

=== contract deployed:
Deployer: 0x49eE6FB60a0941fC9aAc4DBf1e9d1aF4cc00DF1f
Deployed to: 0x32c62C09CF0C6eBDBa31f370A8c7B578b74746E0
Transaction hash: 0x4dfab5e8b63f98c61c7f3878a424ab13956e3e24c2a081edefbf6e4f7af001d6

forge verify-contract --chain base-sepolia --verifier etherscan --etherscan-api-key $BASESCAN_API_KEY --constructor-args $(cast abi-encode "constructor(string)" "New greeting") 0x32c62C09CF0C6eBDBa31f370A8c7B578b74746E0 src/Greeting.sol:Greeting
