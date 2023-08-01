# Blockchain Notarization

## Introduction

- Notarization in blockchain: Record and verify digital documents or
  transactions on a blockchain network.
- Purpose: Authenticate and ensure the integrity of the information.

## How It Works

- **Step 1**: Convert item to be notarized into a digital document (if not
  already).
- **Step 2**: Create a cryptographic hash of this digital document.
- **Step 3**: Add the hash to the blockchain.
- **Step 4**: Authenticate the document at any time by repeating the hashing
process and comparing it with the one stored on the blockchain.

## Benefits of Blockchain Notarization

- **Integrity**: Ensures the integrity of the document as even the slightest
  change in the document would result in a different hash.
- **Decentralization**: Blockchain's distributed nature ensures multiple copies
  of the same data, reducing risk of data loss or tampering.
- **Transparency**: All transactions are transparent and can be tracked back
  to their origin.
- **Cost-effective**: Reduces the need for third-party services, thus saving
  cost.

## Notarization in Smart Contracts

- Smart contracts can automate the notarization process on blockchain.
- Typically involves creating a smart contract function that records the hash
of a document and timestamp of notarization.
- Can later verify notarization by comparing the stored hash with the hash of
the document in question.

## Use Cases

- **Supply Chain**: Authenticating and tracking items through the supply chain.
- **Real Estate**: Documenting ownership and transfer of properties.
- **Intellectual Property**: Proving ownership of digital creations like music,
art, and literature.
- **Certificates**: Authenticating educational, professional, or other types
of certificates.

## Considerations

- **Privacy**: Public blockchains are transparent, which may not be suitable for
sensitive documents.
- **Gas Fees**: Transaction costs on certain blockchains like Ethereum can be
  high.
- **Storage**: While blockchain can store small amounts of data like hashes,
storing larger data is often done off-chain.
