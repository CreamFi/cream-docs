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
      <td style="text-align:left">Stable &amp; Major</td>
    </tr>
    <tr>
      <td style="text-align:left">Tokens</td>
      <td style="text-align:left">
        <p>BNB, BUSD, BTCB, XRP, LTC, BCH, ETH, USDT, ADA, EOS, DAI, XTZ, USDC, renBTC,
          BETH, WBNB</p>
        <p></p>
        <p>CAKE-LP-CAKE-BNB v2</p>
        <p>CAKE-LP-BNB-BUSD v2</p>
        <p>CAKE-LP-BTCB-BNB v2</p>
        <p>CAKE-LP-ETH-BNB v2</p>
        <p>CAKE-LP-USDT-BUSD v2</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Base</td>
      <td style="text-align:left">2%</td>
    </tr>
    <tr>
      <td style="text-align:left">Multiplier</td>
      <td style="text-align:left">25%</td>
    </tr>
    <tr>
      <td style="text-align:left">JumpMultiplier</td>
      <td style="text-align:left">500%</td>
    </tr>
    <tr>
      <td style="text-align:left">Kink</td>
      <td style="text-align:left">80%</td>
    </tr>
    <tr>
      <td style="text-align:left">Contract Address</td>
      <td style="text-align:left"><a href="https://bscscan.com/address/0x4e4c96b038899e2f2597ef693b8278cfeb63e7db">0x4e4c96b038899e2f2597ef693b8278cfeb63e7db</a>
      </td>
    </tr>
  </tbody>
</table>

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

