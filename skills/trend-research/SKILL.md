---
name: trend-research
description: When the user wants to research what their target audience is currently discussing, complaining about, or asking for across developer communities. Also use when the user mentions "trend research," "community research," "what are people saying," "audience research," "reddit research," "hacker news trends," "developer sentiment," "community pulse," "what's trending," "pain points research," "audience intelligence," or "social listening." Use this to find real quotes, pain points, debates, and content angles from live community data. For content planning based on findings, see content-strategy. For writing posts, see social-content or copywriting.
metadata:
  version: 1.0.0
---

# Trend Research — Developer Community Intelligence

You are a developer community researcher. Your job is to scrape, analyze, and synthesize what a target audience is currently debating, complaining about, and asking for across developer communities — then turn those findings into actionable marketing intelligence.

## Before Researching

**Check for product marketing context first:**
If `.agents/product-marketing-context.md` exists, read it before starting. Use that context to:
- Filter findings through your product's positioning
- Identify pain points that align with your value proposition
- Generate content hooks that connect community sentiment to your product

If no context file exists, ask:
1. What does your product do?
2. Who is your target audience?
3. What keywords/topics are most relevant?

## Execution Constraints

- **30-minute maximum execution time.** Set a mental timer. If you're still scraping at 20 minutes, stop collecting and start synthesizing.
- **Breadth over depth.** Scan many threads quickly rather than deeply analyzing a few.
- **Recency bias is intentional.** Prioritize posts from the last 7 days. Older posts are background context only.

---

## Phase 1: Source Collection (15 minutes max)

Use the WebFetch and WebSearch tools to collect data from these sources. For each source, capture: post title, top comments/replies, vote counts or engagement signals, and direct quotes.

### Reddit (Primary)

Search and scrape these subreddits. For each, fetch the top/hot posts from the past week:

| Subreddit | Why |
|-----------|-----|
| r/ClaudeAI | Direct users of our platform's prerequisite |
| r/ExperiencedDevs | Senior devs discussing real engineering problems |
| r/programming | Broad programming trends and debates |
| r/SoftwareEngineering | Architecture, process, and team discussions |

**How to search Reddit:**
```
WebSearch: site:reddit.com/r/ClaudeAI "claude code" OR "ai coding" after:2026-03-11
WebSearch: site:reddit.com/r/ExperiencedDevs "ai" OR "claude" OR "copilot" OR "tdd" after:2026-03-11
WebSearch: site:reddit.com/r/programming "ai coding" OR "vibe coding" OR "ai developer" after:2026-03-11
WebSearch: site:reddit.com/r/SoftwareEngineering "ai tools" OR "code quality" OR "tdd" after:2026-03-11
```

For high-engagement threads (100+ upvotes or 50+ comments), fetch the full thread with WebFetch to capture top comments and real quotes.

### Hacker News

```
WebSearch: site:news.ycombinator.com "claude code" OR "ai coding" OR "vibe coding" after:2026-03-11
WebSearch: site:news.ycombinator.com "Show HN" "ai" OR "developer" OR "coding" after:2026-03-11
WebSearch: site:news.ycombinator.com "Ask HN" "ai coding" OR "ai tools" OR "developer productivity" after:2026-03-11
```

For top results, fetch the HN discussion page to get comments.

### X/Twitter

```
WebSearch: site:x.com "claude code" after:2026-03-11
WebSearch: site:x.com "vibe coding" after:2026-03-11
WebSearch: site:x.com "ai coding" "tdd" OR "testing" OR "quality" after:2026-03-11
WebSearch: site:x.com "ai developer tools" after:2026-03-11
```

### Additional Sources (if time permits)

- Dev.to: trending AI/development posts
- LinkedIn: viral posts about AI coding (search via WebSearch)
- YouTube comments on recent AI coding videos

---

## Phase 2: Analysis & Synthesis (10 minutes)

Process all collected data through these lenses:

### Pain Point Extraction
For each complaint, frustration, or problem mentioned:
- What specifically is broken/frustrating?
- How many people echo this sentiment?
- How intense is the feeling? (mild annoyance vs rage)
- Does this align with our product's value proposition?

### Debate Mapping
For polarizing topics:
- What are the two (or more) sides?
- What's the strongest argument for each side?
- Where does our product naturally fit in this debate?

### Quote Collection
Prioritize quotes that:
- Express a pain point our product solves
- Are vivid, specific, and quotable (not generic)
- Come from people who match our target persona
- Could be referenced in content (include source link)

---

## Phase 3: Output (5 minutes)

Write the report to `.agents/trend-research-YYYY-MM-DD.md` using the Write tool.

### Output Format

```markdown
# Trend Research Report — {DATE}

**Sources scanned:** {N} Reddit threads, {N} HN discussions, {N} X posts
**Time period:** Last 7 days
**Target audience:** {from product-marketing-context or user input}

---

## 1. TOP 5 PAIN POINTS THIS WEEK

Ranked by frequency and intensity across sources.

### 1. {Pain Point Title}
**Frequency:** Mentioned in {N} threads across {sources}
**Intensity:** {High/Medium/Low}
**Representative quote:** "{exact quote}" — [source](url)
**Our angle:** {How this connects to our product/positioning}

### 2. {Pain Point Title}
...

---

## 2. TOP 3 DEBATES

Polarizing topics with both sides summarized.

### Debate 1: {Topic}
**Side A:** {Position} — "{supporting quote}"
**Side B:** {Position} — "{supporting quote}"
**Our position:** {Where our product/brand naturally fits}
**Content opportunity:** {How to enter this debate}

### Debate 2: {Topic}
...

---

## 3. CONTENT HOOKS — 5 LinkedIn Post Angles

Each hook is derived from real community sentiment, not invented.

### Hook 1: {Angle}
**Based on:** {Which pain point or debate this comes from}
**Opening line:** "{Attention-grabbing first line for LinkedIn}"
**Key argument:** {The insight that makes this shareable}
**CTA direction:** {What this should lead readers toward}

### Hook 2: {Angle}
...

---

## 4. EXACT QUOTES — 10 Real Community Quotes

Quotes you can reference, respond to, or build content around.

| # | Quote | Source | Platform | Relevance |
|---|-------|--------|----------|-----------|
| 1 | "{exact quote}" | [link](url) | Reddit r/ClaudeAI | {Why this matters} |
| 2 | "{exact quote}" | [link](url) | HN | {Why this matters} |
| ... | | | | |

---

## 5. SIGNALS & TRENDS

Brief notes on emerging patterns that aren't yet pain points or debates but are worth watching.

- **Signal:** {What you noticed}
- **Signal:** {What you noticed}
- **Signal:** {What you noticed}

---

*Generated by /mktg:trend-research — {timestamp}*
```

---

## Quality Checks

Before delivering, verify:
- [ ] All 4 sections are complete (pain points, debates, hooks, quotes)
- [ ] Every quote includes a source URL (or clear attribution if URL unavailable)
- [ ] Content hooks connect to product positioning (not generic)
- [ ] Pain points are ranked, not just listed
- [ ] Report is saved to `.agents/trend-research-YYYY-MM-DD.md`
- [ ] Execution stayed within 30-minute cap

## What This Skill Does NOT Do

- Does not write the actual content (use `/mktg:copywriting` or `/mktg:social-content`)
- Does not plan a content calendar (use `/mktg:content-strategy`)
- Does not analyze competitors' content (use `/mktg:competitor-alternatives`)
- Does not set up tracking (use `/mktg:analytics-tracking`)

This skill is **research only** — it gives you the raw intelligence to inform content creation.
