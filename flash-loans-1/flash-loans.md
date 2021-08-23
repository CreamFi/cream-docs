# Flash Loans \(deprecated\)

## Overview

C.R.E.A.M. is bringing Flash Loans to our money markets.

Flash Loans allow developers access to undercollateralized loans, pending the borrowed amount \(and fee\) is returned within one transaction block.

Flash Loans offer a wide range of use cases, including democratized liquidations, arbitrage, collateral swapping and interest rate swapping.

Our Flash Loans feature is very similar to [AAVE Flash Loans V1](https://aave.com/flash-loans), except C.R.E.A.M. Flash Loans are implemented on crToken.

There are 3 major differences between C.R.E.A.M. Flash Loans and AAVE v1 Flash Loans:

1. Using C.R.E.A.M. Flash Loans devs **interact with crToken contract** \([Lending](https://docs.cream.finance/lending/lending-contract-address), [IronBank](https://docs.cream.finance/iron-bank/iron-bank)\)**,** instead of the lending pool. To execute Flash Loans, users must know the specific asset address of crToken.
2. There is an additional argument initiator when the callback function executeOperation is invoked. The initiator is the `msg.sender` who calls the Flash Loans function.
3. Fee is cheaper. C.R.E.A.M. fee is 0.03%

{% hint style="info" %}
Only part of markets have Flash Loans
{% endhint %}

### Lending

USDT, USDC, YFI, BAL, COMP, LINK, CRV, renBTC, BUSD, MTA, SUSHI, FTT, SRM, UNI, wNXM, CEL, DPI, BBTC, AAVE, BOND, KP3R, HBTC, HFIL, CRETH2, HUSD, DAI, HEGIC, ESD, COVER, 1INCH, TBTC, OMG, WBTC, SNX, sUSD, PICKLE, AKRO, OGN, AMP, FRAX, BAC, ALPHA, UST, FTM, RUNE, PERP, RAI, OCEAN, RARI

{% page-ref page="../lending/lending-contract-address.md" %}

### Iron Bank

WETH, DAI, USDT, USDC, sUSD, LINK, YFI, SNX, WBTC, mUSD, DUSD, EURS, sEUR, DPI, BUSD, GUSD

{% page-ref page="../iron-bank/iron-bank.md" %}

## Step by step guide

### 1. Deploy your Flash Loan contract

Your contract that receives the flash loaned funds must conform to [`IFlashloanReceiver`](https://github.com/CreamFi/compound-protocol/blob/master/contracts/CCapableErc20.sol#L5-L7) interface by implementing `executeOperation` function as the example below.

```javascript
pragma solidity ^0.5.16;

interface IERC20 {
    function balanceOf(address _owner) external view returns (uint256 balance);
    function transfer(address _to, uint256 _value) external returns (bool success);
}

interface IFlashloanReceiver {
    function executeOperation(address sender, address underlying, uint amount, uint fee, bytes calldata params) external;
}

interface ICTokenFlashloan {
    function flashLoan(address receiver, uint amount, bytes calldata params) external;
}

// FlashloanExample is a simple flashloan receiver sample code
contract FlashloanExample is IFlashloanReceiver {

    address public owner;
    constructor() public {
      owner = msg.sender;
    }

    function doFlashloan(address cToken, uint256 borrowAmount) external {
        require(msg.sender == owner, "not owner");

        // TODO: customize your params here
        bytes memory data = abi.encode(address(this), 1234);

        // call the flashLoan method
        ICTokenFlashloan(cToken).flashLoan(address(this), borrowAmount, data);
    }

    // this function is called after your contract has received the flash loaned amount
    function executeOperation(address sender, address underlying, uint amount, uint fee, bytes calldata params) external {
        address cToken = msg.sender;

        uint currentBalance = IERC20(underlying).balanceOf(address(this));
        require(currentBalance >= amount, "Invalid balance, was the flashLoan successful?");

        // TODO: decode your params if you have any
        (address receiver, uint amount) = abi.decode(params, (address, uint));
        
        // TODO:
        // Your logic goes here.
        // !! Ensure that *this contract* has enough of `underlying` funds to payback the `fee` !!
        //


        // transfer fund + fee back to cToken
        require(IERC20(underlying).transfer(cToken, amount + fee), "Transfer fund back failed");
    }
}
```

{% hint style="info" %}
Line 38-41 is where your Flash Loan logic goes.
{% endhint %}

### 2. Calling `flashloan()`

To call [`flashLoan(address receiver, uint amount, bytes calldata params)`](https://github.com/CreamFi/compound-protocol/blob/master/contracts/CCapableErc20.sol#L231) on supported crTokens\([Lending](https://docs.cream.finance/lending/lending-contract-address), [IronBank](https://docs.cream.finance/iron-bank/iron-bank)\), 3 parameters are required.

* `receiver` : The Flash Loan contract address you deployed.
* `amount`  : Keep in mind that the decimal of amount is dependent on crToken's underlying asset.
* `params` : encoded parameter for `executeOperation()`. 
  * If no parameters are needed in your Flash Loan contract, use an empty value `""`.
  * If you would like to pass parameters into your flash loan, you will need to encode it.

#### How to pass your parameters by encoding and decoding

#### Decoding

Before you pass your parameters, you will need to determine the type and layout of your params and decode them in `executeOperation` function by using the built-in `abi.decode()` function.

For example:

```javascript
(address target) = abi.decode(params, (address));
```

#### Encoding

Encoding can be done off-chain by using a package like [ethers.js](https://docs.ethers.io/v5/api/utils/abi/coder/#AbiCoder--methods).

```javascript
const data = ethers.utils.defaultAbiCoder.encode(
    ["string", "address"],
    ["hello world!", "0x0000000000000000000000000000000000000000"]
);
```

Or else, can be done with solidity.

```javascript
bytes memory data = abi.encode(address(this), 1234);
```

Like line 28 in function `doFlashloan(address cToken, uint256 borrowAmount)` of the above example.



### 3. Paying back flash loaned asset

You **must** transfer fund + fee back to crToken address in order to complete the flash loan process. Just like line 50 in the example code above.

```javascript
// transfer fund + fee back to cToken
require(IERC20(underlying).transfer(cToken, amount + fee), "Transfer fund back failed");
```

## Playground

To playaround with our flashloan with mainnet forking environment, please check out this repo: [CreamFi/**flashloan-playground**](https://github.com/CreamFi/flashloan-playground)\*\*\*\*

