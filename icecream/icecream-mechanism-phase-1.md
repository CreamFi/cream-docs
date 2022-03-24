# iceCREAM Mechanism Phase 1

![](../.gitbook/assets/icecream\_-3-.png)

## Components

### Lending Protocol

The lending protocol includes the comptroller, cToken markets, and cTokenAdmin. Every market will generate reserves. CTokenAdmin is a new contract that controls the cToken market. In addition to normal access control in cToken, it allows a specific reserve manager to extract reserves.

Source: [https://github.com/CreamFi/compound-protocol](https://github.com/CreamFi/compound-protocol)

{% content-ref url="../lending/lending-contract-address.md" %}
[lending-contract-address.md](../lending/lending-contract-address.md)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### Reserve Manager

The reserve manager is the hub of reserves extraction. It snapshots all the cToken reserves and everyone could trigger the extraction (with a 1-day cooldown period). It should take a ratio (currently 50%) of reserves and send them to the burners.

Source: [https://github.com/CreamFi/reserve-manager](https://github.com/CreamFi/reserve-manager)

Reserve Manager: [0x0C5Bf19618A8FCDdb132d82BC6c5ea736A1beAED](https://etherscan.io/address/0x0C5Bf19618A8FCDdb132d82BC6c5ea736A1beAED)

### Burners

Burners are a group of token converters. They will burn tokens into USDC, and USDC burner will convert USDC into yvCurve-IB token. There is a special component called manual burner. It's used for tokens whose onchain liquidity (Ethereum) is not deep enough. The manual burner is an EOA that will send the tokens to a centralized exchange or another network to convert manually. In the end, all tokens will be converted to yvCurve-IB token and send to the fee distributor.

![](../.gitbook/assets/icecream\_-4-.png)

Source: [https://github.com/CreamFi/curve-dao-contracts](https://github.com/CreamFi/curve-dao-contracts)

### Fee Distributor & Voting Escrow

The fee distributor and the voting escrow are the final stops of iceCream phase 1. The fee distributor stores all the reserves in yvCurve-IB and it handles the fee distribution among all the iceCream stakers. The voting escrow (iceCream) is where users stake their CREAM tokens. Users could claim the rewards here.

Source: [https://github.com/CreamFi/curve-dao-contracts](https://github.com/CreamFi/curve-dao-contracts)

Fee Distributor: [0x0Ca0f068edad122f09a39f99E7E89E705d6f6Ace](https://etherscan.io/address/0x0Ca0f068edad122f09a39f99E7E89E705d6f6Ace)

Voting Escrow: [0x3986425b96F11972d31C78ff340908832C5c0043](https://etherscan.io/address/0x3986425b96F11972d31C78ff340908832C5c0043)
