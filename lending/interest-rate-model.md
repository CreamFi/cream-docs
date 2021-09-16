# Interest Rate Model

## APY Function

**Borrow APY**

= \[1 + Base + Multiplier \* min\(UtilizationRate, Kink\) + max\(JumpMultiplier \* UtilizationRate - Kink, 0\)\] ^ 2102400 - 1



**Supply APY**

= Distribute \(Interest Paid by Borrowers Per Block - Reserve\) to all suppliers, and convert it into APY

= Distribute \[\(1 + Borrow APY\) ^ \(1 / BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) to all suppliers, and convert it into APY

= {\[\(1 + Borrow APY\) ^ \(1 / BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) / Total Supply}, and convert it into APY

= {1 + \[\(1 + Borrow APY\) ^ \(1/BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) / Total Supply} ^ BlocksPerYear - 1

= **{1+\[\(1+Borrow APY\)^\(1/BlocksPerYear\)-1\]\*\(1-Reserve Factor\)\*Utilization Rate}^BlocksPerYear-1**

{% hint style="info" %}
BlocksPerYear = 2,102,400 \(15 sec per block\)
{% endhint %}

{% hint style="info" %}
Find other variables in [Markets](https://app.cream.finance/markets/arbitrum)
{% endhint %}

## Major

![](../.gitbook/assets/jie-tu-20210719-xia-wu-8.20.00.png)

| Parameter | Value |
| :--- | :--- |
| Category | Major |
| Tokens | ETH |
| Base | 0% |
| Multiplier | 15% |
| JumpMultiplier | 200% |
| Kink 1 | 80% |
| Kink 2 | 90% |
| Contract Address | [0x3FaE5e5722C51cdb5B0afD8c7082e8a6AF336Ee8](https://arbiscan.io/address/0x3FaE5e5722C51cdb5B0afD8c7082e8a6AF336Ee8) |

## Stable

![](../.gitbook/assets/jie-tu-20210719-xia-wu-8.21.58.png)

| Parameter | Value |
| :--- | :--- |
| Category | Stable |
| Tokens | USDC, USDT |
| Base | 0% |
| Multiplier | 18% |
| JumpMultiplier | 800% |
| Kink 1 | 80% |
| Kink 2 | 90% |
| Contract Address | [0x7ef18d0a9C3Fb1A716FF6c3ED0Edf52a2427F716](https://arbiscan.io/address/0x7ef18d0a9C3Fb1A716FF6c3ED0Edf52a2427F716) |

## Governance + Seed

![](../.gitbook/assets/jie-tu-20210723-xia-wu-4.35.51.png)

| Parameter | Value |
| :--- | :--- |
| Category | Governance & Seeds |
| Tokens |  |
| Base | 0% |
| Multiplier | 20% |
| JumpMultiplier | 500% |
| Kink 1 | 70% |
| Kink 2 | 80% |
| Contract Address | [0x5Dc3A30d8c5937f1529C3c93507C16d86A17072A](https://arbiscan.io/address/0x5Dc3A30d8c5937f1529C3c93507C16d86A17072A) |

