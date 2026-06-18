[Fast Reddit Scraper](https://apify.com/timgreen/fast-reddit-scraper?fpr=data)

## Fast Reddit Scraper - Extract Reddit Posts and Comments Data

Extract Reddit posts and comments from any subreddit or search query. Fast, reliable Reddit scraping with detailed metadata including upvotes, timestamps, and nested comment threads.

### What does Fast Reddit Scraper do?

Fast Reddit Scraper is a powerful Apify actor that extracts comprehensive data from [Reddit](https://reddit.com), the world's largest social discussion platform. This Reddit API scraper can collect posts, comments, and engagement metrics from any subreddit or search query without requiring Reddit authentication.

The scraper handles Reddit's complex structure including nested comment threads, pagination, and dynamic content loading. Extract up to 1,000 posts with full metadata including titles, content, author information, vote counts, timestamps, and optionally a list of top comments per post including nested comments.

### Why scrape Reddit data?

Reddit contains authentic user-generated content across millions of communities, making it invaluable for various business and research applications:

- **Market Research** - Analyze customer opinions, product feedback, and emerging trends in specific niches
- **Sentiment Analysis** - Monitor brand mentions and public opinion about products, services, or topics
- **Content Strategy** - Identify viral content patterns and trending topics for content creation
- **Competitive Intelligence** - Track competitor mentions and customer complaints or praise
- **Lead Generation** - Find potential customers expressing interest in relevant products or services
- **Academic Research** - Collect data for social science studies, linguistics research, and behavioral analysis
- **Crisis Management** - Early detection of negative sentiment or emerging issues
- **Product Development** - Discover unmet customer needs and feature requests
- **SEO and Content Marketing** - Identify popular questions and topics for content optimization
- **Social Listening** - Real-time monitoring of brand reputation and industry discussions

### How to scrape Reddit posts and comments

1. **Choose your data source**: Enter either a specific subreddit name (e.g., "technology") or a search query to find posts across all Reddit
2. **Set extraction limits**: Specify the maximum number of posts to extract (1-1000). This is a soft limit -- the actual number of posts output may be slightly higher.
3. **Configure sorting**: Choose from new, hot, top, best, rising, relevance, or comment count.
4. **Include comments** (optional): Enable comment extraction to get a list of top-rated comments with nested replies per post
5. **Run the scraper**: The actor will extract structured data in JSON format ready for analysis

### Reddit scraper input parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| **Max Posts** | Integer | Approximate Maximum number of posts to extract (1-1000) | 1000 |
| **Subreddit** | String | Target subreddit name (ignored if search query is set) | "LifeProTips" |
| **Search Query** | String | Search term to find posts across all Reddit | - |
| **Sort** | Select | Sort order: new, best, hot, top, rising, relevance, comments | "new" |
| **Include Comments** | Boolean | Extract a list of top comments with nested replies (may not include all comments) | false |

**Note**: Relevance and Comment Count sorting only work with search queries, while Best and Rising only work with subreddits.

**Note**: The number of posts extracted may be less than the maximum set and depends on the subreddit or search query.

### Reddit data output format

The scraper returns structured JSON data for each post with comprehensive metadata:

```
{
  "subreddit": "OpenAI",
  "url": "https://reddit.com/r/OpenAI/comments/1n6pncz/weekly_limit_in_codex_ouch/",
  "title": "Weekly limit in Codex.. ouch",
  "content": "So.. I, as many, switched to Codex two days ago...",
  "link_flair": "Discussion",
  "created_at": "2025-09-02T11:22:06.000-06:00",
  "over_18": false,
  "author": "yo_mono",
  "upvotes": 5,
  "downvotes": 0,
  "num_comments": 4,
  "comments": [
    {
      "url": "https://reddit.com/r/OpenAI/comments/1n6pncz/weekly_limit_in_codex_ouch/nc1sixy/",
      "content": "Avoid using GPT 5 high at all costs. Stick to low and minimal...",
      "created_at": "2025-09-02T11:38:29.000-06:00",
      "author": "bananasareforfun",
      "upvotes": 2,
      "downvotes": 0,
      "comments": [...]
    }
  ]
}
```

**Extracted data fields include:**

- Post title, content, and URL
- Author username
- Upvote and downvote counts
- Creation timestamps
- Subreddit and flair information
- NSFW content flags
- Comment count and nested comment threads
- Comment metadata with vote ratios

### Reddit scraping API integration

Use this Reddit scraper in your applications via the Apify API:

```
const { ApifyClient } = require('apify-client');

const client = new ApifyClient({
    token: 'MY-APIFY-TOKEN',
});

// Starts an actor and waits for it to finish.
const { defaultDatasetId } = await client.actor('timgreen/fast-reddit-scraper').call();

// Fetches results from the actor's dataset.
const { items } = await client.dataset(defaultDatasetId).listItems();
```

### Reddit scraping best practices

**Ethical data collection**: Only scrape publicly available Reddit content and respect community guidelines. This tool accesses the same data visible to any Reddit visitor.

**Rate limiting**: The scraper automatically handles Reddit's rate limits and uses residential proxies to avoid being blocked.

**Data freshness**: Reddit content changes rapidly. For time-sensitive analysis, run extractions frequently to capture the latest posts and comments.

**Comment extraction**: Enable comments only when necessary, as it significantly increases extraction time. Comments are sorted by upvote ratio for quality.

### Frequently asked questions

**Is it legal to scrape Reddit data?**
Yes, this scraper only accesses publicly available Reddit content that any user can view. Always comply with Reddit's Terms of Service and your local data regulations.

**How fast is the Reddit data extraction?**
Without comments: Approximately 800 posts per minute. With comments enabled: Approximately 100 posts per minute depending on comment volume.

**Can I scrape private subreddits?**
No, this scraper only accesses public Reddit content. Private or restricted subreddits require special permissions.

**What's the difference between subreddit and search scraping?**
Subreddit scraping extracts posts from a specific community. Search scraping finds posts matching keywords across all Reddit communities.

Start extracting valuable Reddit data today with Fast Reddit Scraper - your gateway to authentic social media insights and community intelligence.