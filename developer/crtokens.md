---
description: >-
  Shout out to our community member Ivan Flores for the hard work and
  contribution
---

# crTokens

## Introduction

Each asset supported by the C.R.E.A.M. Protocol is integrated through a crToken contract, which is an [EIP-20](https://eips.ethereum.org/EIPS/eip-20) compliant representation of balances supplied to the protocol. By minting crTokens, users \(1\) earn interest through the crToken's exchange rate, which increases in value relative to the underlying asset, and \(2\) gain the ability to use crTokens as collateral.

crTokens are the primary means of interacting with the C.R.E.A.M. Protocol; when a user mints, redeems, borrows, repays a borrow, liquidates a borrow, or transfers crTokens, she will do so using the crToken contract.

There are currently two types of crTokens: CErc20 and CEther. Though both types expose the EIP-20 interface, CErc20 wraps an underlying ERC-20 asset, while CEther simply wraps Ether itself. As such, the core functions which involve transferring an asset into the protocol have slightly different interfaces depending on the type, each of which is shown below.

## Mint

The mint function transfers an asset into the protocol, which begins accumulating interest based on the current Supply Rate for the asset. The user receives a quantity of crTokens equal to the underlying tokens supplied, divided by the current [Exchange Rate](https://docs.cream.finance/api/crtokens#exchange-rate).

### CErc20

```jsx
function mint(uint mintAmount) returns (uint)
```

`msg.sender:` The account which shall supply the asset, and own the minted cTokens.

`mintAmount`: The amount of the asset to be supplied, in units of the underlying asset.

`RETURN:` 0 on success, otherwise an Error code

Before supplying an asset, users must first approve the crToken to access their token balance.

### CEther

```jsx
function mint() payable
```

`msg.valuepayable:` The amount of ether to be supplied, in wei.

`msg.sender:` The account which shall supply the ether, and own the minted cTokens.

`RETURN:` No return, reverts on error.

### Solidity

```jsx
Erc20 underlying = Erc20(0xToken...);     // get a handle for the underlying asset contract
CErc20 crToken = CErc20(0x3FDA...);        // get a handle for the corresponding cToken contract
underlying.approve(address(cToken), 100); // approve the transfer
assert(crToken.mint(100) == 0);            // mint the cTokens and assert there is no error
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDB...);
await crToken.methods.mint().send({from: myAccount, value: 50});
```

## **Redeem**

The redeem function converts a specified quantity of crTokens into the underlying asset, and returns them to the user. The amount of underlying tokens received is equal to the quantity of crTokens redeemed, multiplied by the current [Exchange Rate](https://docs.cream.finance/api/crtokens#exchange-rate). The amount redeemed must be less than the user's Account Liquidity and the market's available liquidity.

### CErc20 / CEther

```jsx
function redeem(uint redeemTokens) returns (uint)
```

`msg.sender:` The account to which redeemed funds shall be transferred.

`redeemTokens:` The number of cTokens to be redeemed.

`RETURN:` 0 on success, otherwise an Error code

### **Solidity**

```jsx
CEther crToken = CEther(0x3FDB...);
require(crToken.redeem(7) == 0, "something went wrong");
```

### **Web3 1.0**

```jsx
const crToken = CErc20.at(0x3FDA...);
crToken.methods.redeem(1).send({from: ...});
```

## **Redeem Underlying**

The redeem underlying function converts crTokens into a specified quantity of the underlying asset, and returns them to the user. The amount of crTokens redeemed is equal to the quantity of underlying tokens received, divided by the current [Exchange Rate](https://docs.cream.finance/api/crtokens#exchange-rate). The amount redeemed must be less than the user's Account Liquidity and the market's available liquidity.

### CErc20 / CEther

```jsx
function redeemUnderlying(uint redeemAmount) returns (uint)
```

### Solidity

```jsx
CEther crToken = CEther(0x3FDB...);
require(crToken.redeemUnderlying(50) == 0, "something went wrong");
```

### Web3 1.0

```jsx
const crToken = CErc20.at(0x3FDA...);
crToken.methods.redeemUnderlying(10).send({from: ...});
```

## **Borrow**

The borrow function transfers an asset from the protocol to the user, and creates a borrow balance which begins accumulating interest based on the Borrow Rate for the asset. The amount borrowed must be less than the user's Account Liquidity and the market's available liquidity.

To borrow Ether, the borrower must be 'payable' \(solidity\).

### **CErc20 / CEther**

```jsx
function borrow(uint borrowAmount) returns (uint)
```

`msg.sender:` The account to which redeemed funds shall be transferred.

`borrowAmount:` The number of crTokens to be borrowed

`RETURN:` 0 on success, otherwise an Error code

### Solidity

```jsx
CEther crToken = CEther(0x3FDB...);
require(crToken.redeemUnderlying(50) == 0, "got collateral?");
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDA...);
await crToken.methods.borrow(50).send({from: 0xMyAccount});
```

## **Repay Borrow**

The repay function transfers an asset into the protocol, reducing the user's borrow balance.

### **CErc20**

```jsx
function repayBorrow(uint borrowAmount) returns (uint)
```

`msg.sender:` The account to which borrowed the asset, and shall repay the borrow.

`borrowAmount:` The amount of the underlying borrowed asset to be repaid. A value of -1 \(i.e. 2^256 - 1\) can be used to repay the full amount.

`RETURN:` 0 on success, otherwise an Error code

Before repaying an asset, users must first approve the crToken to access their token balance.

### CEther

```jsx
function repayBorrow() payable
```

`msg.value` payable: The amount of ether to be repaid, in wei.

`msg.sender:` The account which borrowed the asset, and shall repay the borrow

`RETURN:` 0 on success, otherwise an Error code

### Solidity

```jsx
CEther crToken = CEther(0x3FDB...);
require(crToken.repayBorrow.value(100() == 0, "transfer approved?");const crToken = CErc20.at(0x3FDA...);
crToken.methods.repayBorrow(10000).send({from: ...});
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDA...);
await crToken.methods.borrow(50).send({from: 0xMyAccount});
```

## **Repay Borrow Behalf**

The repay function transfers an asset into the protocol, reducing the target user's borrow balance.

### CErc20

```jsx
function repayBorrowBehalf(address borrower, uint repayAmount) returns (uint)
```

`msg.sender:` The account to which shall repay the borrow

`borrowAmount:` The account which borrowed the asset to be repaid.

`repayAmount`: The amount of the underlying borrowed asset to be repaid. A value of -1 \(i.e. 2^256 - 1\) can be used to repay the full amount.

`RETURN:` 0 on success, otherwise an Error code

Before repaying an asset, users must first approve the crToken to access their token balance.

### **CEther**

```jsx
function repayBorrowBehalf(address borrower) payable
```

`msg.valuepayable:` The amount of ether to be repaid, in wei.

`msg.sender:` The account which shall repay the borrow.

`borrower:` The account which borrowed the asset to be repaid.

`RETURN:` No return, reverts on error.

### **Solidity**

```jsx
CEther crToken = CEther(0x3FDB...);
require(crToken.repayBorrowBehalf.value(100)(0xBorrower) == 0, "transfer approved?");
```

### **Web3 1.0**

```jsx
const crToken = CErc20.at(0x3FDA...);
await crToken.methods.repayBorrowBehalf(0xBorrower, 10000).send({from: 0xPayer});
```

## **Liquidate Borrow**

A user who has negative account liquidity is subject to liquidation by other users of the protocol to return his/her account liquidity back to positive \(i.e. above the collateral requirement\). When a liquidation occurs, a liquidator may repay some or all of an outstanding borrow on behalf of a borrower and in return receive a discounted amount of collateral held by the borrower; this discount is defined as the liquidation incentive.

A liquidator may close up to a certain fixed percentage \(i.e. close factor\) of any individual outstanding borrow of the underwater account. When collateral is seized, the liquidator is transferred crTokens which they may redeem the same as if they had supplied the asset themselves. Users must approve each crToken contract before calling liquidate \(i.e. on the borrowed asset which they are repaying\), as they are transferring funds into the contract.

### **CErc20**

```jsx
function liquidateBorrow(address borrower, uint amount, address collateral) returns (uint)
```

`msg.sender:` The account which shall liquidate the borrower by repaying their debt and seizing their collateral.

`borrower:` The account with negative account liquidity that shall be liquidated.

`repayAmount:` The amount of the borrowed asset to be repaid and converted into collateral, specified in units of the underlying borrowed asset.

`cTokenCollateral:` The address of the crToken currently held as collateral by a borrower, that the liquidator shall seize.

`RETURN:` 0 on success, otherwise an Error code

Before supplying an asset, users must first approve the crToken to access their token balance.

### CEther

```jsx
function liquidateBorrow(address borrower, address crTokenCollateral) payable
```

`msg.valuepayable:` The amount of ether to be repaid and converted into collateral, in wei.

`msg.sender:` The account which shall liquidate the borrower by repaying their debt and seizing their collateral.

`borrower:` The account with negative [account liquidity](https://compound.finance/docs/comptroller#account-liquidity) that shall be liquidated.

`crTokenCollateral:` The address of the crToken currently held as collateral by a borrower, that the liquidator shall seize.

`RETURN:` No return, reverts on error.

### Solidity

```jsx
CEther crToken = CEther(0x3FDB...);
CErc20 crTokenCollateral = CErc20(0x3FDA...);
require(crToken.liquidateBorrow.value(100)(0xBorrower, crTokenCollateral) == 0, "borrower underwater??");
```

### **Web3 1.0**

```jsx
const crToken = CErc20.at(0x3FDA...);
const crTokenCollateral = CEther.at(0x3FDB...);
await crToken.methods.liquidateBorrow(0xBorrower, 33, crTokenCollateral).send({from: 0xLiquidator});
```

## **Exchange Rate**

Each crToken is convertible into an ever increasing quantity of the underlying asset, as interest accrues in the market. The exchange rate between a crToken and the underlying asset is equal to:

```jsx
exchangeRate = (getCash() + totalBorrows() - totalReserves()) / totalSupply()
```

### CErc20/CEther

```jsx
function exchangeRateCurrent() returns (uint)
```

### Solidity

```jsx
CErc20 crToken = CrToken(0x3FDA...);
uint exchangeRateMantissa = crToken.exchangeRateCurrent();
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDB...);
const exchangeRate = (await crToken.methods.exchangeRateCurrent().call()) / 1e18;
```

Tip: note the use of call vs. send to invoke the function from off-chain without incurring gas costs.

## Get Cash

Cash is the amount of underlying balance owned by this crToken contract. One may query the total amount of cash currently available to this market.

### CErc20/CEther

```jsx
function getCash() returns (unit)
```

`RETURN:` The quantity of underlying asset owned by the contract.

### Solidity

```jsx
CErc20 crToken = CrToken(0x3FDA...);
uint cash = crToken.getCash();
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDB...);
const cash = (await crToken.methods.getCash().call());
```

## Total Borrow

Total Borrows is the amount of underlying currently loaned out by the market, and the amount upon which interest is accumulated to suppliers of the market.

### CErc20/CEther

```jsx
function totalBorrowCurrent() returns (unit)
```

`RETURN:` The total amount of borrowed underlying, with interest.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint borrows = crToken.totalBorrowsCurrent();
```

### Web3 1.0

```jsx
crToken = CEther.at(0x3FDB...);
const borrows = (await crToken.methods.totalBorrowsCurrent().call());
```

## Borrow Balance

A user who borrows assets from the protocol is subject to accumulated interest based on the current borrow rate. Interest is accumulated every block and integrations may use this function to obtain the current value of a user's borrow balance with interest.

### CErc20/CEther

```jsx
function borrowBalanceCurrent(addressacount) returns (unit)
```

`RETURN:` The total amount of borrowed underlying, with interest.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint borrows = crToken.borrowBalanceCurrent(msg.caller);
```

### Web3 1.0

```jsx
crToken = CEther.at(0x3FDB...);
const borrows = await crToken.methods.totalBorrowsCurrent(account).call();
```

## Borrow Rate

At any point in time one may query the contract to get the current borrow rate per block.

### CErc20/CEther

```jsx
function borrowRatePerBlock() returns (unit)
```

`RETURN:` The total amount of borrowed underlying, with interest.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint borrowRateMantissa = crToken.borrowRatePerBlock();
```

### Web3 1.0

```jsx
crToken = CEther.at(0x3FDB...);
const borrowRate = (await crToken.methods.borrowRatePerBlock().call());
```

## Total Supply

Total Supply is the number of tokens currently in circulation in this crToken market. It is part of the EIP-20 interface of the crToken contract.

### CErc20/CEther

```jsx
function totalSupply() returns (unit)
```

`RETURN:` The total number of tokens in circulation for the market.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint tokens = crToken.totalSupply();
```

### Web3 1.0

```jsx
crToken = CEther.at(0x3FDB...);
const tokens = (await crToken.methods.totalSupply().call());
```

## Underlying Balance

The user's underlying balance, representing their assets in the protocol, is equal to the user's crToken balance multiplied by the Exchange Rate.

### CErc20/CEther

```jsx
function balanceOfUnderlying(address account) returns (unit)
```

`account:` The account to get the underlying balance of.

`RETURN:` The amount of underlying currently owned by the account.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint tokens = crToken.balanceOfUnderlying(msg.caller);
```

### Web3 1.0

```jsx
crToken = CEther.at(0x3FDB...);
const tokens = await crToken.methods.balanceOfUnderlying(account).call();
```

## Supply Rate

At any point in time one may query the contract to get the current supply rate per block. The supply rate is derived from the borrow rate, reserve factor and the amount of total borrows.

### CErc20/CEther

```jsx
function supplyRatePerBlock() returns (unit)
```

`RETURN:` The current supply rate as an unsigned integer, scaled by 1e18.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint supplyRateMantissa = crToken.supplyRatePerBlock();
```

### Web3 1.0

```jsx
const cToken = CEther.at(0x3FDB...);
const supplyRate = (await cToken.methods.supplyRatePerBlock().call()) / 1e18;
```

## Total Reserves

Reserves are an accounting entry in each crToken contract that represents a portion of historical interest set aside as cash which can be withdrawn or transferred through the protocol's governance. A small portion of borrower interest accrues into the protocol, determined by the reserve factor.

### CErc20/CEther

```jsx
function totalReserves() returns (unit)
```

`RETURN:` The total amount of reserves held in the market

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint reserves = crToken.totalReserves();
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDB...);
const reserves = (await crToken.methods.totalReserves().call());
```

## Reserve Factor

The reserve factor defines the portion of borrower interest that is converted into reserves.

### CErc20/CEther

```jsx
function reserveFactorMantissa() returns (unit)
```

`RETURN:` The current reserve factor as an unsigned itneger, scaled by 1e18.

### Solidity

```jsx
CErc20 crToken = CToken(0x3FDA...);
uint reserveFactorMantissa = crconst cToken = CEther.at(0x3FDB...);
const reserveFactor = (await cToken.methods.reserveFactorMantissa().call()) / 1e18;Token.reserveFactorMantissa();
```

### Web3 1.0

```jsx
const crToken = CEther.at(0x3FDB...);
const reserves = (await crToken.methods.totalReserves().call());
```

