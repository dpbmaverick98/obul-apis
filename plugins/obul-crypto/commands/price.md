---
name: price
description: Get cryptocurrency prices and market data. Usage: /obul-crypto:price <coin>
---

Fetch the current price and market data for a cryptocurrency.

## Usage

```
/obul-crypto:price bitcoin
/obul-crypto:price ethereum solana
/obul-crypto:price BTC ETH SOL
```

## Workflow

1. Check that `OBUL_API_KEY` is set. If not, tell the user to get one at https://my.obul.ai/.
2. Normalize the input: map common ticker symbols to CoinGecko IDs (BTC -> bitcoin, ETH -> ethereum, SOL -> solana, etc.). If unsure, use the input as-is.
3. Fetch prices from CoinGecko via the Obul proxy:

```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/pro-api.coingecko.com/api/v3/x402/simple/price?ids={coin_ids}&vs_currencies=usd&include_24hr_change=true&include_market_cap=true&include_24hr_vol=true"
```

4. Display results in a clean table format:

| Coin | Price | 24h Change | Market Cap | 24h Volume |
|------|-------|------------|------------|------------|

5. If the CoinGecko endpoint fails or returns empty, fall back to x402engine:

```bash
curl -sS \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  "https://proxy.obul.ai/proxy/https/x402-gateway-production.up.railway.app/api/crypto/price?ids={coin_ids}"
```

## Common Ticker Mappings

| Ticker | CoinGecko ID |
|--------|-------------|
| BTC | bitcoin |
| ETH | ethereum |
| SOL | solana |
| USDC | usd-coin |
| USDT | tether |
| DOGE | dogecoin |
| ADA | cardano |
| AVAX | avalanche-2 |
| MATIC | matic-network |
| DOT | polkadot |
| LINK | chainlink |
| UNI | uniswap |
| ARB | arbitrum |
| OP | optimism |
| BASE | base-protocol |

## Cost

~$0.01 per request via CoinGecko, ~$0.001 via x402engine fallback.
