# weabove
This repository contains the technical information and scripts to verify the untampered mint of WeAbove.

## Contract source code and Network?
The contract address is 0xd0aaaC09E7f9b794FAfA9020a34aD5B906566A5C on Ethereum Mainnet. The code source is published on etherscan https://etherscan.io/address/0xd0aaaC09E7f9b794FAfA9020a34aD5B906566A5C#code

## What are the different phases of the mint?
- Only Access List:  block.timestamp >= 1662652800 (september 8 2022, 4pm UTC) 
- Access List and Raffle: block.timestamp >= 1662652800 + 1h (september 8 2022 5pm UTC)
- Public: block.timestamp >= 1662652800 + 3h (september 8 2022 7pm UTC)

## How many NFTs can be minted per wallet?
If your wallet exists in the Access List you have 3 slots, else 2 slots.

## How to premint?
To premint, you must provide a proof that you are in one of the two lists (whitelist or raffle) and transfer 0.15 eth

## How to generate a proof?
By using the https://mint.weabove.io frontend, the application generates the proof for the connected wallet and passes it as a parameter of the mint function of the smart contract. 
You can also use a standard library like https://www.npmjs.com/package/merkletreejs to generate proof that a wallet exists in the tree.

## Can the metadata change between the mint and the reveal?
No, the contract contains a hash of metadata and the shuffle algorithm that will be used for the reveal. 
At the time of the reveal, the preimage of the metadata hash (the concatenation of all the meta-data) will be published in order to establish that no post-deployment manipulation has been done.

## Can the allocation of NFTs be manipulated at the reveal?
No, a random number provided by an onchain oracle (chanlink) will serve as seed for a shuffle algorithm whose source code is published in this repository.

This design allows anyone to verify that from a random number generated in a trustless way, the assignment of NFTs is consistent with the result of the shuffle.
