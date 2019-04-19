# Module 4 - Culmination Lab: Smart Contract Using Truffle and Ganache

## Background
Following the inception of the Ethereum world computer and smart contracts which run on it, many tools for development of smart contracts have come about. A few noteworthy tools address issues such as risk and other costs to deploy and test smart contracts. Prior to beginning this lab, it is assumed that you have completed the installations of Python, Node.js, Truffle, and Ganache. In this lab, we will create a "Hello World" smart contract which will be executed locally on our personal blockchain.

## Meta Information
| Attribute | Explanation |
| - | - |
| Summary | Hello-world exercise using Truffle and Ganache. |
| Topics | Truffle, Ganache, and Smart Contracts. |
| Audience | CS1 or later. |
| Difficulty | Beginner. |
| Strengths | Constitutes a full development cycle. |
| Weaknesses | Is just one of the ways to develop for Ethereum. |
| Dependencies | Python, Node.js, Truffle, and Ganache. |
| Variants | There are prior labs for installing Truffle and Ganache. |

## Assignment Instructions
1. Install the command-line version of Ganache.
    * In a terminal or command prompt, run: npm install -g ganache-cli
2. Let Ganache run in its own terminal while we move on to begin development.
    * In a terminal or command prompt, run: ganache-cli
3. In a new terminal or command prompt, set up our development environment by issuing the following commands:
    * mkdir HelloEthereum
    * cd HelloEthereum
    * truffle init
    * cd contracts
4. We will now create a HelloWorld contract in the contracts directory. Using the text editor of your choice, create a file in the current directory and paste the following contract code. Save the file as `HelloWorld.sol`.
    ```solidity
    pragma solidity >=0.4.22 <0.6.0;
    
    contract HelloWorld{
        function sayHello() public pure returns (string memory) {
            return "Hello, World!";
        }
    }
    ```
5. Next, compile the contract using Truffle:
    * In the terminal or command prompt, run: truffle compile
6. Now we will start preparing to deploy:
    * Change directory into migrations: cd ../migrations
    * Using the text editor of your choice, create a file named `2_helloworld_migration.js` in this directory and save the following code within it:
        ```javascript
        var MyContract = artifacts.require("HelloWorld");
        
        module.exports = function(deployer) {
            // deployment steps
            deployer.deploy(MyContract);
        };
        ```
    * For more information on migrations, see [this page][migrations-page].
    * If you are on Windows, you will need to also edit the `truffle-config.js` file in the HelloWorld directory. Specifically, find and uncomment the block beginning with `development: {` to declare the host and port for our blockchain. The port number should match the one shown by ganache-cli in the other terminal or command prompt, but it is most likely already correct with a value of 8545.
7. Deploy. In the terminal or command prompt, run the following command:
    * truffle migrate

## Credits
Dr. Debasis Bhattacharya  
Mario Canul  
Saxon Knight  

[migrations-page]: https://truffleframework.com/docs/truffle/getting-started/running-migrations#migration-files
