# Price Oracle

{% hint style="info" %}
We have Chainlink as our main price oracle
{% endhint %}

### Chainlink

For the following tokens, we use price feed provided by Chainlink:

WETH / BTC / DAI / LINK / YFI / SNX / DPI / USDT / USDC

For the following BTC-pegged token, we use BTC price instead:

* WBTC

For the following EUR stablecoins, we use euro price instead:

* EURS
* sEUR

### Contract

For the following token, we fetch price from contracts directly:

* y3Crv

### C.R.E.A.M. Finance

For the other tokens, we use our own price oracle to get the price.

### Price Oracle Address

| Contract | Address |
| :--- | :--- |
| PriceOracleProxy | [0x6B96c414ce762578c3E7930da9114CffC88704Cb](https://etherscan.io/address/0x6b96c414ce762578c3e7930da9114cffc88704cb) |
| V1PriceOracle | [0x3aBce8F1DB258fBc64827b0926e14A0F90525CF7](https://etherscan.io/address/0x3abce8f1db258fbc64827b0926e14a0f90525cf7) |

