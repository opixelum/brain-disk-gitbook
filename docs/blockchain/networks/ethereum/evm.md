# Ethereum Virtual Machine (EVM)

## Definition

Turing-complete virtual machine that executes smart contracts on the Ethereum blockchain.

## State

- Ethereum is a distributed state machine;
- The machine state (or simply "state") is a data structure that keeps a record
of all changes made to the blockchain like all accounts balances, all
contracts, etc;
- State is stored in a modified Merkle Patricia Trie (MPT);
- State can change from block to block.
- Rules for state changes are defined by the EVM.

## Storage

- Storage is a key-value permanent store that is part of the state;
- Key-value pairs are called "slots";
- Values are called ***words*** or ***items***, and are 256-bit (32 bytes)
long;
- Keys are Keccak-256 (so 32 bytes long) hashes of the their contract address
and the word;
- If a transaction tries to add an item that is too big, the transaction will
be reverted;

## References

- [(1) Ethereum Virtual Machine (EVM) - Ethereum Developer Documentation](https://ethereum.org/en/developers/docs/evm/)
- [(2) Merkle Patricia Trie - Ethereum Developer Documentation](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)