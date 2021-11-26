# Flash Loans

## Overview

C.R.E.A.M. is bringing Flash Loans to our money markets.

Flash Loans allow developers access to undercollateralized loans, provided that the borrowed amount (and fee) is returned within one transaction block.

Flash Loans offer a wide range of use cases, including democratized liquidations, arbitrage, collateral swapping and interest rate swapping.

Our Flash Loans feature is very similar to [AAVE Flash Loans V1](https://aave.com/flash-loans), except C.R.E.A.M. Flash Loans are implemented on crToken.

There are 3 major differences between C.R.E.A.M. Flash Loans and AAVE v1 Flash Loans:

1. Using C.R.E.A.M. Flash Loans devs **interact with flashLoanLender contract ,** instead of the lending pool.
2. C.R.E.A.M has deployed two flashLoanLenders that conform to EIP-3156; one for Lending and one for IronBank.
3. Fee is cheaper. C.R.E.A.M. fee is 0.03%

FlashloanLender: [0xb7132898491431B63c7C90DF31F13dC6dC414b5a](https://bscscan.com/address/0xb7132898491431B63c7C90DF31F13dC6dC414b5a)

{% hint style="info" %}
Not all markets have Flash Loans
{% endhint %}

{% content-ref url="lending/lending-contract-address.md" %}
[lending-contract-address.md](lending/lending-contract-address.md)
{% endcontent-ref %}

## Step by step guide

Please refer to Ethereum mainnet's [documentation](https://docs.cream.finance/flash-loans#step-by-step-guide).
