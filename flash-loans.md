---
description: Conforming to EIP-3156
---

# Flash Loans

C.R.E.A.M. is bringing Flash Loans to our money markets.

Flash Loans allow developers access to undercollateralized loans, pending the borrowed amount (and fee) is returned within one transaction block.

Flash Loans offer a wide range of use cases, including democratized liquidations, arbitrage, collateral swapping and interest rate swapping.

Our Flash Loans feature are very similar to [AAVE Flash Loans V1](https://aave.com/flash-loans), except C.R.E.A.M. Flash Loans are implemented on crToken.

There are 3 major differences between C.R.E.A.M. Flash Loans and AAVE v1 Flash Loans:

1. Using C.R.E.A.M. Flash Loans devs interact with crToken, instead of the lending pool. To execute Flash Loans, users must know specific asset address of crToken
2. There is an addition argument initiator when the callback function executeOperation is invoked. The initiator is the msg.sender who calls the Flash Loans function.
3. Fee is cheaper. C.R.E.A.M. fee is 0.03%

{% hint style="info" %}
Not all markets have Flash Loans
{% endhint %}

{% content-ref url="lending/lending-contract-address.md" %}
[lending-contract-address.md](lending/lending-contract-address.md)
{% endcontent-ref %}

## Step by step guide

Please refer to Ethereum mainnet's [documentation](https://docs.cream.finance/flash-loans-1/flash-loans-eip-3156).
