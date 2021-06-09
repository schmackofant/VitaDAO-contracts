# ![VitaDAO](https://github.com/VitaDAO/whitepaper/blob/master/images/VitaDAO%20Opengraph.png?raw=true) 
# Smart Contracts

Governance Contracts for VitaDAO

# Setting Up


Navigate to the root of the repository directory in your terminal. 

If you don't have [hardhat](https://hardhat.org/) installed, you will need it.

Install the project dependencies (including hardhat): 

```Shell
yarn install
```

# Compiling the Contracts

To compile the contracts, just run: 

```Shell
yarn compile
```


Compile before you run locally or run the tests. 

## Instructions for deploying locally (dev chain)

Launch the chain locally: 

```Shell
# Start a local development chain
yarn start
```

You should see a message that says `Started HTTP and WebSocket JSON-RPC server at http://127.0.0.1:8545/` and then a list of accounts. 

Congratulations, at this point you can connect your wallet and begin to interact. 


# Running Tests

## Setting up for testing


Before you run the tests, you need to make two changes to the contracts. 

First, in [Raphael.sol](contracts/Raphael.sol) change the lines below to use the `for testing` values:

```Solidity
uint256 public CREATE_TO_VOTE_PROPOSAL_DELAY = 18500; // ~3 days
uint256 public VOTING_DURATION = 30850; // ~5 days

// for testing
// uint256 public CREATE_TO_VOTE_PROPOSAL_DELAY = 5;
// uint256 public VOTING_DURATION = 10;
```

Second, in [raphael.test.ts](test/Raphael/raphael.test.ts) change the value for these two constants to the much lower values in the comments: 

```Solidity
const CREATE_TO_VOTE_PROPOSAL_DELAY = 18500 //for shorter testing, use 5
const VOTING_DURATION = 30850 //for shorter testing, use 10
```

If you fail to do this, the tests will take forever and ultimately fail when javascript runs out of memory. If that happens, Ctrl-C out of that process and use the testing timeouts above. 

## Test Against Local Chain (as you ran above)

If you have the local development chain running, you can run the tests immediately from another terminal. 

```Shell
# Run the whole test suite
yarn test
```

The tests take a while to run. The test terminal may not update often while the tests run, but the terminal with the running hardhat server should show many transactions or mining of blocks occurring. Be patient, the should all pass after a while.

## Test if Local Chain Is Not Running

If there isn't already a local network running, you will first need to run: 

```Shell 
npx hardhat node
```
OR 
```Shell
yarn start
```

This will start a local network to which the tests can connect. Then you are free to run:

```Shell
# Run the whole test suite
yarn test
```

# Recompiling

If you need a fresh compile, you can get rid of all the build artifacts and clear the cache using: 
```Shell
yarn clean
```

# Deployment

This script is not ready. 


