---
name: exa
description: Neural and semantic web search using Exa. Use when the user needs intelligent search, finding similar pages, retrieving page contents, or getting AI-generated answers with citations.
---

# exa Skill

Search the web using Exa's neural search engine. Exa excels at semantic/meaning-based search, finding pages similar to a URL, extracting page contents, and generating answers with citations.

## When to Use
- User needs semantic or neural search (finding pages by meaning, not just keywords)
- User wants to find pages similar to a given URL
- User needs to extract clean text content from specific URLs
- User wants an AI-generated answer backed by web search citations
- User asks for research papers, company pages, news, or tweets by category

## Endpoints

### Search
- **URL**: `https://api.exa.ai/search`
- **Method**: POST
- **Pricing**: ~$0.005 per request

**Request:**
```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "latest research on LLM reasoning",
    "type": "auto",
    "numResults": 5,
    "contents": {
      "text": true
    }
  }' \
  "https://proxy.obul.ai/proxy/https/api.exa.ai/search"
```

**Parameters:**
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | required | Search query |
| `type` | string | `"auto"` | `"neural"`, `"auto"`, `"keyword"` |
| `numResults` | integer | 10 | Number of results (max 100) |
| `category` | string | — | `"company"`, `"research paper"`, `"news"`, `"tweet"`, `"personal site"`, `"financial report"`, `"people"` |
| `includeDomains` | array | — | Restrict results to these domains |
| `excludeDomains` | array | — | Exclude these domains |
| `startPublishedDate` | string | — | ISO 8601 date filter start |
| `endPublishedDate` | string | — | ISO 8601 date filter end |
| `contents.text` | bool/object | — | Include full text. Object form: `{"maxCharacters": 2000}` |
| `contents.highlights` | bool/object | — | Include relevant snippets. Object form: `{"maxCharacters": 500, "query": "specific focus"}` |
| `contents.summary` | object | — | LLM-generated summary. `{"query": "summarize the key findings"}` |

**Response:**
```json
{
  "requestId": "abc123",
  "results": [
    {
      "id": "result-id",
      "url": "https://example.com/article",
      "title": "Article Title",
      "publishedDate": "2025-01-15T00:00:00.000Z",
      "author": "Author Name",
      "text": "Full page content...",
      "highlights": ["Relevant snippet 1", "Relevant snippet 2"],
      "summary": "LLM-generated summary of the page"
    }
  ],
  "costDollars": { "total": 0.005 }
}
```

### Find Similar
- **URL**: `https://api.exa.ai/findSimilar`
- **Method**: POST
- **Pricing**: ~$0.005 per request

**Request:**
```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "https://example.com/interesting-article",
    "numResults": 5,
    "contents": {
      "text": true
    }
  }' \
  "https://proxy.obul.ai/proxy/https/api.exa.ai/findSimilar"
```

**Parameters:**
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `url` | string | required | URL to find similar pages for |
| `numResults` | integer | 10 | Number of results |
| `includeDomains` | array | — | Restrict to these domains |
| `excludeDomains` | array | — | Exclude these domains |
| `contents.text` | bool/object | — | Include full text content |
| `contents.highlights` | bool/object | — | Include relevant snippets |

**Response:** Same format as Search.

### Get Contents
- **URL**: `https://api.exa.ai/contents`
- **Method**: POST
- **Pricing**: ~$0.002 per request

**Request:**
```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "urls": ["https://example.com/page1", "https://example.com/page2"],
    "text": true
  }' \
  "https://proxy.obul.ai/proxy/https/api.exa.ai/contents"
```

**Parameters:**
| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `urls` | array | required | URLs to extract content from |
| `text` | bool/object | — | Include full text. Object form: `{"maxCharacters": 5000}` |
| `highlights` | bool/object | — | Include relevant snippets |
| `summary` | object | — | LLM-generated summary |
| `maxAgeHours` | integer | — | Cache freshness; triggers live crawl if stale |
| `subpages` | integer | — | Number of subpages to also crawl |

**Response:**
```json
{
  "results": [
    {
      "url": "https://example.com/page1",
      "title": "Page Title",
      "publishedDate": "2025-01-15T00:00:00.000Z",
      "author": "Author Name",
      "text": "Full extracted page content..."
    }
  ]
}
```

### Answer
- **URL**: `https://api.exa.ai/answer`
- **Method**: POST
- **Pricing**: ~$0.01 per request

**Request:**
```bash
curl -sS -X POST \
  -H "X-Obul-Api-Key: ${OBUL_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "What are the latest developments in x402 payments?",
    "text": true
  }' \
  "https://proxy.obul.ai/proxy/https/api.exa.ai/answer"
```

**Response:** JSON object with an AI-generated answer and an array of cited source results.

## Notes
- Exa's neural search is best for semantic queries where meaning matters more than exact keyword matching
- Use `"type": "keyword"` for exact-match searches, `"neural"` for semantic, `"auto"` to let Exa decide
- The `category` parameter significantly improves result quality when you know the content type
- `findSimilar` is uniquely powerful for discovering related content from a known good URL
- `contents` is useful when you already have URLs and just need to extract their text
- Settlement is in USDC on Base chain, handled automatically by the Obul proxy
