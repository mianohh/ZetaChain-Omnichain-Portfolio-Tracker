# ZetaChain Omnichain Portfolio Tracker

A cross-chain DeFi portfolio tracker with Universal NFT gamification, built on ZetaChain with 100% revert resilience.

## 🎯 Hackathon Features

- **Universal NFT**: Mint Safety Badge once on ZetaChain, transfer to any chain
- **Revert Resilience**: 100% automatic refunds on failed cross-chain transactions
- **Volatility Premium**: 30% gas buffer for safe cross-chain operations
- **Gamification**: Unlock NFT badges by using safety features
- **Multi-Chain**: Deploy and test on ZetaChain, Ethereum, BSC, Polygon

## 🚀 Quick Start

### Prerequisites
- Node.js v16+
- MetaMask wallet
- ZETA tokens ([Get from faucet](https://labs.zetachain.com/get-zeta))

### Installation

```bash
# Install dependencies
npm install

# Create environment file
cp .env.example .env
# Add your PRIVATE_KEY to .env

# Deploy to ZetaChain Athens Testnet
npm run deploy:zeta

# Update contract address in app.js (line 11)
# this.CONTRACT_ADDRESS = "0xYOUR_DEPLOYED_ADDRESS";

# Start local server
npm start
# Open http://localhost:8000
```

## 📖 Usage

### 1. Create Position
- Connect MetaMask wallet
- Enter ZETA amount (e.g., 0.1)
- Click "Create Position"
- Confirm transaction

### 2. Cross-Chain Withdrawal
- Select a position
- Choose destination chain
- Enter recipient address
- Click "Withdraw" (includes 30% volatility premium)

### 3. Unlock & Mint NFT Badge
- After withdrawal, badge becomes eligible
- Click "Mint Safety Badge"
- NFT minted on ZetaChain

### 4. Transfer Badge Cross-Chain
- Select destination chain
- Enter recipient address
- Click "Transfer Badge"
- Universal NFT transfers to any chain

### 5. Emergency Functions
- View position statistics
- Emergency withdraw if needed
- Check total deposited

## 🛠️ Development

### Deploy to Different Networks

```bash
npm run deploy:zeta      # ZetaChain Athens
npm run deploy:sepolia   # Ethereum Sepolia
npm run deploy:bsc       # BSC Testnet
npm run deploy:mumbai    # Polygon Mumbai
```

### Test Functions

```bash
npm run test:zeta        # Test on ZetaChain
npm run check            # Diagnostic check
npm run test             # Full test suite
```

### Project Structure

```
├── contracts/
│   └── OmnichainTracker.sol    # Main smart contract
├── deployments/                 # Deployment artifacts
├── index.html                   # Frontend UI
├── app.js                       # Frontend logic
├── styles.css                   # Ethereum-inspired theme
├── hardhat.config.js            # Network configuration
├── deploy-testnet.js            # Universal deployment script
├── test-testnet-functions.js    # Automated testing
└── check-setup.js               # Diagnostic tool
```

## 🔧 Smart Contract Functions

### Core Functions
- `deposit()` - Create position with ZETA
- `withdrawAndTrack(positionId, destinationChainId, recipient)` - Cross-chain withdrawal
- `getPosition(positionId)` - View position details
- `getUserPositions(user)` - Get all user positions
- `getPositionCount()` - Total positions created
- `emergencyWithdraw(positionId)` - Emergency withdrawal

### NFT Functions
- `mintSafetyBadge()` - Mint Universal NFT badge
- `transferBadgeCrossChain(destinationChainId, recipient)` - Transfer NFT cross-chain
- `isEligibleForBadge(user)` - Check badge eligibility
- `getUserBadge(user)` - Get user's badge token ID
- `hasUsedSafetyBuffer(user)` - Check if user used volatility premium
- `ownerOf(tokenId)` - Get NFT owner
- `tokenURI(tokenId)` - Get NFT metadata

### View Functions
- `estimateWithdrawGas(destinationChainId)` - Estimate gas costs
- `totalDeposited()` - Total ZETA deposited in contract

## 🌐 Network Configuration

### ZetaChain Athens Testnet
- **Chain ID**: 7001
- **RPC**: https://zetachain-athens-evm.blockpi.network/v1/rpc/public
- **Explorer**: https://athens3.explorer.zetachain.com/
- **Faucet**: https://labs.zetachain.com/get-zeta

### Ethereum Sepolia
- **Chain ID**: 11155111
- **RPC**: https://rpc.sepolia.org

### BSC Testnet
- **Chain ID**: 97
- **RPC**: https://data-seed-prebsc-1-s1.binance.org:8545

### Polygon Mumbai
- **Chain ID**: 80001
- **RPC**: https://rpc-mumbai.maticvigil.com

## 🐛 Troubleshooting

### "Internal JSON-RPC error"
- **Cause**: Insufficient ZETA balance or wrong network
- **Fix**: Get ZETA from faucet, verify MetaMask is on ZetaChain Athens (Chain ID 7001)

### Contract not found
- **Cause**: Wrong contract address in app.js
- **Fix**: Update `CONTRACT_ADDRESS` in app.js line 11 with deployed address

### Transaction fails
- **Cause**: Gas estimation failure
- **Fix**: Try smaller amount (0.001 ZETA), check console (F12) for errors

### Run Diagnostics
```bash
npm run check
```

## 🏗️ Architecture

### Smart Contract
- Built with Solidity 0.8.26
- Implements ZetaChain's UniversalContract interface
- ERC721 for Universal NFT functionality
- onRevert callback for automatic refunds

### Frontend
- Vanilla JavaScript with ethers.js v6
- Ethereum-inspired dark theme with glassmorphism
- Real-time transaction monitoring
- Comprehensive error handling

### Safety Features
- ✅ 30% volatility premium on gas estimates
- ✅ Automatic refunds on failed transactions
- ✅ Position status tracking
- ✅ Emergency withdrawal function
- ✅ Event-driven monitoring

## 🎨 UI Features

- **Dark Theme**: Ethereum-inspired void black (#0a0b0d)
- **Glassmorphism**: Frosted glass effect on cards
- **Gradients**: Purple-blue eth-gradient (#6366f1 to #a855f7)
- **Animations**: Pulse for eligible badges, glow for unlocked
- **Responsive**: Mobile-friendly design
- **Real-time**: Live transaction status updates

## 📝 Testing Checklist

- [ ] Get ZETA tokens from faucet
- [ ] Deploy contract to testnet
- [ ] Update app.js with contract address
- [ ] Connect wallet to app
- [ ] Create position (deposit ZETA)
- [ ] Withdraw with volatility premium
- [ ] Check badge eligibility
- [ ] Mint Safety Badge NFT
- [ ] Transfer badge cross-chain
- [ ] Verify transactions on explorer
- [ ] Test emergency withdraw
- [ ] Check position statistics

## 🏆 Hackathon Bounties

### Bounty #2: Universal AI App
- **Requirement**: Universal NFT (mint once, launch everywhere)
- **Implementation**: Safety Badge NFT with cross-chain transfer
- **Demo**: Mint on ZetaChain → Transfer to any supported chain

### Bounty #3: Multi-Sponsor App
- **Requirement**: Amazon Q attribution
- **Implementation**: Footer attribution in UI
- **Location**: Bottom of index.html

## 📦 Dependencies

```json
{
  "dependencies": {
    "@zetachain/protocol-contracts": "^11.0.0-rc1",
    "@openzeppelin/contracts": "^5.0.0",
    "dotenv": "^16.0.0"
  },
  "devDependencies": {
    "@nomicfoundation/hardhat-toolbox": "^5.0.0",
    "hardhat": "^2.22.0"
  }
}
```

## 🔗 Important Links

- **ZetaChain Docs**: https://www.zetachain.com/docs/
- **Faucet**: https://labs.zetachain.com/get-zeta
- **Explorer**: https://athens3.explorer.zetachain.com/
- **Universal Apps**: https://www.zetachain.com/docs/developers/omnichain/universal-apps/

## 📄 License

MIT

## 🙏 Acknowledgments

Built with Amazon Q Developer for the ZetaChain Hackathon.

---

**Ready to test?** Run `npm run deploy:zeta` and start tracking your omnichain portfolio! 🚀
