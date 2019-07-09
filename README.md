# Udacity Blockchain Capstone

[Capstone: Real Estate Marketplace](https://classroom.udacity.com/nanodegrees/nd1309/parts/48aa25b7-ae11-4349-93c3-c83361e8fa4c/modules/43d200d0-9ce6-4e20-b1c0-39a4e00ac275/lessons/d35b025b-01b3-4bd9-acf5-e8bb5b88f00c/concepts/4d2728c0-0886-4ba2-aa61-bf1362bc3664)

In this project I minted my own tokens to represent my title to the housing properties, and then placed them on a blockchain market place (OpenSea) for others to purchase.

I used the ZoKrates toolbox implement zk-SNARKs (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge) proofs to create a verification system which can prove I have title to the property without revealing that specific information on the property. 


## Project Environment
Execute this command to find out:`truffle v`
```
Truffle v5.0.25 (core: 5.0.25)
Solidity - ^0.4.25 (solc-js)
Node v10.16.0
```

## Project Repository

My project can be cloned: 
```
git clone https://github.com/margaretycf/Blockchain-Capstone
```

## Zokrates Installation and Proof Generation

1. Install Docker to be able to run Zokrates using the instructions [here](https://docs.docker.com/install/)

2. Run ZoKrates docker container:
```
docker run -v <path to your project folder>:/home/zokrates/code -ti zokrates/zokrates /bin/bash
```

3. Compile the program written in ZoKrates DSL
```
/path/to/zokrates compile -i <program_name>.code
```
4. Generate the Trusted Setup
Now take the 'flattened' code, which is a circuit and go through a 'trusted setup' Repeat this process, every-time the program.code changes Two keys are generated - 'proving.key' and 'verification.key'
```
/path/to/zokrates setup
```

5. Compute Witness
Having gone through the 'trusted setup' let's compute our 'witness' who knows the answer and it generates a witness file with computation steps
```
/path/to/zokrates compute-witness -a <a> <b> ... <n>
```

6. Generate Proof
Next step is to 'generate our proof' based on the above 'witness' A proof.json file is generated in this step
```
/path/to/zokrates generate-proof
```

7. Export Verifier
Last but never the least, let's generate our 'verifier' smart contract
```
path/to/zokrates export-verifier
```

There is more information regarding these steps in the course material of [Getting Started with Zokrates](https://classroom.udacity.com/nanodegrees/nd1309/parts/48aa25b7-ae11-4349-93c3-c83361e8fa4c/modules/43d200d0-9ce6-4e20-b1c0-39a4e00ac275/lessons/d35b025b-01b3-4bd9-acf5-e8bb5b88f00c/concepts/a431480a-c27c-437d-a911-8d442d2c8624).


## Running Tests

1. Install npm packages

In a terminal window, go to the project directory and execute:
```
npm install
```

2. Launch Ganache locally
```
ganache-cli -m "enroll crazy just label faith garlic derive outer clerk recipe differ winter"
```

3. In a separate terminal window, go to the project's 'eth-contracts' directory, compile smart contracts:
```
truffle compile --reset
```

4. Run the tests:
```
truffle test
```
All 11 tests should pass.


## Migrate to Rinkeby Network

I started Metamask with my account in the Chrome browser and deployed the smart contracts to the Rinkeby network. In the project's 'eth-contracts' directory:
```
truffle migrate --reset --network rinkeby
```

### Contract Address Deployed to Rinkeby Network
```
SolnSquareVerifier Contract Address: 0xB7cE82018ae90032E5EC68ED293aFfAc8494A5A1
```

### Contract ABI
```
[
    {
      "constant": true,
      "inputs": [
        {
          "name": "interfaceId",
          "type": "bytes4"
        }
      ],
      "name": "supportsInterface",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "name",
      "outputs": [
        {
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "getApproved",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "approve",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "totalSupply",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "from",
          "type": "address"
        },
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "transferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "_myid",
          "type": "bytes32"
        },
        {
          "name": "_result",
          "type": "string"
        }
      ],
      "name": "__callback",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "verifier",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "owner",
          "type": "address"
        },
        {
          "name": "index",
          "type": "uint256"
        }
      ],
      "name": "tokenOfOwnerByIndex",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "_myid",
          "type": "bytes32"
        },
        {
          "name": "_result",
          "type": "string"
        },
        {
          "name": "_proof",
          "type": "bytes"
        }
      ],
      "name": "__callback",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "mint",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "from",
          "type": "address"
        },
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "safeTransferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "index",
          "type": "uint256"
        }
      ],
      "name": "tokenByIndex",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "ownerOf",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "owner",
          "type": "address"
        }
      ],
      "name": "balanceOf",
      "outputs": [
        {
          "name": "",
          "type": "uint256"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "symbol",
      "outputs": [
        {
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "approved",
          "type": "bool"
        }
      ],
      "name": "setApprovalForAll",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "from",
          "type": "address"
        },
        {
          "name": "to",
          "type": "address"
        },
        {
          "name": "tokenId",
          "type": "uint256"
        },
        {
          "name": "_data",
          "type": "bytes"
        }
      ],
      "name": "safeTransferFrom",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "tokenURI",
      "outputs": [
        {
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "contractOwner",
      "outputs": [
        {
          "name": "",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [],
      "name": "baseTokenURI",
      "outputs": [
        {
          "name": "",
          "type": "string"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": true,
      "inputs": [
        {
          "name": "owner",
          "type": "address"
        },
        {
          "name": "operator",
          "type": "address"
        }
      ],
      "name": "isApprovedForAll",
      "outputs": [
        {
          "name": "",
          "type": "bool"
        }
      ],
      "payable": false,
      "stateMutability": "view",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "pausableState",
          "type": "bool"
        }
      ],
      "name": "setPausableState",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "newOwner",
          "type": "address"
        }
      ],
      "name": "transferOwnership",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "inputs": [
        {
          "name": "verifierAddress",
          "type": "address"
        }
      ],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "tokenId",
          "type": "uint256"
        },
        {
          "indexed": false,
          "name": "owner",
          "type": "address"
        }
      ],
      "name": "SolutionAdded",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "from",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "to",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "Transfer",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "owner",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "approved",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "tokenId",
          "type": "uint256"
        }
      ],
      "name": "Approval",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": true,
          "name": "owner",
          "type": "address"
        },
        {
          "indexed": true,
          "name": "operator",
          "type": "address"
        },
        {
          "indexed": false,
          "name": "approved",
          "type": "bool"
        }
      ],
      "name": "ApprovalForAll",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "callerAddress",
          "type": "address"
        }
      ],
      "name": "Paused",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "callerAddress",
          "type": "address"
        }
      ],
      "name": "Unpaused",
      "type": "event"
    },
    {
      "anonymous": false,
      "inputs": [
        {
          "indexed": false,
          "name": "newOwner",
          "type": "address"
        }
      ],
      "name": "OwnershipTransfered",
      "type": "event"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "tokenId",
          "type": "uint256"
        },
        {
          "name": "owner",
          "type": "address"
        },
        {
          "name": "key",
          "type": "bytes32"
        }
      ],
      "name": "addSolution",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    },
    {
      "constant": false,
      "inputs": [
        {
          "name": "tokenId",
          "type": "uint256"
        },
        {
          "name": "owner",
          "type": "address"
        },
        {
          "name": "a",
          "type": "uint256[2]"
        },
        {
          "name": "b",
          "type": "uint256[2][2]"
        },
        {
          "name": "c",
          "type": "uint256[2]"
        },
        {
          "name": "input",
          "type": "uint256[2]"
        }
      ],
      "name": "mintNewToken",
      "outputs": [],
      "payable": false,
      "stateMutability": "nonpayable",
      "type": "function"
    }
  ]
  ```


## Mint Tokens

I minted my tokens using [MyEtherWallet](https://vintage.myetherwallet.com/#contracts)
Tutorials of using MyEtherWallet to mint a token can be found in the video [Mint a token using MyEtherWallet](https://www.youtube.com/watch?v=8MChn-NJJB0&feature=youtu.be).


### Blockchain Transaction Details of My Minted Tokens
```
SolnSquareVerifier address: 0xB7cE82018ae90032E5EC68ED293aFfAc8494A5A1

SquareVerifier address:     0x9bAF4027F22cA1b3a68900aeE3dE94Ae4Ad06fcf

Transaction 1 hash token 11 
https://rinkeby.etherscan.io/tx/0x457fca35aecf5cc7fea67df55069d4fe70a71c7fc8469cc581297bb687967c76


Transaction 2 hash token 12 
https://rinkeby.etherscan.io/tx/0x9546437e98ed3f28cdf848c0a26f1f4806889faca361a4af0415aa136037ab38


Transaction 3 hash token 25 
https://rinkeby.etherscan.io/tx/0xd54e43ee5c1348ae56504714a039c810ad5953e1561f7416952be5ec3de5da53


Transaction 4 hash token 26 
https://rinkeby.etherscan.io/tx/0x40c05aabf751c0a294d1d57b838c1c5bd8972bb1f1f4155bd99e7c680e6cd3d8


Transaction 5 hash token 30 
https://rinkeby.etherscan.io/tx/0x8534c7dd86c9557b17553e453d2859af7c37384344f98eff961bbf9638b490f4


Transaction 6 hash token 33 
https://rinkeby.etherscan.io/tx/0x7e2c360bb01a25438bbd6a8768548cebc2183ad2f1ef57831e7b16a8467a0663



Transaction 7 hash token 50 
https://rinkeby.etherscan.io/tx/0x1c7c84a1dd5973677d07e99a1f9ca2a3343e06e409d1f63b9adbe7ac6d7a2a76


Transaction 8 hash token 52 
https://rinkeby.etherscan.io/tx/0x2821afe9d76d2f1a0c1aba8843eb1afbdab1c96a6389e5b854cb0d9759f346e8



Transaction 9 hash token 65 
https://rinkeby.etherscan.io/tx/00x44c28115854e7ea41ae79a7ce05b91590221876aaf471b7cdcf6ae0a9eaab172


Transaction 10 hash token 97 
https://rinkeby.etherscan.io/tx/0x21199dde54515dfb37cc12d7e7ae69b1e410e0a51f3ad0e735dcf98cb8f2fc45

```


## OpenSea Marketplace

https://rinkeby.opensea.io/assets/<asset_contract_address>/<token_id>
https://rinkeby.opensea.io/assets/0xB7cE82018ae90032E5EC68ED293aFfAc8494A5A1/11


I went to the web site link of [OpenSea storefront](https://rinkeby.opensea.io/get-listed/step-two) to go to the storefront creator. I then walked through the process of getting all of my items to show up on OpenSea by:

- entering my contract address '0xB7cE82018ae90032E5EC68ED293aFfAc8494A5A1'
- and then loading items


The tokens are listed under the name "Real Estate Marketplace V11" on Opensea. It can be accessed [here](https://rinkeby.opensea.io/assets/real-estate-marketplace-v11) by searching the name "Real Estate Marketplace V11".


# Project Resources

* [Remix - Solidity IDE](https://remix.ethereum.org/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Truffle Framework](https://truffleframework.com/)
* [Ganache - One Click Blockchain](https://truffleframework.com/ganache)
* [Open Zeppelin ](https://openzeppelin.org/)
* [Interactive zero knowledge 3-colorability demonstration](http://web.mit.edu/~ezyang/Public/graph/svg.html)
* [Docker](https://docs.docker.com/install/)
* [ZoKrates](https://github.com/Zokrates/ZoKrates)
