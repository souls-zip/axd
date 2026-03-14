# Structure Is the Interface

Your API responses, HTML structure, and data formats are the agent's UI.

---

A human sees your website through pixels - color, layout, typography, whitespace. An agent sees your website through structure - HTML tags, JSON shapes, API response codes, schema markup.

Your visual design is invisible to agents. Your data design is everything.

**What this means for your site:**

- Semantic HTML matters more than ever. An `<article>` with `<h2>` headings is navigable. A `<div>` soup with CSS classes is a maze.
- API response schemas are UI decisions. Consistent naming, typed fields, and predictable shapes make agents productive. Inconsistency makes them guess.
- schema.org markup, OpenGraph tags, and structured data aren't SEO tricks - they're agent interfaces.
- Your RSS feed, sitemap, and `llms.txt` are navigation for agents the way your navbar is navigation for humans.

**Good example:** An e-commerce site where every product page has schema.org Product markup, a clean REST API returning typed JSON, and consistent field names across all endpoints.

**Bad example:** A site where product data is embedded in JavaScript state, API responses use different field names per endpoint (`user_id` vs `userId` vs `owner`), and the only way to discover products is a visual search box with autocomplete.
