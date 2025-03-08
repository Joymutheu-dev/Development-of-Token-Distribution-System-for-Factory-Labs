## Overview
This project presents a **Token Distribution System** for **Factory Labs**, enabling governance committees to **passively manage token allocations** via **modular smart contracts** integrated with Factory Labs' token infrastructure.

## Architecture
- **TokenDistributor.sol** – Manages token distribution, supports multi-asset transfers, enforces governance control.
- **GovernanceControl.sol** – Implements role-based access for governance committees, integrates multi-signature approvals.
- **FactoryLabsToken.sol** *(if needed)* – ERC-20 token for integration/testing.

## Technical Stack
- Solidity (0.8.x)
- Hardhat
- OpenZeppelin (ERC-20, AccessControl)
- EVM-compatible networks

## Setup

### Clone & Install
```bash
git clone https://github.com/yourusername/token-distribution-system.git
cd token-distribution-system
npm install

## Compile & Test

npx hardhat compile  
npx hardhat test

Deploy

Local (Hardhat Network)

npx hardhat node  
npx hardhat run scripts/deploy.js --network localhost

**Testnet (Goerli, Sepolia)**

1. Update .env with RPC URL & Private Key.


2. Run:

npx hardhat run scripts/deploy.js --network goerli



**Smart Contracts**

**TokenDistributor.sol**

distributeTokens(address recipient, uint256 amount) – Transfers tokens based on governance rules.

updateAllocation(address recipient, uint256 newAmount) – Allows governance to adjust distributions.

emergencyWithdraw(address token, uint256 amount) – Safeguard for fund retrieval.


**GovernanceControl.sol**

proposeAllocationUpdate(address recipient, uint256 newAmount) – Creates a governance proposal.

approveUpdate(uint256 proposalId) – Approves allocation changes via voting.

addGovernanceMember(address member) – Adds a new governance member.


**Security**

Access Control – Role-based permissions (onlyGovernance).

Reentrancy Protection – Uses ReentrancyGuard.

Gas Optimization – Batch transactions, low-level Solidity optimizations.

Upgradeability – Modular design, supports proxy patterns.


**Testing & Validation**

Unit Testing – npx hardhat test

Fuzz Testing – Identifies edge cases.

Security Audits – Planned before mainnet deployment.


