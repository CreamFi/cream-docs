# Interest Rate Model

## APY Function

**Borrow APY**

= \[1 + Base + Multiplier \* min\(UtilizationRate, Kink\) + max\(JumpMultiplier \* UtilizationRate - Kink, 0\)\] ^ 10512000 - 1



**Supply APY**

= Distribute \(Interest Paid by Borrowers Per Block - Reserve\) to all suppliers, and convert it into APY

= Distribute \[\(1 + Borrow APY\) ^ \(1 / BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) to all suppliers, and convert it into APY

= {\[\(1 + Borrow APY\) ^ \(1 / BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) / Total Supply}, and convert it into APY

= {1 + \[\(1 + Borrow APY\) ^ \(1/BlocksPerYear\) - 1\] \* Total Borrow \* \(1 - Reserve Factor\) / Total Supply} ^ BlocksPerYear - 1

= **{1+\[\(1+Borrow APY\)^\(1/BlocksPerYear\)-1\]\*\(1-Reserve Factor\)\*Utilization Rate}^BlocksPerYear-1**

{% hint style="info" %}
BlocksPerYear = 10,512,000 \(3 sec per block\)
{% endhint %}

{% hint style="info" %}
Find other variables in [Markets](https://app.cream.finance/markets)
{% endhint %}

## Stable + Major

![](https://i.imgur.com/5aoSePr.png)

| Parameter | Value |
| :--- | :--- |
| Category | Stable & Major |
| Tokens | BNB, BUSD, BTCB, XRP, LTC, BCH, ETH, USDT, ADA, EOS, DAI, XTZ, USDC, renBTC, BETH, WBNB |
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
| Tokens | LINK, CREAM, BAND, FIL, YFI, UNI, ATOM, ALPHA, TWT, CAKE, XVS, BAT, VAI, AUTO, renZEC, IOTX, SXP, SUSHI |
| Base | 2% |
| Multiplier | 35% |
| JumpMultiplier | 750% |
| Kink | 80% |
| Contract Address | [0x66d801f9bf3F3225251318565352d49E348aEB6d](https://bscscan.com/address/0x66d801f9bf3F3225251318565352d49E348aEB6d) |

## Cake Liquidity Provider token \(CakeLP\)

![](../.gitbook/assets/jie-tu-20210602-10.27.10.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Category</td>
      <td style="text-align:left">CakeLP</td>
    </tr>
    <tr>
      <td style="text-align:left">Tokens</td>
      <td style="text-align:left">
        <p>CAKE-LP-CAKE-BNB v2</p>
        <p>CAKE-LP-BNB-BUSD v2</p>
        <p>CAKE-LP-BTCB-BNB v2</p>
        <p>CAKE-LP-ETH-BNB v2</p>
        <p>CAKE-LP-USDT-BUSD v2</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Base</td>
      <td style="text-align:left">10%</td>
    </tr>
    <tr>
      <td style="text-align:left">Multiplier</td>
      <td style="text-align:left">55%</td>
    </tr>
    <tr>
      <td style="text-align:left">JumpMultiplier</td>
      <td style="text-align:left">180%</td>
    </tr>
    <tr>
      <td style="text-align:left">Kink</td>
      <td style="text-align:left">50%</td>
    </tr>
    <tr>
      <td style="text-align:left">Contract Address</td>
      <td style="text-align:left"><a href="https://bscscan.com/address/0x0A4F9Ab20A56DD4624266c610B5F960Bd72C5710">0x0A4F9Ab20A56DD4624266c610B5F960Bd72C5710</a>
      </td>
    </tr>
  </tbody>
</table>

