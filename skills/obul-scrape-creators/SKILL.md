---
name: obul-scrape-creators
description: Social media data extraction API covering 22+ platforms including TikTok, Instagram, YouTube, Twitter/X, LinkedIn, Facebook, Reddit, and more.
homepage: https://scrapecreators.com
metadata:
  obul-skill: "📱"
  requires.env: OBUL_API_KEY
  requires.primaryEnv: OBUL_API_KEY
registries: {}
---

# Scrape Creators

Social media data extraction API covering 22+ platforms including TikTok, Instagram, YouTube, Twitter/X, LinkedIn, Facebook, Reddit, Pinterest, Threads, Bluesky, and more. Get profiles, posts, comments, ad libraries, and trending content.

## Authentication

All requests route through the Obul proxy. Include your Obul API key in every request:

```json
{
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

Base URL: `https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators`

To get an Obul API key, sign up at **https://my.obul.ai**.

## Common Operations

### TikTok Profile

Get TikTok user profile data.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/tiktok/profile?handle=khaby.lame",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### TikTok Video

Get TikTok video details and transcript.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v2/tiktok/video?url=https://www.tiktok.com/@user/video/123",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Instagram Profile

Get Instagram user profile.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/instagram/profile?handle=therock",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Instagram Post

Get Instagram post or reel details.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/instagram/post?url=https://www.instagram.com/p/ABC123/",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### YouTube Channel

Get YouTube channel information.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/youtube/channel?url=https://www.youtube.com/@MrBeast",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### YouTube Video

Get YouTube video details.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/youtube/video?url=https://www.youtube.com/watch?v=abc123",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### YouTube Transcript

Get transcript from a YouTube video.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/youtube/video/transcript?url=https://www.youtube.com/watch?v=abc123",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Twitter Profile

Get Twitter/X user profile.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/twitter/profile?handle=elonmusk",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Twitter Tweet

Get tweet details.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/twitter/tweet?url=https://twitter.com/user/status/123",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### LinkedIn Profile

Get LinkedIn profile data.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/linkedin/profile?url=https://www.linkedin.com/in/sundarpichai",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### LinkedIn Company

Get LinkedIn company page data.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/linkedin/company?url=https://www.linkedin.com/company/google",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Facebook Profile

Get Facebook profile data.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/facebook/profile?url=https://www.facebook.com/zuck",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Reddit Post

Get Reddit post and comments.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/reddit/subreddit?subreddit=technology",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Google Search

Get Google search results.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/google/search?query=artificial+intelligence",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Facebook Ad Library

Search Facebook ads.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/facebook/adLibrary/ad?id=ad_id",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Threads Profile

Get Threads profile.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/threads/profile?handle=zuck",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Bluesky Profile

Get Bluesky profile.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/bluesky/profile?handle=handle.bsky.social",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### Pinterest Profile

Get Pinterest profile and pins.

**Pricing:** $0.02

```json
{
  "url": "https://proxy.obul.ai/proxy/https/x402.orth.sh/scrapecreators/v1/pinterest/search?query=interior+design",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /v1/tiktok/profile` | $0.02 | TikTok profile |
| `GET /v2/tiktok/video` | $0.02 | TikTok video |
| `GET /v1/tiktok/video/transcript` | $0.02 | TikTok transcript |
| `GET /v1/instagram/profile` | $0.02 | Instagram profile |
| `GET /v1/instagram/post` | $0.02 | Instagram post |
| `GET /v2/instagram/media/transcript` | $0.02 | Instagram transcript |
| `GET /v1/youtube/channel` | $0.02 | YouTube channel |
| `GET /v1/youtube/video` | $0.02 | YouTube video |
| `GET /v1/youtube/video/transcript` | $0.02 | YouTube transcript |
| `GET /v1/twitter/profile` | $0.02 | Twitter profile |
| `GET /v1/twitter/tweet` | $0.02 | Twitter tweet |
| `GET /v1/linkedin/profile` | $0.02 | LinkedIn profile |
| `GET /v1/linkedin/company` | $0.02 | LinkedIn company |
| `GET /v1/facebook/profile` | $0.02 | Facebook profile |
| `GET /v1/facebook/post` | $0.02 | Facebook post |
| `GET /v1/facebook/adLibrary/*` | $0.02 | Facebook ads |
| `GET /v1/reddit/subreddit` | $0.02 | Reddit posts |
| `GET /v1/reddit/post/comments` | $0.02 | Reddit comments |
| `GET /v1/google/search` | $0.02 | Google search |
| `GET /v1/threads/profile` | $0.02 | Threads profile |
| `GET /v1/bluesky/profile` | $0.02 | Bluesky profile |
| `GET /v1/pinterest/*` | $0.02 | Pinterest |
| `GET /v1/twitch/*` | $0.02 | Twitch |
| `GET /v1/snapchat/*` | $0.02 | Snapchat |

## When to Use

- **Social Media Monitoring**: Track brand presence across platforms
- **Influencer Research**: Analyze influencer profiles and metrics
- **Content Aggregation**: Collect content from multiple platforms
- **Ad Intelligence**: Monitor competitor advertising
- **Trend Analysis**: Track trending content and topics
- **Competitive Research**: Monitor competitor social presence

## Best Practices

1. **Platform-Specific Params**: Each platform has specific identifier types (handle, URL, ID)
2. **Transcripts**: Use transcript endpoints for video content analysis
3. **Pagination**: Use cursors for endpoints that return lists

## Error Handling

| Code | Cause | Solution |
|------|-------|----------|
| 400 | Invalid parameters | Check URL/identifier format |
| 401 | Missing API key | Include `x-obul-api-key` header |
| 402 | Payment required | Check Obul account balance |
| 404 | Not found | Profile/content doesn't exist |
| 429 | Rate limited | Implement exponential backoff |
| 500 | Server error | Retry with exponential backoff |
