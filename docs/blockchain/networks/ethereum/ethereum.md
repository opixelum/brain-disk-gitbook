# Ethereum

## Introduction

Ethereum is blockchain with smart contract functionality.

It was conceived in 2013 by Vitalik Buterin and released the July 30th 2015.
Also, Ethereum should get a major update in June 2022.

For Vitalik Buterin, blockchains could benefit from other applications besides
money. Moreover, it needed a more robust language for application development,
in order to link real-world assets such as stocks and property, to the
blockchain.

## Token Standards (ERC)

ERC (Ethereum Request for Comments) help ensure smart contracts remain
composable, so any token using a standard is compatible with any other
smart contract using the same standard.

Here are the different ERC:

- [ERC-20 (common token)](#erc-20)
- [ERC-165](#erc-165)
- [ERC-721 (NFT)](#erc-721)
- [ERC-777](#erc-777)
- [ERC-1155](#erc-1155)
- [ERC-4626](#erc-4626)

### ERC-20

The ERC-20, proposed by Fabian Vogelsteller in November 2015, is a standard
interface for fungible (interchangeable) tokens, like voting tokens, staking
tokens or virtual currencies.

Provided functionalities:

- transfer tokens from one account to another
- get the current token balance of an account
- get the total supply of the token available on the network
- approve whether an amount of token from an account can be spent by a
third-party account

### ERC-721

The ERC-721, proposed by William Entriken, Dieter Shirley, Jacob Evans,
Nastassia Sachs in January 2018, is a standard interface for Non-Fongible
Tokens (NFT), like artworks, ENS, lands in a metaverse or positions in DeFi.

Provided functionalities:

- transfer tokens from one account to another
- get the current token balance of an account
- get the owner of a specific token
- get the total supply of the token available on the network
- approve whether an amount of token from an account can be spent by a
third-party account

### ERC-777

_Coming soon_

### ERC-1155

_Coming soon_

### ERC-4626

_Coming soon_

## Gas

- Unit of measure for the amount of computational effort required to execute
  specific operations on the Ethereum network;
- Gas is paid in Gwei (1 Gwei = 0.000000001 ETH);
- Gas is used to pay for transactions fees.

## Gas & energy correlation

Since gas is a unit of measure for the amount of computational effort required,
the more gas is required for a function, the more energy is required. But this
can be negligible, depending on various factors:

- Hardware used to validate transactions & running smart contracts;
- Number of nodes (every nodes must validate the transaction);
- Number of users (multiply the gas cost of a function by the number of users
  using it).
- ...
