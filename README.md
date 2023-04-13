# Full stack voting Dapp deployed on the celo blockchain

# INTRODUCTION
In recent years, the importance of secure and transparent voting systems has become increasingly clear. Traditional voting methods are often subject to human error, manipulation, and fraud, which can lead to inaccurate election results and a lack of trust in the democratic process. The emergence of blockchain technology has the potential to revolutionize the way we approach voting, providing a secure, decentralized, and tamper-proof system for recording and verifying votes. In this article, we will explore the concept of a full stack voting dapp deployed on the Celo blockchain, using Metamask to interact with the blockchain. We will provide an overview of the components of a full stack voting dapp, explain the benefits of the Celo blockchain for voting systems, and provide a step-by-step guide to using the dapp with Metamask. By the end of this article, you will have a clear understanding of how blockchain-based voting systems can improve the integrity of the democratic process and enhance voter trust.

# WHAT WE WILL BE CREATING
We will be creating a full stack dapp that will enable users to vote on which is their favorite social media platform.
![Screenshot (194)](https://user-images.githubusercontent.com/81447346/231892645-e4417906-a8e6-4e5d-93a6-30a1de959340.png)

# ANALIZING THE SMART CONTRACT

Voting is a fundamental aspect of democratic societies, allowing citizens to participate in the decision-making process and express their views. However, traditional voting systems are often subject to manipulation and fraud, which can undermine the integrity of the democratic process. The emergence of blockchain technology has opened up new possibilities for secure and transparent voting systems.

Smart contracts are self-executing contracts with the terms of the agreement between buyer and seller being directly written into lines of code. These contracts are stored on a blockchain, which provides a tamper-proof record of all transactions. One of the most promising applications of smart contracts is in the field of voting. The best part is that even if the voter open multiple accounts with the same private key he will still be able to vote only once

The smart contract presented above is a simple implementation of a voting system on the Ethereum blockchain using the Solidity programming language. The contract, named "Ballot," allows voters to cast their votes for one of four proposals: LinkedIn, Twitter, Youtube, or Tiktok. The contract has two main components: the Voter struct and the Proposal struct.

The Voter struct stores the weight of the voter, which determines the number of votes they can cast, whether they have already voted, and their vote choice. The Proposal struct stores the name of the proposal and the number of votes it has received.

The contract has a chairperson, who is the administrator of the voting process and can give the right to vote to other participants. The chairperson is assigned the weight of 1 by default, and all other voters start with a weight of 0. The giveRightToVote function allows the chairperson to give the right to vote to other participants, provided they have not already voted.

## Voting

The vote function is used by voters to cast their vote for one of the proposals. The function checks that the voter has the right to vote and has not already voted, and then updates the vote count for the chosen proposal.

Finally, the winningProposal and winnerName functions determine which proposal has received the most votes and returns its name. The contract can be extended to add more proposals, and the winningProposal and winnerName functions can be modified to return more detailed information about the results.

Overall, the Ballot smart contract provides a simple but effective example of how blockchain technology can be used to create secure and transparent voting systems. While this contract is not intended for use in real-world elections, it provides a starting point for the development of more sophisticated voting systems that could be used to ensure the integrity of democratic processes.

# OPENING A CELO ACCOUNT ON THE AFROJONES TESTNET IN META MASK
To continue you will need to have the metamask extension installed in your chrome. The next step will be to add the celo afrojomes network in your Meta mask account.
Here is a guide
https://docs.celo.org/blog/tutorials/3-simple-steps-to-connect-your-metamask-wallet-to-celo
We will be using the Alfajores Testnet

## FUNDING YOUR CELO WALLET
After that we will need fund our created wallet with celo, this is used as a gas fee for contract deployment  
https://faucet.celo.org/alfajores
After funding your metamask wallet with CELO, you will need to deploy your smart contract. Head over to remix and create a ** Ballot.sol ** file, paste the smart contract and click on deploy.

## CONTRACT DEPLOYMENT
A pop up will appear if you in your meta mask. After accepting the transaction it will be deployed to the celo blockchain. Copy your contract address and your abi we will need that later. Click on the solidity complier to view ypur ABI

![Screenshot (197)](https://user-images.githubusercontent.com/81447346/231894737-b209d78b-a717-40d8-81c7-35bb011c1cec.png)

## CREATING THE FRONTEND
Click on the link below to access my repo and copy the frontend

## CONNECTING THE FRONTEND TO THE BACKEND

### Ether js
To connect the frontend to the backend we use ether js. The ethers.js library aims to be a complete and compact library for interacting with the Ethereum Blockchain and its ecosystem. Since we are using just html, we will be using their script. Copy and paste the script below in your html file.

<script
      src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js"
      type="application/javascript"
    ></script>

### Fetching the data from your deployed contract
Create a <script> tag in html. this is where we will be writing our javascript. We will creating a function called get votes. store your abi in a variable and create your provider instance using ether js.
**  

const provider = new ethers.providers.Web3Provider(
          web3.currentProvider
        );

        contract = new ethers.Contract(
          "write your contract here",
          abi,
          provider
        );
        
        **


After adding the contract address the next step is to use the data in our frontend. We use the innerHTML command to append the data to our web app. Call the function using windows.load()
### Calling the vote function

In this function we create another abi variable. Then it waits for the user to connect their Ethereum wallet using the eth_requestAccounts method provided by the Ethereum JavaScript API.

Once the user has connected their wallet, the function creates a new instance of the Web3Provider class from the ethers.js library using the window.ethereum object. It then gets a signer object from the provider and creates a new instance of the Contract class from the same library using the address of a smart contract and its ABI (Application Binary Interface) as arguments.

The function then gets the value of an HTML select element with an ID of “ProposalSelect” and calls the vote() method of the contract with that value as an argument. The result of this call is assigned to a variable called castvote.

Finally, the function waits for the castvote promise to resolve and logs the transaction hash to the console and displays it. We call this function on click on the vote button. It will prompt the users metamask account and cast the vote





