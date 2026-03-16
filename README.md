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
| [Agent0 TypeScript SDK](https://github.com/agent0labs/agent0-ts) | TypeScript SDK for ERC-8004 protocol interactions |
| [Agent0 Python SDK](https://github.com/agent0labs/agent0-py) | Python SDK for ERC-8004 protocol interactions |
| [Best Practices](https://best-practices.8004scan.io) | Official v2.0 specification and standards |
| [8004scan API](https://www.8004scan.io/developers/docs) | Public REST API for agent discovery and data |

## Skills

This project ships three [ClawHub](https://clawhub.ai)-standard skills for Claude Code:

### `8004` — Protocol Knowledge

ERC-8004 protocol reference covering all three registries, agent schema, 45+ supported chains with contract addresses, trust model, and integration patterns (MCP, A2A, OASF, x402). Includes SDK usage examples for both TypeScript and Python. Read-only knowledge skill.

**References**: protocol overview, identity/reputation/validation registries, agent schema, chains & addresses, trust model with real-world scenarios, integration patterns, Agent0 TypeScript SDK examples, Python SDK recipes.

### `8004scan` — API Integration

Wraps the [8004scan Public API](https://www.8004scan.io/api/v1/public/docs/openapi.json) for agent discovery, semantic search, statistics, and feedback queries. Uses `curl` + `jq`.

**Endpoints**: list agents, get agent details, search agents, account lookups, platform stats, supported chains, feedbacks.

### `8004scan-webhooks` — Real-Time Events

Subscribe to 8004scan webhook events for real-time notifications. Covers webhook registration, event subscriptions, HMAC-SHA256 signature verification, and delivery monitoring.

**Events**: `validation.requested`, `validation.completed`, `feedback.received`, `feedback.revoked`, `star.received`, `star.removed`.

### Installation

```bash
# Clone and use with Claude Code
git clone https://github.com/jiayaoqijia/8004.git
cd 8004
# Skills are auto-detected from .claude/skills/
```

## Key Addresses

Deterministic vanity addresses deployed via CREATE2:

| Registry | Testnet | Mainnet |
|----------|---------|---------|
| Identity | `0x8004A818BFB912233c491871b3d84c89A494BD9e` | `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` |
| Reputation | `0x8004B663056A597Dffe9eCcC1965A193B7388713` | Same |
| Validation | `0x8004Cb1BFb31DAf7788923b405b754f57acEB4272` | Same |

## 8004scan Public API

Base URL: `https://www.8004scan.io/api/v1/public`

| Endpoint | Description |
|----------|-------------|
| `GET /agents` | List agents with pagination and filters |
| `GET /agents/{chainId}/{tokenId}` | Get agent details |
| `GET /agents/search` | Semantic and keyword search |
| `GET /accounts/{address}/agents` | Agents by owner wallet |
| `GET /stats` | Platform statistics |
| `GET /chains` | Supported blockchain networks |
| `GET /feedbacks` | Feedback entries with score filtering |

```bash
# Search agents
curl -s "https://www.8004scan.io/api/v1/public/agents/search?q=code+review" | jq .

# Get agent details
curl -s "https://www.8004scan.io/api/v1/public/agents/8453/17" | jq .

# Platform stats
curl -s "https://www.8004scan.io/api/v1/public/stats" | jq .
```

Optional `X-API-Key` header for elevated rate limits. See [Developer Docs](https://www.8004scan.io/developers/docs) and [OpenAPI Spec](https://www.8004scan.io/api/v1/public/docs/openapi.json).

## Trust Model

Agents earn trust through on-chain reputation feedback. Trust labels are derived from feedback count and average value:

| Emoji | Label | Condition |
|-------|-------|-----------|
| 🔴 | Untrusted | count >= 5, avg < -50 |
| 🟠 | Caution | avg < 0 |
| ⭐ | Highly Trusted | count >= 20, avg >= 80 |
| 🟢 | Trusted | count >= 10, avg >= 70 |
| 🟢 | Established | count >= 5, avg >= 50 |
| 🔵 | Emerging | count > 0, count < 5 |
| ⚪ | No Data | count = 0 |

The 8004scan leaderboard extends this with 7 dimensions: feedback score, volume, validator score, endpoint availability, activity recency, domain verification, and x402 readiness.

## Project Structure

```
.claude/skills/
├── 8004/                          # ERC-8004 protocol knowledge
│   ├── SKILL.md
│   └── references/
│       ├── protocol.md            # Three registries, lifecycle
│       ├── identity-registry.md   # ERC-721 agent NFTs
│       ├── reputation-registry.md # Feedback signals
│       ├── validation-registry.md # Third-party attestations
│       ├── agent-schema.md        # Registration file format
│       ├── chains.md              # 45+ chains with addresses
│       ├── trust-model.md         # Trust labels, boundaries, deep-dive
│       ├── integration.md         # MCP, A2A, OASF, ENS, x402
│       ├── sdk-usage.md           # Agent0 TypeScript SDK examples
│       └── python-recipes.md      # Python SDK recipes
├── 8004scan/                      # 8004scan API integration
│   ├── SKILL.md
│   └── references/
│       ├── api-reference.md       # Full endpoint documentation
│       ├── authentication.md      # API keys, rate limits
│       └── examples.md            # curl examples
└── 8004scan-webhooks/             # Real-time event webhooks
    ├── SKILL.md
    └── references/
        ├── webhook-api.md         # Webhook CRUD endpoints
        ├── events.md              # Event types and payloads
        └── verification.md        # HMAC-SHA256 verification
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for general guidelines. To create a new skill, see [CONTRIBUTING-SKILLS.md](CONTRIBUTING-SKILLS.md) and [SKILL-CHECKLIST.md](SKILL-CHECKLIST.md).

## Security

See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## Roadmap

See [ROADMAP.md](ROADMAP.md) for planned features and progress.

## License

[AGPL-3.0](LICENSE)
