# Auth Is Experience

Browser-only OAuth kills agents. Scoped tokens enable them.

---

Authentication is where most agent interactions die. OAuth flows requiring browser redirects. CAPTCHAs. Email verification loops. Multi-step wizards. These work fine for humans clicking through a browser. For agents, they're brick walls.

**What this means for your site:**

- Offer API keys or bearer tokens as an auth option, not just browser-based OAuth.
- Separate read and write scopes. An agent fetching product data shouldn't need the same permissions as one placing orders.
- Return clear permission errors: "You have read access but this action requires write scope" is actionable. "403 Forbidden" is not.
- Support delegated auth so agents can act on behalf of users without storing passwords.
- Don't put CAPTCHAs on API endpoints.

**Good example:** A site that offers both browser-based login for humans AND API key auth for agents, with scoped permissions (read, write, admin) that agents can request granularly.

**Bad example:** A site where the only way to authenticate is clicking through a Google OAuth popup, solving a CAPTCHA, and confirming via email. No programmatic alternative exists.
