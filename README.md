
# Voting Smart Contract

This repository contains a Solidity smart contract for a voting system. The contract allows for the creation of a ballot with multiple proposals and enables users to vote on those proposals. The contract also includes functions to manage voter rights and determine the winning proposal.

## Overview

The `Ballot` smart contract allows a chairperson to:
- Set up proposals for voting.
- Grant voting rights to specific addresses.
- Record votes from eligible voters.
- Determine and retrieve the winning proposal based on vote count.

## Features

- **Proposal Management**: Initialize a list of proposals for voting.
- **Voter Management**: Grant voting rights to addresses and ensure voters can only vote once.
- **Voting Process**: Allow registered voters to cast their votes for proposals.
- **Result Calculation**: Determine the winning proposal based on the highest vote count.

## Contract Functions

### Constructor

- `constructor(bytes32[] memory proposalNames)`: Initializes the contract with a list of proposals.

### Voter Management

- `function giveRightToVote(address voter)`: Grants voting rights to a specified address. Only the chairperson can call this function.

### Voting

- `function vote(uint proposal)`: Allows an address with voting rights to cast a vote for a specific proposal. The vote count for the selected proposal is incremented.

### Results

- `function winningProposal() public view returns (uint winningProposal_)`: Returns the index of the proposal with the highest vote count.

- `function winningName() public view returns (bytes32 winningName_)`: Returns the name of the proposal with the highest vote count.

## Usage

1. **Deploy the Contract**: Deploy the `Ballot` contract using a Solidity-compatible environment, such as Remix or Truffle.

2. **Initialize Proposals**: Use the constructor to initialize the contract with a list of proposal names.

3. **Grant Voting Rights**: Use the `giveRightToVote` function to grant voting rights to addresses.

4. **Cast Votes**: Eligible addresses can use the `vote` function to vote for proposals.

5. **Retrieve Results**: Use `winningProposal` and `winningName` to get the proposal with the highest vote count.

## Requirements

- Solidity version `^0.8.0`
- A Solidity-compatible development environment (e.g., Remix, Truffle)

## Example

Example of interacting with the Ballot contract:

Assuming `ballotContract` is an instance of the deployed Ballot contract:

- **Grant voting rights**:

  ```javascript
  await ballotContract.giveRightToVote('0xAddress');
  ```

- **Cast a vote for proposal index 1**:

  ```javascript
  await ballotContract.vote(1);
  ```

- **Get the winning proposal**:

  ```javascript
  const winningProposalIndex = await ballotContract.winningProposal();
  const winningProposalName = await ballotContract.winningName();
  ```

