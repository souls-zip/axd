# Context Beats Prompting

A self-describing site beats clever instructions every time.

---

When an agent arrives at your site, it needs to understand what it's looking at. If your pages, APIs, and docs are clear and well-structured, the agent succeeds regardless of how it was prompted. If they're ambiguous, no amount of prompt engineering saves it.

Context is what your site communicates about itself. Prompting is what someone tells the agent about your site. You control the first. You don't control the second.

**What this means for your site:**

- Name things clearly. If your endpoint does search, call it `/search`, not `/api/v2/query-resolver`.
- Describe your API at the top level. A discovery endpoint or `llms.txt` that explains "here's what this site does and here are the main actions" lets any agent orient instantly.
- Include purpose statements. "This page lists all products in the Electronics category" is context. An agent reading it knows where it is.
- Write docs that work without prerequisite knowledge. An agent won't have read your blog post explaining your naming conventions.

**Good example:** An API with a root endpoint returning `{"name": "Acme Store API", "version": "2.0", "capabilities": ["search", "cart", "checkout"]}` with links to each.

**Bad example:** An API where you need to read a 40-page PDF guide to understand which of 200 endpoints to call first.
