---
name: invest-financial-research
description: Conduct financial research, analyze SEC/A-share filings, and retrieve company insights using a specialized knowledge base. Use when the user needs deep-dive analysis on company financials or performance.
---

# Invest Research

This skill enables deep financial research using the ValueCell Research Agent framework. It specializes in retrieving and interpreting primary-source filings and thematic knowledge.

## Capabilities

- **SEC Filing Retrieval**: Access 10-K, 10-Q, 8-K, and ownership forms (3/4/5) for US-listed companies.
- **A-Share Filing Retrieval**: Access annual, semi-annual, and quarterly reports for Chinese companies using 6-digit stock codes.
- **Hybrid Knowledge Search**: Combines semantic and keyword search across an internal index (LanceDB) of analyst commentary and historical data.
- **Real-time Web Integration**: Gathers current IR news and press releases to supplement filing data.

## Workflow & Guidelines

### 1. Information Retrieval
- Use `fetch_periodic_sec_filings` for scheduled reports (revenue, net income).
- Use `fetch_ashare_filings` for Chinese markets. **CRITICAL**: Use English report types: `annual`, `semi-annual`, or `quarterly`.
- Use `web_search` for the most recent updates not yet reflected in filings.

### 2. Analysis & Synthesis
- **Factual Queries**: Provide direct answers with numeric evidence and source links.
- **Analytical Queries**: Tell the business story behind the numbers (e.g., "Why did margins expand?").
- **Exploratory Queries**: Organize by themes (e.g., "AI Strategy", "Regulatory Risks").

### 3. Verification
- Never fabricate data. If a number is missing, state it clearly and suggest next steps.
- Prefer filing tables and MD&A sections for numeric facts.

## Tool Routing Matrix
- **Metrics/Numbers**: Filings first → Knowledge Base second.
- **Trends/Context**: Knowledge Base first → Filings to confirm details.
- **Recent Events**: Web Search first.

## Output Standards
- **Citations**: Always use `[Descriptor](file://path)` format for all data points.
- **Language**: Respond in the user's language (e.g., Chinese input → Chinese output).
- **Relatability**: Define jargon (e.g., EBITDA) and use analogies for large figures.
