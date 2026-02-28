---
name: coingecko
description: Fetch cryptocurrency prices, on-chain token data, trending pools, and pool search via CoinGecko x402 API. Use when the user asks about crypto prices, token market data, or DeFi pool info.
---

# coingecko Skill

Pay-per-request crypto market data from CoinGecko. No API key needed -- payment is handled automatically by the Obul proxy.

## When to Use
- User asks for the current price of a cryptocurrency (e.g. "What's the price of Bitcoin?")
- User wants on-chain token price or liquidity data by contract address
- User wants to find or search for DeFi pools or tokens
- User asks about trending pools on a specific network
- User needs market cap, volume, or 24h change data

## Endpoints

### Simple Price
- **URL**: `https://pro-api.coingecko.com/api/v3/x402/simple/price`
- **Method**: GET
- **Pricing**: ~$0.01 per request

Query parameters: `ids` (comma-separated coin IDs, e.g. `bitcoin,ethereum`), `vs_currencies` (e.g. `usd`), `include_market_cap` (true/false), `include_24hr_vol` (true/false), `include_24hr_change` (true/false).

**Request:**
```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/simple/price?ids=bitcoin,ethereum&vs_currencies=usd&include_24hr_change=true"
```

**Response:** JSON object keyed by coin ID with price, market cap, volume, and change fields.

### On-Chain Token Price
- **URL**: `https://pro-api.coingecko.com/api/v3/x402/onchain/simple/networks/{network}/token_price/{contract_address}`
- **Method**: GET
- **Pricing**: ~$0.01 per request

Path parameters: `network` (e.g. `base`, `eth`, `solana`), `contract_address` (token contract address).

**Request:**
```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/onchain/simple/networks/base/token_price/0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913"
```

**Response:** JSON with token price, market cap, volume, and liquidity data.

### Token Data by Address
- **URL**: `https://pro-api.coingecko.com/api/v3/x402/onchain/networks/{network}/tokens/{contract_address}`
- **Method**: GET
- **Pricing**: ~$0.01 per request

**Request:**
```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/onchain/networks/eth/tokens/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48"
```

**Response:** JSON with detailed token data including price, liquidity, and market metrics.

### Search Pools
- **URL**: `https://pro-api.coingecko.com/api/v3/x402/onchain/search/pools`
- **Method**: GET
- **Pricing**: ~$0.01 per request

Query parameters: `query` (search term -- contract address, token name, or symbol).

**Request:**
```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/onchain/search/pools?query=USDC"
```

**Response:** JSON array of matching pools with token pair info, volume, and liquidity.

### Trending Pools by Network
- **URL**: `https://pro-api.coingecko.com/api/v3/x402/onchain/networks/{network}/trending_pools`
- **Method**: GET
- **Pricing**: ~$0.01 per request

Path parameters: `network` (e.g. `solana`, `base`, `eth`).

**Request:**
```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/onchain/networks/solana/trending_pools"
```

**Response:** JSON array of trending pools on the specified network with volume and price data.

## Notes
- All endpoints cost $0.01 USDC per request. Pricing is subject to change.
- CoinGecko coin IDs (used in `ids` param) are lowercase slugs, e.g. `bitcoin`, `ethereum`, `solana`, `usd-coin`.
- Network IDs for on-chain endpoints: `eth`, `base`, `solana`, `polygon_pos`, `arbitrum`, `optimism`, `bsc`, `avalanche`, and 250+ others.
- The Obul proxy handles x402 payment automatically -- no USDC wallet or payment header needed.
