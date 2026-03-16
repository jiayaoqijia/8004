# Supported Chains

ERC-8004 contracts are deployed on 30+ EVM chains using deterministic vanity addresses via CREATE2.

## Full SDK Support (5 chains)

These chains have full subgraph indexing and SDK support:

| Chain | Chain ID | RPC (public) | Explorer |
|-------|----------|-------------|----------|
| Ethereum Mainnet | 1 | `https://eth.llamarpc.com` | etherscan.io |
| Ethereum Sepolia | 11155111 | `https://rpc.sepolia.org` | sepolia.etherscan.io |
| Polygon Mainnet | 137 | `https://polygon-rpc.com` | polygonscan.com |
| Base Mainnet | 8453 | `https://mainnet.base.org` | basescan.org |
| Base Sepolia | 84532 | `https://sepolia.base.org` | sepolia.basescan.org |

## Contract Addresses

### Identity Registry

| Network Type | Address |
|-------------|---------|
| Testnets | `0x8004A818BFB912233c491871b3d84c89A494BD9e` |
| Mainnets | `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` |

### Reputation Registry

| All networks | `0x8004B663056A597Dffe9eCcC1965A193B7388713` |

### Validation Registry

| All networks | `0x8004Cb1BFb31DAf7788923b405b754f57acEB4272` |

## Additional Deployed Chains

Contracts are deployed but require manual `SUBGRAPH_URL` configuration for SDK use:

| Chain | Chain ID | Chain | Chain ID |
|-------|----------|-------|----------|
| Arbitrum One | 42161 | Arbitrum Sepolia | 421614 |
| Optimism | 10 | Optimism Sepolia | 11155420 |
| Avalanche C-Chain | 43114 | Avalanche Fuji | 43113 |
| BNB Smart Chain | 56 | BNB Testnet | 97 |
| Celo | 42220 | Celo Alfajores | 44787 |
| Gnosis | 100 | Gnosis Chiado | 10200 |
| Linea | 59144 | Linea Sepolia | 59141 |
| Mantle | 5000 | Mantle Sepolia | 5003 |
| Scroll | 534352 | Scroll Sepolia | 534351 |
| zkSync Era | 324 | zkSync Sepolia | 300 |
| Polygon zkEVM | 1101 | Polygon Amoy | 80002 |
| Moonbeam | 1284 | Moonbase Alpha | 1287 |
| Fantom | 250 | Fantom Testnet | 4002 |

## Chain Resolution Rules

When resolving which chain to use:

1. **Agent ID prefix**: `11155111:42` → chain 11155111 (Sepolia)
2. **Config file**: `~/.8004skill/config.json` → `activeChain` field
3. **Ask the user**: Never default silently — wrong chain = wrong registry

**Disambiguation**: "Sepolia" alone is ambiguous — could be Ethereum Sepolia (11155111) or Base Sepolia (84532). Always ask.

## RPC Configuration

For chains without default RPC, users can provide custom endpoints:

```
--rpc-url https://custom-rpc.example.com
```

Or set via environment:
```
SUBGRAPH_URL=https://custom-subgraph.example.com/subgraphs/name/erc8004
```
