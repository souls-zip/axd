# Accessibility for Agents

Design for the range: big models and small, rich context and limited.

---

Just like web accessibility means designing for screen readers, keyboard navigation, and color blindness, agent accessibility means designing for different agent capabilities. Some agents have 200K token context windows. Some have 8K. Some can execute JavaScript. Some can only read HTML. Some have tool access. Some just parse text.

**What this means for your site:**

- Provide content in multiple formats: visual pages for humans, structured data for rich agents, plain text for basic agents.
- Keep critical information in the HTML, not just in JavaScript state.
- Offer tiered documentation: a 100-token summary, a 1000-token overview, and full detail. Let agents choose their depth.
- Don't require JavaScript execution to access core content or API responses.
- Test with basic fetchers (curl, web_fetch), not just full browsers.
- Your most important content should be accessible in under 2000 tokens.

**Good example:** A docs site with server-rendered HTML, a `llms.txt` summary, an API for structured access, and key content visible without JavaScript. Works for any agent.

**Bad example:** A single-page app where all content loads via JavaScript, the API requires a complex SDK, and understanding the site requires loading 50K tokens of docs. Only the most capable agents can use it.
