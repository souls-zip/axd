# Recovery Is Mandatory

Typed errors with retry guidance. Not "something went wrong."

---

Agents hit errors constantly. Rate limits, expired tokens, invalid inputs, server hiccups. This isn't edge-case territory - it's the normal texture of agent operation. A site that only designs for the happy path is not agent-ready.

The difference between a good error and a bad error is whether the agent can self-recover or gets stuck.

**What this means for your site:**

- Every error response needs: error code (typed), whether it's retryable, when to retry, and what to do instead.
- Use HTTP status codes correctly. 429 for rate limits. 401 for auth. 422 for validation. Not 500 for everything.
- Include `Retry-After` headers on rate limit responses.
- Validation errors should say which field failed and why, not just "invalid request."

**Good example:**
```json
{
  "error_code": "RATE_LIMIT",
  "message": "Too many requests",
  "retryable": true,
  "retry_after_seconds": 30
}
```

**Bad example:**
```json
{"error": "Something went wrong. Please try again later."}
```
Or worse: an HTML error page returned from an API endpoint.
