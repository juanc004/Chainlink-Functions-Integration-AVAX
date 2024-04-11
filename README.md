# Access Offchain Data With Chainlink Functions

Explore the integration of Chainlink Functions to fetch real-world data via external APIs directly into your smart contracts on the Avalanche Fuji network. This guide outlines the process to deploy a consumer contract that interacts with these APIs.

## Table of Contents

1. [Setup](#setup)
2. [Deployment Steps](#deployment-steps)
   - [Smart Contract Preparation](#step-1-smart-contract-preparation)
   - [Funding Your Wallet](#step-2-funding-your-wallet)
   - [Create Functions Subscription](#step-3-create-functions-subscription)
   - [Interacting with Chainlink Functions](#step-4-interacting-with-chainlink-functions)
   - [Weather Data with Chainlink Functions](#step-5-weather-data-with-chainlink-functions)
   - [Testing with External Contracts](#step-6-testing-with-external-contracts)
   - [Review and Repeat for Testing](#step-7-review-and-repeat-for-testing)
3. [Troubleshooting Common Issues with Chainlink Functions](#troubleshooting-common-issues-with-chainlink-functions)
4. [Resources and Tools](#resources-and-tools)
5. [Watch the Tutorial](#watch-the-tutorial)

## Setup

Prepare your development environment:

- **Wallet**: [Install MetaMask](https://metamask.io/) and configure it for the Avalanche Fuji network.
- **IDE**: Access smart contract development via [Remix IDE](https://remix.ethereum.org/).
- **Network**: Ensure MetaMask is connected to the Avalanche Fuji network (Custom network ID: 43113).

## Deployment Steps

### Step 1: Smart Contract Preparation

1. **Open Remix IDE**: Navigate to [Remix IDE](https://remix.ethereum.org/) and ensure you're signed in.
2. **Create `GettingStartedFunctionsConsumer.sol`**: In the "FILE EXPLORER" tab, click "Create New File" and name it `GettingStartedFunctionsConsumer.sol`.
3. **Deploy the Contract**: Follow the compilation and deployment prompts within Remix for the Avalanche Fuji network

### Step 2: Funding Your Wallet

Before creating a subscription, ensure your wallet is prepared:

1. **Acquire Testnet LINK**: Visit [Chainlink Faucets](https://faucets.chain.link/fuji) to get LINK tokens for the Fuji network. These tokens are necessary for funding your Functions subscription.
2. **Check ETH Balance**: Ensure you have a small amount of Fuji AVAX for transaction fees. You can acquire Fuji AVAX from the same faucet.

### Step 3: Create Functions Subscription

1. **Navigate to Chainlink Functions**: Open [Chainlink Functions](https://functions.chain.link/) and connect your MetaMask wallet to the Fuji network.
2. **Create a New Subscription**: Click "Create New Subscription", name it "Chainlink Bootcamp 2024", and add your email. Fund this subscription with at least 5 LINK tokens.
3. **Register Your Contract**: Add your deployed `GettingStartedFunctionsConsumer.sol` contract as a consumer.

   > **Important**: Confirm you are connected to the Fuji network, have at least 5 LINK, and have listed your contract correctly as a consumer.

### Step 4: Interacting with Chainlink Functions

1. **Prepare to Send a Request**: In Remix, with your `GettingStartedFunctionsConsumer.sol` contract deployed and selected, find the `sendRequest` function in the deployed contract's methods.
2. **Make an API Call**: Execute the `sendRequest` function by inputting your subscription ID and setting `args` to `[1]`. This action requests data from the Star Wars API, aiming to fetch information about a specific character.

### Step 5: Weather Data with Chainlink Functions

1. **Deploy Another Contract**: Within Remix, create and deploy `WeatherFunctions.sol` following a similar process as before. Use the same subscription ID for this new deployment.
2. **Add to Chainlink Functions**: Go back to the Chainlink Functions dashboard and add your `WeatherFunctions` contract as another consumer.
3. **Execute Temperature Query**: Within Remix, find the deployed `WeatherFunctions` contract. Use the `getTemperature` function, inputting a city name (e.g., "Dallas"), to request current temperature data.

### Step 6: Testing with External Contracts

In this step, you'll interact with deployed contracts other than your own to observe Chainlink Functions in action across different use cases.

1. **Create a New Subscription**: If you wish to test with a separate subscription ID, revisit the [Chainlink Functions](https://functions.chain.link/) page to set up another subscription. This can be beneficial for isolating test cases or interacting with external contracts without affecting your original setup.
   
2. **Deploy Another Contract**: Optionally, you can deploy another instance of `GettingStartedFunctionsConsumer.sol` or `WeatherFunctions.sol` using this new subscription ID for varied testing.
   
3. **Interact Using "At Address"**: In Remix, locate the "Deploy & Run Transactions" panel. Utilize the "At Address" field to input the address of an external contract you want to interact with, such as JohnDoe's `WeatherFunctions.sol` contract. This allows you to call functions on contracts not deployed by you but are open for public interaction.

4. **Send Requests**: With the external contract loaded, try executing functions like `getTemperature`. This showcases how Chainlink Functions can be used by various contracts to access off-chain data.

### Step 7: Review and Repeat for Testing

After interacting with external contracts and fetching data:

1. **Review Data**: Use the `lastTemperature` function to check the results of your `getTemperature` call. For example, retrieving the temperature for "Dallas" might show "Dallas - ☀️ +14°C".

2. **Repeat with New Subscription**: Utilizing the new subscription ID, repeat the data fetching process. This practice helps in understanding how different subscriptions can be managed and utilized across multiple contracts.

3. **Document Observations**: Keep track of the responses and any differences observed when using different subscription IDs or interacting with various contracts. This can provide insights into the flexibility and power of Chainlink Functions.

4. **Explore Further**: Encourage experimentation by interacting with a variety of API endpoints and external contracts. Each interaction provides a learning opportunity and showcases the versatility of Chainlink Functions in real-world applications.

### Additional Tips for Success

- **Stay Organized**: Keep a record of your subscription IDs and associated contracts. This helps in managing multiple tests and understanding their outcomes.
- **Engage with the Community**: If you encounter unique scenarios or challenges, reaching out to the Chainlink community can provide additional perspectives and solutions.

## Resources and Tools

Enhance your project with additional support:

- [Chainlink Functions Documentation](https://docs.chain.link/chainlink-functions/getting-started)
- [Avalanche Fuji Testnet Information](https://docs.chain.link/chainlink-functions/supported-networks#avalanche-fuji-testnet)
- [Network Configuration with Chainlist](https://chainlist.org/chain/43113)
- [Developing in Remix IDE](https://remix.ethereum.org)
- [Experimenting in Chainlink Functions Playground](https://functions.chain.link/playground)
- [Understanding Chainlink Functions](https://blog.chain.link/ways-to-use-chainlink-functions/)

## Troubleshooting Common Issues

While integrating Chainlink Functions, you might encounter several errors. Below, we dive into why these issues occur and how to effectively address them:

### Gas Estimation Error

This error typically signals trouble with transaction execution, which can be due to various factors:

- **Insufficient Funds in Functions Subscription**: Your Chainlink Functions subscription may lack enough LINK tokens to cover the transaction.
  
- **Lack of AVAX for Gas Fees**: There might not be enough AVAX in your wallet to pay the gas fees for executing the function.
  
- **Funding or Deploying on the Incorrect Network**: Double-check if you've funded your subscription or deployed your contract on the intended network (e.g., Avalanche Fuji).
  
- **Interacting with an Underfunded Address**: The contract address you're interacting with might not have a sufficient LINK balance to process the transaction.

**Solutions**:
- Fund your Chainlink Functions subscription with sufficient LINK tokens.
- Ensure your wallet has enough AVAX for gas fees.
- Verify that both your funding and deployment are on the correct network.
- Check the LINK balance of the contract you're interacting with; it must have enough LINK to process requests.

### Subscription Not Found Error

Encountering this error message indicates a mismatch or absence of the specified subscription ID on the expected network.

**Reasons**:
- **Incorrect Network**: You might be on a different network in your MetaMask than where your subscription was created (e.g., using Fuji network settings but the subscription is on Mumbai).
- **Wrong Subscription ID**: There's a possibility of entering an incorrect subscription ID or using an ID that does not exist.

**Solutions**:
- Confirm that your MetaMask is set to the same network where your subscription exists (e.g., Avalanche Fuji).
- Verify the subscription ID for accuracy. If necessary, go back to the [Chainlink Functions dashboard](https://functions.chain.link/) to check your subscriptions and ensure you're using the correct ID.

By understanding the underlying reasons for these common issues and following the provided solutions, you can navigate through the troubleshooting process more effectively and minimize disruptions in your project development with Chainlink Functions.

## Watch the Tutorial

Watch our [tutorial on YouTube](https://www.youtube.com/watch?v=s-ilo2Ex8H0) for a step-by-step project walkthrough.
