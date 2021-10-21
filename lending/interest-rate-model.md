# Interest Rate Model

## APY Function

**Borrow APY**

\= \[1 + Base + Multiplier \* min(UtilizationRate, Kink 1) + max(JumpMultiplier \* UtilizationRate - Kink 2, 0)] ^ 31536000 - 1

**Supply APY**

\= Distribute (Interest Paid by Borrowers Per Block - Reserve) to all suppliers, and convert it into APY

\= Distribute \[(1 + Borrow APY) ^ (1 / BlocksPerYear) - 1] \* Total Borrow \* (1 - Reserve Factor) to all suppliers, and convert it into APY

\= {\[(1 + Borrow APY) ^ (1 / BlocksPerYear) - 1] \* Total Borrow \* (1 - Reserve Factor) / Total Supply}, and convert it into APY

\= {1 + \[(1 + Borrow APY) ^ (1/BlocksPerYear) - 1] \* Total Borrow \* (1 - Reserve Factor) / Total Supply} ^ BlocksPerYear - 1

\= **{1+\[(1+Borrow APY)^(1/BlocksPerYear)-1]\*(1-Reserve Factor)\*Utilization Rate}^BlocksPerYear-1**

{% hint style="info" %}
BlocksPerYear = 31,536,000 (1 sec per block)
{% endhint %}

{% hint style="info" %}
Find other variables in [Markets](https://app.cream.finance/markets/arbitrum)
{% endhint %}

## Major

![](<../.gitbook/assets/截圖 2021-10-13 16.04.10.png>)

| Parameter        | Value                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------- |
| Category         | Major                                                                                       |
| Tokens           | WAVAX, WETH.e, WBTC.e                                                                       |
| Base             | 0%                                                                                          |
| Multiplier       | 15%                                                                                         |
| JumpMultiplier   | 500%                                                                                        |
| Kink 1           | 80%                                                                                         |
| Kink 2           | 90%                                                                                         |
| Contract Address | [0x7ef18d0a9C3Fb1A716FF6c3ED0Edf52a2427F716](https://cchain.explorer.avax.network/address/) |

## Stable

![](<../.gitbook/assets/截圖 2021-10-13 16.04.58.png>)

| Parameter        | Value                                                                                                                                 |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Category         | Stable                                                                                                                                |
| Tokens           | USDT.e, USDC.e, DAI.e                                                                                                                 |
| Base             | 0%                                                                                                                                    |
| Multiplier       | 18%                                                                                                                                   |
| JumpMultiplier   | 800%                                                                                                                                  |
| Kink 1           | 80%                                                                                                                                   |
| Kink 2           | 90%                                                                                                                                   |
| Contract Address | [0x5Dc3A30d8c5937f1529C3c93507C16d86A17072A](https://cchain.explorer.avax.network/address/0x5Dc3A30d8c5937f1529C3c93507C16d86A17072A) |

## Governance

![](<../.gitbook/assets/截圖 2021-10-13 16.05.43.png>)

| Parameter        | Value                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------- |
| Category         | Governance & Seeds                                                                          |
| Tokens           | LINK.e                                                                                      |
| Base             | 0%                                                                                          |
| Multiplier       | 20%                                                                                         |
| JumpMultiplier   | 500%                                                                                        |
| Kink 1           | 70%                                                                                         |
| Kink 2           | 80%                                                                                         |
| Contract Address | [0x20d5d319C2964ecb52e1B006a4C059b7f6d6ad0a](https://cchain.explorer.avax.network/address/) |
