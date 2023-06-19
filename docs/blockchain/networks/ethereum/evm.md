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

- Key-value permanent store that is part of the state;
- Key-value pairs = "slots";
- Values = 256 bits ***words*** or ***items***;
- Keys = Keccak256 hashes of their contract's address & the word;
- If a transaction tries to add an item that is too big, the transaction will
  be reverted;
- Data types smaller than 256 bits can be packed into a single slot. For this,
  developers must order the same data types from the smallest to the biggest:

```solidity
// Good
uint8 a;
uint16 b;
uint32 c;

// Bad
uint16 a;
uint8 b;
uint32 c;
```

- Mappings & dynamic arrays values are stored in different slots but contiguous;
- Strings have 1 storage slot for the length, then 1 slot for each 32 bytes of
  the string;
- A struct is stored in a single slot if it fits, otherwise it is stored in
  multiple contiguous slots.

## Opcode

### `STATICCALL`

- Similar to `CALL` but does not allow state modifications;
- Introduced in the [EIP-214](https://eips.ethereum.org/EIPS/eip-214);
- Used for `view` & `pure` functions.

### `DELEGATECALL`

- Calls another contract's function using the current contract's context (storage,
caller, value);
- Introduced in the [EIP-7](https://eips.ethereum.org/EIPS/eip-7);
- Used in proxy contracts.

## References

- [(1) Ethereum Virtual Machine (EVM) - Ethereum Developer Documentation](https://ethereum.org/en/developers/docs/evm/)
- [(2) Merkle Patricia Trie - Ethereum Developer Documentation](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)
