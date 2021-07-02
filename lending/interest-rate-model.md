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
      <td style="text-align:left">BNB, BUSD, BTCB, XRP, LTC, BCH, ETH, USDT, ADA, EOS, DAI, XTZ, USDC, renBTC,
        BETH, WBNB</td>
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
      <td style="text-align:left">
        <p><a href="https://bscscan.com/address/0x4e4c96b038899e2f2597ef693b8278cfeb63e7db">0x4e4c96b038899e2f2597ef693b8278cfeb63e7db</a>
        </p>
        <p><a href="https://www.bscscan.com/address/0x681AB0F8a860fE234025b0205Eb69889aff32b75">0x681AB0F8a860fE234025b0205Eb69889aff32b75</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Governance + Seed

![](https://i.imgur.com/Fg4vOj7.png)

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
      <td style="text-align:left">Governance &amp; Seeds</td>
    </tr>
    <tr>
      <td style="text-align:left">Tokens</td>
      <td style="text-align:left">LINK, CREAM, BAND, FIL, YFI, UNI, ATOM, ALPHA, TWT, CAKE, XVS, BAT, VAI,
        AUTO, renZEC, IOTX, SXP, SUSHI</td>
    </tr>
    <tr>
      <td style="text-align:left">Base</td>
      <td style="text-align:left">2%</td>
    </tr>
    <tr>
      <td style="text-align:left">Multiplier</td>
      <td style="text-align:left">35%</td>
    </tr>
    <tr>
      <td style="text-align:left">JumpMultiplier</td>
      <td style="text-align:left">750%</td>
    </tr>
    <tr>
      <td style="text-align:left">Kink</td>
      <td style="text-align:left">80%</td>
    </tr>
    <tr>
      <td style="text-align:left">Contract Address</td>
      <td style="text-align:left">
        <p><a href="https://bscscan.com/address/0x66d801f9bf3F3225251318565352d49E348aEB6d">0x66d801f9bf3F3225251318565352d49E348aEB6d</a>
        </p>
        <p><a href="https://www.bscscan.com/address/0x410EcEc0229bEb4b66C98b217065767277a5d0B0">0x410EcEc0229bEb4b66C98b217065767277a5d0B0</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>

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

