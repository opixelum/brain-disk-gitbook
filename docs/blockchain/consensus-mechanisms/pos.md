# Proof of Stake (PoS)

## Definition

Consensus mechanism that uses a randomized process to figure out who gets a
chance to produce the next block, among nodes that have staked a certain amount
of cryptocurrency.

## Process to add a new block

1. A validator is pseudo-randomly selected to produce the next block.
2. The validator produces the block.
3. The validator broadcasts the block to the network.
4. The network accepts the block if it is valid.

## Validators

Validators are nodes eligible to produce a new block.

In order to become a validator, a node must stake a certain amount of
cryptocurrency.

## Pseudo-random election process

This is the algorithm used to select a validator among a pool of candidates.

*Each blockchain has its own algorithm with their own set of rules to select a
validator, in order to get the best combination possible for their respective
ecosystem.*

Here is a common algorithm, based on 3 factors:

- Staking age: it is the number of coins staked multiplied by the number of
days the coins have been staked. A specific amount of staking age is needed to
be selected by the algorithm;
- Node's wealth: the algorithm looks for nodes with the lowest hash values &
the highest stake values;
- Randomization.

In order to prevent large stake nodes from controlling the network, the staking
age of a validator is reset to 0 when it gets selected to forge a new block.

## Adding a new block

*Same as for the pseudo-random election process, each blockchain has its own
process & set of rules to add a new block.*

When a validator is selected, it verifies the validity of the transactions in
the mempool (space where new transactions are stored before getting inserted
into a block), stores them into a block, signs the block & broadcasts (or
proposes) the block to the whole network.

Other nodes (called attestors) verifies if there is any fraudulent transaction,
then vote if the block is valid or not.

If the block is valid (majority of "valid" votes), it is added to the
blockchain. If not, the validator is punished. It loses a part of it stake, or
more severely, get also blacklisted (that last action is called **slashing**).
Then, another validator is selected to re-produce the block.

## Pros

- Low energy consumption: no need to use lots of computing power & energy;
- Easy to participate: in PoW, against big mining farms, you need to buy
expensive hardware to get a chance to produce a block, . In PoS, you just need
to stake some cryptocurrency (minimal stake depends on the blockchain);
- Reduced centralization risk: since it's easier to participate, it allows more
people to participate securing the network;
- Less chance of 51% attack: thanks to the economic penalties for misbehavior,
51% attacks are more costly to an attacker compared to PoW;
- Less issuance of new coins is required to incentivize network participants.

## Cons

- Less tested (for the moment): Pos is younger & less tested than PoW;
- More complex: PoS is more complex to implement than PoW;

## References

- [Proof of Stake (Ethereum Docs)](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/)
- [What is Proof of Stake - Explained in Detail (Animation)](https://www.youtube.com/watch?v=YudpU58uYuM)
