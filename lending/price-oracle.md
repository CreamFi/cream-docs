---
description: How C.R.E.A.M. Finance get token price
---

# Price Oracle

{% hint style="info" %}
We have Chainlink as our main price oracle
{% endhint %}

### Chainlink

For the following tokens, we use price feed provided by Chainlink:

ETH / BTC / USDT / USDC / YFI / COMP / BAL / LINK / CRV / BUSD / UNI / wNXM / AAVE / DAI / 1INCH / CEL / COVER / FTT / HEGIC / KP3R / MTA / OMG / SRM / SNX / sUSD / SUSHI / CREAM / DPI / UST / FTM

For the following BTC-pegged tokens, we use BTC price instead:

* WBTC
* renBTC
* BBTC
* HBTC
* tBTC

### Contract

For the following tokens, we fetch price from contracts directly:

yUSD / yETH / yCRV / xSushi / bBadger

### C.R.E.A.M. Finance

For the other tokens, we use our own price oracle to get the price.

### Price Oracle Address

| Contract | Address |
| :--- | :--- |
| v1PriceOracle | [0x4250A6D3BD57455d7C6821eECb6206F507576cD2](https://etherscan.io/address/0x4250A6D3BD57455d7C6821eECb6206F507576cD2) |
| PriceOracleProxy | [0x940ce2a25b0BA48d213AcC13AbC21d9Fee2Ed6Dd](https://etherscan.io/address/0x940ce2a25b0BA48d213AcC13AbC21d9Fee2Ed6Dd) |
| ~~PriceOracleProxy \(deprecated\)~~ | [0x9a5135157a74b753d11197a821e7f199f5b2fed0](https://etherscan.io/address/0x9a5135157a74b753d11197a821e7f199f5b2fed0) |
| ~~PriceOracleProxy \(deprecated\)~~ | [0x4B7dbA23beA9d1a2d652373bcD1B78b0E9e0188a](https://etherscan.io/address/0x4B7dbA23beA9d1a2d652373bcD1B78b0E9e0188a) |

