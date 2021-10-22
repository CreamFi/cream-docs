# Testnet

## Contract Deployment Script

[GitHub repo](https://github.com/CreamFi/cream-deployment)

### Installation

```
git clone https://github.com/CreamFi/cream-deployment
cd cream-deployment
yarn install
```

### Setup

```
cp .env.default .env
```

Fill in environment variables

### Deploy

```
npx hardhat run scripts/deployComptroller.js --network <NETWORK>
```

### App in Testnet

We support Göerli. Go to [testnet.cream.finance](https://testnet.cream.finance)
