# Obul API Marketplace

A collection of pay-per-use APIs accessed through the Obul proxy (`proxy.obul.ai`). Each API is wrapped as a skill that AI agents can use with just an `OBUL_API_KEY`.

## Quick Start

Get an API key at [https://my.obul.ai](https://my.obul.ai), then make requests:

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/<upstream-url>",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Available Skills

| Category | Skills |
|----------|--------|
| Infrastructure | obul-proxy, obul-pinata, obul-cnvrting, obul-didit, obul-textbelt |
| Web Scraping | obul-firecrawl, obul-browserbase, obul-zyte, obul-minifetch, obul-x402engine-web, obul-aviato, obul-fiber, obul-notte, obul-nyne, obul-olostep, obul-riveter, obul-scrapegraph |
| Web Search | obul-firecrawl-search, obul-exa, obul-jina, obul-parallel, obul-perplexity, obul-tavily, obul-searchapi, obul-valyu |
| Social Media | obul-tweetx402, obul-neynar, obul-reddit, obul-scrape-creators |
| Blockchain/DeFi | obul-coingecko, obul-heyelsa, obul-zapper, obul-slamai, obul-silverback, obul-blocksec, obul-x402engine-chain, obul-ordiscan, obul-dome |
| Image/Audio/Video | obul-freepik, obul-x402engine-image, obul-x402engine-audio, obul-dtelecom, obul-aibeats, obul-genbase, obul-nano-banana, obul-nano-banana-2, obul-tavus, obul-zai |
| Security/Risk | obul-orac, obul-blackswan |
| Lead Enrichment | obul-stableenrich, obul-brand-dev, obul-coresignal, obul-openmart, obul-predictleads, obul-sixtyfour, obul-tomba, obul-apollo, obul-hunter, obul-logo |
| Weather Data | obul-precip |

## Repository Structure

```
apis.json                           # API marketplace manifest (lists all 61 skills)
skills/                             # All skills directory
  <service-name>/
    SKILL.md                        # Skill definition file
registry.md                         # Registry reference and publishing guide
CLAUDE.md                           # Claude Code guidance
```

## Skills

Each skill is documented in `skills/<name>/SKILL.md` with:
- Service description and use cases
- Authentication instructions
- Common operations with pricing
- Endpoint pricing reference
- Best practices and error handling

## Resources

- [Registry Guide](registry.md) - Publishing skills to registries
- [Obul Documentation](https://docs.obul.ai)
- [Get API Key](https://my.obul.ai)
