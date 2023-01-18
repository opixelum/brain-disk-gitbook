# Gas

*Note: This document talks about gas in the context of blockchains using the
**EVM**. Gas may differ in other blockchains.*

## Introduction

Each transaction on the blockchain costs gas. Gas is used to pay for the
computational resources used to process the transaction. The total amount of
gas used by a transaction is the sum of the gas used by each operation in the
transaction.

The sender of a transaction pays for the gas used by the transaction. This
mechanism is used to pay the miners or validators for processing the
transaction, and to prevent spam transactions from being processed.

## Gas per operation

The gas usage of each operation is a constant number. The gas usage of each
operation is the same for all contracts. The gas usage of each operation is
the same for all transactions.

You can find the gas usage of each operation
[here](https://docs.google.com/spreadsheets/d/1n6mRqkBz3iWcOlRem_mO09GtSKEKrAsfO7Frgx18pNU/edit#gid=0).

## Gas Usage

The gas usage of a smart contract is determined by the number of operations
performed in the contract. The gas usage of each operation is a constant
number, and is the same for all contracts. The gas usage of a contract is
the sum of the gas usage of each operation performed in the contract.

## Gas Limit

The gas limit is the maximum amount of gas that can be used in a transaction.
If the gas usage of a transaction exceeds the gas limit, the transaction
will fail. The gas limit is set by the sender of the transaction.

## Gas Price

The gas price is the amount of gas that is paid for each unit of gas used in
a transaction. The gas price is set by the sender of the transaction.

## Gas Cost

The gas cost is the total amount of gas that is paid for a transaction. The
gas cost is equal to the gas limit multiplied by the gas price. The gas cost
is paid by the sender of the transaction.

## Gas Refund

The gas refund is the amount of gas that is refunded to the sender of a
transaction. The gas refund is equal to the gas limit minus the gas usage of
the transaction. The gas refund is paid by the sender of the transaction.

## Optimizing Gas Usage

- Use the correct data type for your variables. For example, use `uint8` for
variables that will never be greater than 255.

- Use the correct modifier for your variables. For example, use `constant`
for variables that will never change.

- Use the correct visibility for your functions. For example, a public function
will cost more gas than an internal function.

  | Function visibility | Description |
  |-------------------|-------------|
  | `public` | Can be called by anyone. |
  | `external` | Can only be called from outside the contract. |
  | `internal` | Can only be called from inside the contract. |
  | `private` | Can only be called from inside the contract that defines it. |

- Use the correct function modifier for your functions.

  | Function modifier | Description |
  |-------------------|-------------|
  | `view` | Does not modify the state of the contract. |
  | `pure` | Does not modify the state of the contract and does not read from the state of the contract. |
  | `payable` | Can receive Ether. |

- Use the correct storage location for your variables. For example, `memory`
variables will cost more gas than `calldata` variables because they are
copied to memory. See the `calldata` keyword as a ***read-only*** variable.

  | Storage location | Description |
  |------------------|-------------|
  | `memory` | Stored in memory. |
  | `storage` | Stored in storage. |
  | `calldata` | Stored in calldata. |

- Impose a size limit on strings with the `bytes` data type. For example, use
`bytes32` instead of `string` for strings that will never be greater than 32
characters.

- Use mappings instead of arrays when possible. Mappings are cheaper than
arrays because they don't have to be stored in a contiguous block of memory.

- Don't initialize variables to their default value, Solidity will do it for
you. If you do it, it means that you're initilizing the variable twice, which
will cost more gas.

  ```solidity
  uint8 a = 0; // Wrong
  uint8 a; // Right
  ```

- Use `unchecked` blocks to avoid overflow checks in for loops.

  ```solidity
  for (uint i; i < 100;) {
      unchecked {
          i++;
      }
  }
  ```

- Use `public`/`external` functions as interfaces to your contract, then use
`internal` functions to do the actual work. This will save you gas because
`public`/`external` functions will cost more gas than `internal` functions.

  ```solidity
  function foo() public {
      _foo();
  }

  function _foo() internal {
      // Do something
  }
  ```

- In custom function modifiers, declare `error` instead of using a string in
`require` statements. This will save you gas because `require` costs more gas
than `error`. On top of that, call an internal function, like the pattern
defined in the previous point. This will save you gas because at compile time,
the compiler will inline the internal function, meaning that the bytecode will
be smaller by just containing the function call instead of the function body.

  ```solidity
  // Wrong
  modifer onlyOwner() {
      require(msg.sender == owner, "Only the owner can call this function.");
      _;
  }

  // Right
  error OnlyOwnerCanCallThisFunction();

  modifer onlyOwner() {
      _onlyOwner();
      _;
  }

  function _onlyOwner() internal view {
      if (msg.sender != owner) {
          revert OnlyOwnerCanCallThisFunction();
      }
  }
  ```

- Using the optimizer will save you gas. With a high `runs` value, the
optimizer will make your bytecode longer (so it will cost more gas to deploy)
but each operation will cost less gas. With a low `runs` value, the optimizer
will make your bytecode shorter (so it will cost less gas to deploy) but each
operation will cost more gas. A good tradeoff for the `runs` value is
**20,000**.
