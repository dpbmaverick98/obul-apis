# Obul Skills

Obul is the **universal API gateway for the agent economy**. It proxies requests to x402-enabled APIs and handles payment automatically — no crypto wallet, no USDC, no gas fees. One `OBUL_API_KEY`, consolidated billing, scoped keys with spending caps. Pay-per-use access to any supported service.

## What is x402?

[x402](https://www.x402.org/) is an open payment protocol (by Coinbase) that uses HTTP 402 for instant, per-request stablecoin payments. Obul abstracts x402 away entirely — you just make normal HTTP requests.

## Getting Started

1. **Sign up** at [my.obul.ai](https://my.obul.ai) (free, ~30 seconds)
2. **Set your API key** as an environment variable:
   ```sh
   export OBUL_API_KEY="your-key-here"
   ```
3. **Make requests** through the proxy. URL pattern:
   ```
   https://proxy.obul.ai/proxy/{scheme}/{host}{path}
   ```
   All requests must include the `x-obul-api-key` header.

## Plugin Categories

| | Category | Plugin | Skills |
|---|---|---|---|
| 🔗 | Infrastructure | [obul-core](plugins/obul-core/) | obul-proxy, pinata, cnvrting |
| 🔥 | Web Scraping | [obul-scrape](plugins/obul-scrape/) | firecrawl, browserbase, zyte, minifetch, x402engine-web |
| 🔍 | Web Search | [obul-search](plugins/obul-search/) | firecrawl-search, exa |
| 🐦 | Social Media | [obul-social](plugins/obul-social/) | x-search, neynar, reddit |
| 💰 | Blockchain/DeFi | [obul-crypto](plugins/obul-crypto/) | coingecko, heyelsa, zapper, slamai, silverback, blocksec, x402engine-chain, ordiscan |
| 🎨 | Media | [obul-media](plugins/obul-media/) | freepik, x402engine-image, x402engine-audio, dtelecom, aibeats, genbase |
| 🛡️ | Security & Risk | [obul-security](plugins/obul-security/) | orac, blackswan |
| 👤 | Lead Enrichment | [obul-leads](plugins/obul-leads/) | stableenrich |

## Usage Example

```sh
curl -s -X POST "https://proxy.obul.ai/proxy/https/firecrawl.x402endpoints.com/v1/scrape" \
  -H "Content-Type: application/json" \
  -H "x-obul-api-key: $OBUL_API_KEY" \
  -d '{"url": "https://example.com", "formats": ["markdown"]}'
```

## Claude Code Plugin

This repo is a Claude Code plugin marketplace. Add it and install all plugins:

```sh
claude plugin marketplace add https://github.com/obulai/obul-plugin.git
claude plugin install obul-core obul-scrape obul-search obul-social obul-crypto obul-media obul-security obul-leads
```

### Commands

| Command | Plugin | Description | Cost |
|---------|--------|-------------|------|
| `/obul-core:proxy <url>` | core | Proxy any request to an x402 endpoint | Varies |
| `/obul-scrape:scrape <url>` | scrape | Scrape a webpage | $0.001 |
| `/obul-scrape:screenshot <url>` | scrape | Screenshot a webpage | $0.01 |
| `/obul-search:search <query>` | search | Search the web | $0.002 |
| `/obul-social:x-search <query>` | social | Search X/Twitter | $0.001 |
| `/obul-social:farcaster <query>` | social | Search Farcaster | $0.01 |
| `/obul-crypto:price <coin>` | crypto | Get crypto prices | $0.01 |
| `/obul-crypto:wallet <address>` | crypto | Look up wallet info | $0.001 |
| `/obul-media:imagine <prompt>` | media | Generate an image | $0.015+ |
| `/obul-media:transcribe <file>` | media | Transcribe audio or generate speech | $0.01+ |
| `/obul-security:audit <target>` | security | Security analysis | $0.005+ |
| `/obul-leads:enrich <query>` | leads | People/company enrichment & lead discovery | $0.02+ |

See [PLUGIN.md](PLUGIN.md) for full installation and usage details.

## Resources

- [Obul Dashboard](https://my.obul.ai) — manage keys, view usage, set spending caps
- [x402 Protocol](https://www.x402.org/) — the payment protocol powering Obul
- [Writing a New Skill](https://github.com/dpbmaverick98/Agent_Army_Skills/blob/main/Agent_Army_Skills_Obul/how-to-write-obul-skills.md) — guide for contributors
