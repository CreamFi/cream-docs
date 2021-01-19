---
description: How C.R.E.A.M. Finance get token price
---

# Price Oracle

{% hint style="info" %}
Currently we have Chainlink, yVault and curve.fi as third-party price oracle
{% endhint %}

### Chainlink

ETH / LINK / COMP / BAL / YFI / BUSD / USDT / USDC / UNI / wNXM / AAVE / DAI / CRV

For the following BTC-pegged token, we use BTC price instead:

* renBTC
* BBTC
* HBTC

### yVault

yUSD / yETH

### Curve.fi

yCRV

### C.R.E.A.M. Finance

For the other tokens, we use our own price oracle to get the price.

| Contract | Address |
| :--- | :--- |
| PriceOracleProxy | [0x4B7dbA23beA9d1a2d652373bcD1B78b0E9e0188a](https://etherscan.io/address/0x4B7dbA23beA9d1a2d652373bcD1B78b0E9e0188a) |
| v1PriceOracle | [0x4250A6D3BD57455d7C6821eECb6206F507576cD2](https://etherscan.io/address/0x4250A6D3BD57455d7C6821eECb6206F507576cD2) |

