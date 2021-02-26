# Interest Rate Model

## APY Funcion

Borrow APY

= Base + min\(Multiplier \* __UtilizationRate, Multiplier \* Kink\) + max\(JumpMultiplier \* UtilizationRate - Kink, 0\)



Supply APY

= annualized\[de–annualized\(Borrow APY\) - Reserve Factor\]

## Stable + Major

![](https://i.imgur.com/5aoSePr.png)

| Parameter | Value |
| :--- | :--- |
| Category | Stable & Major |
| Tokens | BNB, BUSD, BTCB, XRP, LTC, BCH, ETH, USDT, ADA, EOS, DAI, XTZ, USDC, renBTC |
| Base | 2% |
| Multiplier | 25% |
| JumpMultiplier | 500% |
| Kink | 80% |
| Contract Address | [0x4e4c96b038899e2f2597ef693b8278cfeb63e7db](https://bscscan.com/address/0x4e4c96b038899e2f2597ef693b8278cfeb63e7db) |

## Governance + Seed

![](https://i.imgur.com/Fg4vOj7.png)

| Parameter | Value |
| :--- | :--- |
| Category | Governance & Seeds |
| Tokens | LINK, CREAM, BAND, FIL, YFI, UNI, ATOM, ALPHA, TWT, CAKE, XVS, BAT, VAI, AUTO, renZEC |
| Base | 2% |
| Multiplier | 35% |
| JumpMultiplier | 750% |
| Kink | 80% |
| Contract Address | [0x66d801f9bf3F3225251318565352d49E348aEB6d](https://bscscan.com/address/0x66d801f9bf3F3225251318565352d49E348aEB6d) |

