# Comptroller

## Error Codes

| Code | Name | Description |
| :--- | :--- | :--- |
| 0 | NO\_ERROR | Not a failure. |
| 1 | UNAUTHORIZED | The sender is not authorized to perform this action. |
| 2 | COMPTROLLER\_MISMATCH | Liquidation cannot be performed in markets with different comptrollers. |
| 3 | INSUFFICIENT\_SHORTFALL | The account does not have sufficient shortfall to perform this action. |
| 4 | INSUFFICIENT\_LIQUIDITY | The account does not have sufficient liquidity to perform this action. |
| 5 | INVALID\_CLOSE\_FACTOR | The close factor is not valid. |
| 6 | INVALID\_COLLATERAL\_FACTOR | The collateral factor is not valid. |
| 7 | INVALID\_LIQUIDATION\_INCENTIVE | The liquidation incentive is invalid. |
| 8 | MARKET\_NOT\_ENTERED | The market has not been entered by the account. |
| 9 | MARKET\_NOT\_LISTED | The market is not currently listed by the comptroller. |
| 10 | MARKET\_ALREADY\_LISTED | An admin tried to list the same market more than once. |
| 11 | MATH\_ERROR | A math calculation error occurred. |
| 12 | NONZERO\_BORROW\_BALANCE | The action cannot be performed since the account carries a borrow balance. |
| 13 | PRICE\_ERROR | The comptroller could not obtain a required price of an asset. |
| 14 | REJECTION | The comptroller rejects the action requested by the market. |
| 15 | SNAPSHOT\_ERROR | The comptroller could not get the account borrows and exchange rate from the market. |
| 16 | TOO\_MANY\_ASSETS | Attempted to enter more markets than are currently supported. |
| 17 | TOO\_MUCH\_REPAY | Attempted to repay more than is allowed by the protocol. |

## Failure Info

| Code | Name |
| :--- | :--- |
| 0 | ACCEPT\_ADMIN\_PENDING\_ADMIN\_CHECK |
| 1 | ACCEPT\_PENDING\_IMPLEMENTATION\_ADDRESS\_CHECK |
| 2 | EXIT\_MARKET\_BALANCE\_OWED |
| 3 | EXIT\_MARKET\_REJECTION |
| 4 | SET\_CLOSE\_FACTOR\_OWNER\_CHECK |
| 5 | SET\_CLOSE\_FACTOR\_VALIDATION |
| 6 | SET\_COLLATERAL\_FACTOR\_OWNER\_CHECK |
| 7 | SET\_COLLATERAL\_FACTOR\_NO\_EXISTS |
| 8 | SET\_COLLATERAL\_FACTOR\_VALIDATION |
| 9 | SET\_COLLATERAL\_FACTOR\_WITHOUT\_PRICE |
| 10 | SET\_IMPLEMENTATION\_OWNER\_CHECK |
| 11 | SET\_LIQUIDATION\_INCENTIVE\_OWNER\_CHECK |
| 12 | SET\_LIQUIDATION\_INCENTIVE\_VALIDATION |
| 13 | SET\_MAX\_ASSETS\_OWNER\_CHECK |
| 14 | SET\_PENDING\_ADMIN\_OWNER\_CHECK |
| 15 | SET\_PENDING\_IMPLEMENTATION\_OWNER\_CHECK |
| 16 | SET\_PRICE\_ORACLE\_OWNER\_CHECK |
| 17 | SUPPORT\_MARKET\_EXISTS |
| 18 | SUPPORT\_MARKET\_OWNER\_CHECK |

