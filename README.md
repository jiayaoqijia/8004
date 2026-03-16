# 8004

The central hub for the [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004) ecosystem — the Ethereum standard for **Trustless Agents**, providing on-chain identity, reputation, and validation for autonomous AI agents.

## What is ERC-8004?

ERC-8004 establishes a trust and discovery layer for AI agents through three lightweight on-chain registries:

| Registry | Purpose | Standard |
|----------|---------|----------|
| **Identity** | Agent as ERC-721 NFT with `agentURI` metadata | ERC-721 + URIStorage |
| **Reputation** | On-chain feedback signals (signed values, tags, IPFS payloads) | Custom |
| **Validation** | Third-party validator attestations (TEE, staking, manual) | Custom |

Deployed on **45+ EVM chains** including Ethereum, Base, BSC, Arbitrum, Polygon, Optimism, and more. Also supports Solana.

## Ecosystem

| Component | Description |
|-----------|-------------|
| [ERC-8004 Contracts](https://github.com/erc-8004/erc-8004-contracts) | Solidity registries deployed across 45+ chains |
| [8004scan](https://www.8004scan.io) | Agent discovery platform with search, leaderboards, and analytics |
| [Agent0 SDK](https://github.com/agent0labs/agent0-ts) | TypeScript SDK for ERC-8004 protocol interactions |
| [Best Practices](https://best-practices.8004scan.io) | Official v2.0 specification and standards |
| [8004scan API](https://www.8004scan.io/developers/docs) | Public REST API for agent discovery and data |

## Skills

This project ships two [ClawHub](https://clawhub.ai)-standard skills for Claude Code:

### `8004` — Protocol Knowledge

ERC-8004 protocol reference covering all three registries, agent schema, 45+ supported chains with contract addresses, trust model, and integration patterns (MCP, A2A, OASF, x402). Read-only knowledge skill.

### `8004scan` — API Integration

Wraps the [8004scan Public API](https://www.8004scan.io/api/v1/public/docs/openapi.json) for agent discovery, semantic search, statistics, and feedback queries. Uses `curl` + `jq`.

### Installation

```bash
# Clone and use with Claude Code
git clone https://github.com/jiayaoqijia/8004.git
cd 8004
# Skills are auto-detected from .claude/skills/
```

## Key Addresses

| Registry | Testnet | Mainnet |
|----------|---------|---------|
| Identity | `0x8004A818BFB912233c491871b3d84c89A494BD9e` | `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` |
| Reputation | `0x8004B663056A597Dffe9eCcC1965A193B7388713` | Same |
| Validation | `0x8004Cb1BFb31DAf7788923b405b754f57acEB4272` | Same |

## 8004scan Public API

Base URL: `https://www.8004scan.io/api/v1/public`

```bash
# Search agents
curl -s "https://www.8004scan.io/api/v1/public/agents/search?q=code+review" | jq .

# Get agent details
curl -s "https://www.8004scan.io/api/v1/public/agents/8453/17" | jq .

# Platform stats
curl -s "https://www.8004scan.io/api/v1/public/stats" | jq .
```

Optional `X-API-Key` header for elevated rate limits. See [Developer Docs](https://www.8004scan.io/developers/docs) and [OpenAPI Spec](https://www.8004scan.io/api/v1/public/docs/openapi.json).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute.

## Security

See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## License

[AGPL-3.0](LICENSE)
