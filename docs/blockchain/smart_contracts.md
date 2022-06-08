# Smart contracts

## Abstract contract

Abstract contracts are contracts that have at least one function without its implementation.

An instance of an abstract cannot be created.

Abstract contracts are used as base contracts so that the child contract can
inherit and utilize its functions.

The abstract contract defines the structure of the contract and any derived
contract inherited from it should provide an implementation for the incomplete
functions.

If the derived contract is also not implementing the incomplete functions then
that derived contract will also be marked as abstract. 


## Approve/Allow

There are two transactions needed for transfering ERC-20 tokens: 
- token approval;
- price & amount setting.

Both token holder and DApp developers benefit from the approval step:

- Token holder give permission for the smart contract to transfer up to a
certain amount of token (called an allowance), so that the smart contract will
only ever be able to transfer the approved token amount.

- DApp developers are sure that the smart contract functions properly: by
approving an amount of token, the smart contract is allowed to validate how
much token the holder truly has.
