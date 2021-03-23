# Interest Rate Model

### APY Function

Borrow APY

= Base + min\(Multiplier \* __UtilizationRate, Multiplier \* Kink1\) + max\(JumpMultiplier \* UtilizationRate - Kink2, 0\)



Supply APY

= annualized\[de–annualized\(Borrow APY\) - Reserve Factor\]

### Major

![](../.gitbook/assets/jie-tu-20210323-19.08.43.png)

| Parameter | Value |
| :--- | :--- |
| Tokens | WETH, WBTC |
| Base | 0% |
| Multiplier | 17.5% |
| JumpMultiplier | 200% |
| Kink 1 | 80% |
| Kink 2 | 90% |
| Contract Address | [0x61e9a6aB4923F5046C0Fb80E5c9F98afc9995fad](https://etherscan.io/address/0x61e9a6ab4923f5046c0fb80e5c9f98afc9995fad#code) |

### Stable

![](../.gitbook/assets/jie-tu-20210323-19.09.28.png)

| Parameter | Value |
| :--- | :--- |
| Tokens | y3Crv, DAI, USDT, USDC, sUSD, mUSD, DUSD, EURS, sEUR, BUSD, GUSD, cDAI, cUSDT, cUSDC |
| Base | 0% |
| Multiplier | 23% |
| JumpMultiplier | 800% |
| Kink 1 | 80% |
| Kink 2 | 90% |
| Contract Address | [0xd6C04cF463A52A9C929D434F9F84ee70c1c0Ac6F](https://etherscan.io/address/0xd6C04cF463A52A9C929D434F9F84ee70c1c0Ac6F#code) |

### Governance

![](../.gitbook/assets/jie-tu-20210323-19.11.44.png)

| Parameter | Value |
| :--- | :--- |
| Tokens | LINK, YFI, SNX, DPI |
| Base | 0% |
| Multiplier | 10% |
| JumpMultiplier | 450% |
| Kink | 45% |
| Contract Address | [0xaaeDaFC0a2550c8D25A881904b85d91931bA6992](https://etherscan.io/address/0xaaedafc0a2550c8d25a881904b85d91931ba6992) |

