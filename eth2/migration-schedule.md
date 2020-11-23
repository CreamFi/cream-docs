# Migration Schedule

## Ethereum 2.0 Migration Schedule

ETH2 will be released in several phases.

![](../.gitbook/assets/timeline_deposit_contract_launch.d09b4bf3.svg)

Phase 0 contains all of the machinery behind ETH2's PoS consensus, it tracks the validators and their balances.

Phase 1 handles adding, storing, and retrieving the data associated with ETH2's shards.

Phase 1.5 updates Ethereum as we know it today from PoW to PoS by making it a shard under 2. 

Phase 2 adds execution to the remaining ETH2 shards which enables smart contracts to run on all of the shards.

### The Beacon Chain

[Beacon Chain](https://ethereum.org/en/eth2/beacon-chain/) is known as phase 0 in the roadmap. The beacon chain doesn't change anything about the Ethereum we use today. It will coordinate the network, and introduces proof-of-stake to the Ethereum ecosystem.

This is estimated to deliver in Dec 01, 2020.

### Shard Chains

[Shard Chains](https://ethereum.org/en/eth2/shard-chains/) is included in phase 1 and phase 2. Sharding is a multi-phase upgrade to improve Ethereum’s scalability and capacity. Shard chains spread the network's load across 64 new chains. They make it easier to run a node by keeping hardware requirements low.

This is estimated to deliver in 2021.

### The Docking

[Docking mainnet with ETH2](https://ethereum.org/en/eth2/docking/) is known as phase 1.5 in the roadmap. Eventually the current Ethereum mainnet will "dock" with the rest of the ETH2 upgrades. The docking will merge "ETH1" mainnet with the ETH2 beacon chain and sharding system. This will mark the end of proof-of-work for Ethereum, and the full transition to proof of stake.

This is estimated to deliver in 2022.

## C.R.E.A.M. to Ethereum 2.0 Schedule

### Conservative Migration

For the safety of the protocol, the migration process will be done conservatively.

We will not deposit a large batch to [ETH2 deposit contract](https://etherscan.io/address/0x00000000219ab540356cbb839cbe05303d7705fa) but only a small portion of total ETH before phase 0 starts. Once we verify that the whole mechanism is stable and robust after phase 0 kicks off, we will continuously deposit to ETH2 contract.

However, full plan is hard to reveal at the moment, for other than stable and safety there are still factors affecting our implementation like reward model and APR. The effect of these factors are dynamically changing and we will find the way to balance and optimize them all.

