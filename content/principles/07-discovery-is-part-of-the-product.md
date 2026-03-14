# Discovery Is Part of the Product

If agents can't find your capabilities, they don't exist.

---

Humans discover features through visual exploration - menus, search bars, browse pages. Agents discover features through structured metadata - API indexes, sitemaps, capability manifests, `llms.txt`.

If your site's capabilities are only discoverable through visual browsing, agents are blind to them.

**What this means for your site:**

- Ship an `llms.txt` that tells agents what your site does and where to find things.
- Your API should have a root endpoint that lists available capabilities.
- Your sitemap should be current and comprehensive.
- Use structured data (schema.org) so agents can understand what each page contains without parsing prose.
- Search results should return structured data, not just HTML snippets.

**Good example:** A marketplace with `GET /api/capabilities` returning all available actions, plus `llms.txt` at the root, plus schema.org markup on every product page.

**Bad example:** A site where the only way to find features is clicking through a hamburger menu, and the API has no index endpoint. The agent has to guess endpoint URLs.
