# Smart contract

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
