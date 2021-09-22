---
description: How C.R.E.A.M. Finance get token price
---

# Price Oracle

{% hint style="info" %}
We have Chainlink as our main price oracle
{% endhint %}

### Chainlink

For the following tokens, we use price feed provided by Chainlink:

ETH / BTC / USDT / USDC / YFI / COMP / BAL / LINK / CRV / BUSD / UNI / wNXM / AAVE / DAI / 1INCH / CEL / COVER / FTT / HEGIC / KP3R / MTA / OMG / SRM / SNX / sUSD / SUSHI / CREAM / DPI / UST / FTM / RUNE / PERP / OCEAN / RAI / RARI / HUSD / AKRO / AMP / SFI / MLN / VSP / GNO / SWAP / FEI / WOO / BNT / PAX / PAXG / LON / YGG / AXS / SAND / MANA / FRAX

For the following BTC-pegged tokens, we use BTC price instead:

* WBTC
* renBTC
* BBTC
* HBTC
* ibBTC

### LP Tokens

For SushiSwap LP tokens / Uniswap LP tokens, we use [Fair LP Pricing](https://blog.alphafinance.io/fair-lp-token-pricing/) introduced by [Alpha Finance](https://alphafinance.io/).

Price for underlying asset is retrieved from Chainlink price feed.

See [source code](https://github.com/CreamFi/compound-protocol/blob/master/contracts/PriceOracleProxy.sol#L288) for the implementation.

### Contract

For the following tokens, we fetch price from contracts directly:

yUSD \(v1\) / yETH / yCRV / xSushi / bBadger / yvCurve-IB / yvCurve-sETH / yvCurve-stETH / VVSP / yvWETH \(v2\) / yUSD \(v2\)

### C.R.E.A.M. Finance

For the other tokens, we use our own price oracle to get the price.

### Price Oracle Address

| Contract | Address |
| :--- | :--- |
| v1PriceOracle | [0x9A975fe93CFf8b0387b958adB9082B0ed0659AD2](https://etherscan.io/address/0x9a975fe93cff8b0387b958adb9082b0ed0659ad2) |
| PriceOracleProxy | [0x338EEE1F7B89CE6272f302bDC4b952C13b221f1d](https://etherscan.io/address/0x338EEE1F7B89CE6272f302bDC4b952C13b221f1d) |
| ~~PriceOracleProxy \(deprecated\)~~ | [0x647A539282e8456A64DFE28923B7999b66091488](https://etherscan.io/address/0x647a539282e8456a64dfe28923b7999b66091488#code) |
| ~~PriceOracleProxy \(deprecated\)~~ | [0x940ce2a25b0BA48d213AcC13AbC21d9Fee2Ed6Dd](https://etherscan.io/address/0x940ce2a25b0BA48d213AcC13AbC21d9Fee2Ed6Dd) |
| ~~PriceOracleProxy \(deprecated\)~~ | [0x9a5135157a74b753d11197a821e7f199f5b2fed0](https://etherscan.io/address/0x9a5135157a74b753d11197a821e7f199f5b2fed0) |

