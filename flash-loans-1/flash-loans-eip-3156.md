---
description: conforming to EIP-3156
---

# Flash Loans

## Overview

C.R.E.A.M. is bringing Flash Loans to our money markets.

Flash Loans allow developers access to undercollateralized loans, provided that the borrowed amount \(and fee\) is returned within one transaction block.

Flash Loans offer a wide range of use cases, including democratized liquidations, arbitrage, collateral swapping and interest rate swapping.

Our Flash Loans feature is very similar to [AAVE Flash Loans V1](https://aave.com/flash-loans), except C.R.E.A.M. Flash Loans are implemented on crToken.

There are 3 major differences between C.R.E.A.M. Flash Loans and AAVE v1 Flash Loans:

1. Using C.R.E.A.M. Flash Loans devs **interact with flashLoanLender contract ,** instead of the lending pool.
2. C.R.E.A.M has deployed two flashLoanLenders that conform to EIP-3156; one for Lending and one for IronBank.
3. Fee is cheaper. C.R.E.A.M. fee is 0.03%

Only tokens listed below are flash-loanable:

LON IBBTC PAXG PAX EURT BNT WOO FEI SWAP GNO COVER VVSP VSP MLN ARNXM ARMOR SFI RARI OCEAN PERP RAI RUNE FTM UST ALPHA FRAX AMP OGN AKRO PICKLE SUSD SNX WBTC OMG 1INCH ESD HEGIC DAI HUSD CRETH2 HFIL HBTC KP3R AAVE BOND BBTC DPI CEL WNXM SRM UNI FTT SUSHI MTA BUSD RENBTC CRV LINK COMP BAL YFI USDC USDT

## flashloanLender

* Ethereum v1: [0xa8682Cfd2B6c714d2190fA38863d545c7a0b73D5](https://etherscan.io/address/0xa8682Cfd2B6c714d2190fA38863d545c7a0b73D5)
* Iron Bank: [0x1a21Ab52d1Ca1312232a72f4cf4389361A479829](https://etherscan.io/address/0x1a21Ab52d1Ca1312232a72f4cf4389361A479829)

## Step by step guide

### 1. Deploy your Flash Loan contract

Your contract that receives the flash loaned funds must conform to [IERC3156Flash](https://eips.ethereum.org/EIPS/eip-3156)BorrowerInterface interface as specified in the standard

```text
pragma solidity ^0.5.16;

import "./ERC3156FlashLenderInterface.sol";
import "./ERC3156FlashBorrowerInterface.sol";

// FlashloanReceiver is a simple flashloan receiver implementation for testing
contract FlashloanBorrower is ERC3156FlashBorrowerInterface {
    function doFlashloan(
        address flashloanLender,
        address borrowToken,
        uint256 borrowAmount
    ) external {
        bytes memory data = abi.encode(cToken, borrowAmount);
        ERC3156FlashLenderInterface(flashloanLender).flashLoan(this, borrowToken, borrowAmount, data);
    }

    function onFlashLoan(
        address initiator,
        address token,
        uint256 amount,
        uint256 fee,
        bytes calldata data
    ) external returns (bytes32) {
        require(initiator == address(this), "FlashBorrower: Untrusted loan initiator");
        ERC20(borrowToken).approve(msg.sender, amount.add(fee));
        (address cToken, uint256 borrowAmount) = abi.decode(data, (address, uint256));
        // your logic is written here...
        return keccak256("ERC3156FlashBorrowerInterface.onFlashLoan");
    }
}
```

### 2. Calling `flashLoan()`

To call [flashLoan\(ERC3156FlashBorrowerInterface receiver, address token, uint256 amount, bytes calldata data\)](https://github.com/CreamFi/compound-protocol/blob/master/contracts/CCollateralCapErc20.sol#L185) on flashLoanLender \([Lending](https://docs.cream.finance/lending/lending-contract-address), [IronBank](https://docs.cream.finance/iron-bank/iron-bank)\), 4 parameters are required.

* `receiver` : The Flash Loan contract address you deployed.
* `token` : The token you'd like to borrow
* `amount` : Keep in mind that the decimal of amount is dependent on borrowToken's contract implementation.
* `data` : encoded parameter for `onFlashloan()`.

  * If no parameters are needed in your Flash Loan contract, use an empty value `""`.

  If you would like to pass parameters into your flash loan, you will need to encode it.

### How to pass your parameters by encoding and decoding

#### Decoding

Before you pass your parameters, you will need to determine the type and layout of your params and decode them in `executeOperation` function by using the built-in `abi.decode()` function.

For example:

```text
(address target) = abi.decode(params, (address));

```

#### Encoding

Encoding can be done off-chain by using a package like [ethers.js](https://docs.ethers.io/v5/api/utils/abi/coder/#AbiCoder--methods).

```text
const data = ethers.utils.defaultAbiCoder.encode(
    ["string", "address"],
    ["hello world!", "0x0000000000000000000000000000000000000000"]
);

```

Or else, can be done with solidity.

```text
bytes memory data = abi.encode(address(this), 1234);

```

Like in function`doFlashloan(address flashloanLender, address borrowToken, uint256 borrowAmount)`   
of the above example.

## Playground

To play around with our Flash Loans with mainnet forking environment, please check out this repo: ****[CreamFi/flashloan-playground](https://github.com/CreamFi/flashloan-playground)

