# Flash Loans

C.R.E.A.M. is bringing Flash Loans to our money markets.

Flash Loans allow developers access to undercollateralized loans, pending the borrowed amount \(and fee\) is returned within one transaction block.

Flash Loans offer a wide range of use cases, including democratized liquidations, arbitrage, collateral swapping and interest rate swapping.

Our Flash Loans feature are very similar to [AAVE Flash Loans V1](https://aave.com/flash-loans), except C.R.E.A.M. Flash Loans are implemented on crToken.

There are 3 major differences between C.R.E.A.M. Flash Loans and AAVE v1 Flash Loans:

1. Using C.R.E.A.M. Flash Loans devs interact with crToken, instead of the lending pool. To execute Flash Loans, users must know specific asset address of crToken
2. There is an addition argument initiator when the callback function executeOperation is invoked. The initiator is the msg.sender who calls the Flash Loans function.
3. Fee is cheaper. C.R.E.A.M. fee is 0.03%

{% hint style="info" %}
Only part of markets have Flash Loans
{% endhint %}

### Binance Smart Chain

WBNB, ETH, USDT, USDC, DAI, BTCB, BUSD, XRP, BCH, LTC, LINK, DOT, ADA, CREAM, BAND, EOS, XTZ, FIL, YFI, UNI, ATOM, ALPHA, TWT, CAKE, XVS, BAT, VAI, AUTO, renBTC, renZEC, BETH, IOTX, SXP, SUSHI

