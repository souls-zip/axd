# AX Anti-Patterns

25 things that break agent experience. If you recognize your product in this list, fix it.

**Status:** Draft v0.1

---

## Access Anti-Patterns

### 1. The Browser-Only Auth Flow
Auth requires visual browser interaction (OAuth redirects, CAPTCHAs) with no programmatic alternative. Agents can't click buttons.

### 2. The All-or-Nothing Token
A single token grants full access with no scope separation. Agents can't operate with least privilege.

### 3. The Silent Permission Failure
Returns 403 with no explanation of which permission is missing or how to obtain it.

---

## Documentation Anti-Patterns

### 4. The Pretty Website, Useless API
Beautiful landing page, marketing copy everywhere, but the actual API docs are an afterthought - incomplete, outdated, or buried.

### 5. The PDF Documentation
Product docs are a 200-page PDF. Not searchable, not linkable, not parseable. Agents need structured text, not page layouts.

### 6. The Marketing Tool Description
Tool descriptions read like ad copy ("Our powerful, innovative solution transforms...") instead of stating what the tool does, what it accepts, and what it returns.

### 7. The Video-Only Tutorial
Key information is only available in a video walkthrough. Agents can't watch videos. Write it down.

---

## API Design Anti-Patterns

### 8. The Inconsistent Naming
`user_id` in one endpoint, `userId` in another, `owner` in a third. Forces agents to maintain translation tables instead of building patterns.

### 9. The Silent Mutation
POST endpoint that triggers side effects (sends emails, creates records, charges money) with no mention in the documentation.

### 10. The Surprise Pagination
Returns first 10 results with no indication there are more. No `total_count`, no `next_page`, no cursor. Agent thinks it has all the data.

### 11. The Kitchen Sink Endpoint
One endpoint that does 5 different things depending on which combination of parameters you send. Impossible to reason about reliably.

### 12. The Undocumented Breaking Change
API behavior changes with no version bump, no changelog, no deprecation notice. Agent's working code breaks with no explanation.

---

## Error Handling Anti-Patterns

### 13. The "Something Went Wrong" Error
Generic error message with no error code, no classification, no recovery guidance. Agent is stuck.

### 14. The Rate Limit Without Retry-After
Returns 429 but doesn't say when to retry. Agent must guess, usually wrong.

### 15. The HTML Error Page
API returns an HTML error page instead of JSON. Agent's JSON parser breaks before it can even read the error.

### 16. The Misleading Status Code
Returns 200 with `{"success": false}` in the body. Or returns 500 for a client error. Status codes should mean what HTTP says they mean.

---

## Discovery Anti-Patterns

### 17. The 100 Tools With No Categories
Dumps all capabilities in a flat list with no organization, no tags, no filtering. Agent must evaluate each one individually.

### 18. The Title-Only Search
Search returns titles and nothing else. No descriptions, no metadata, no compatibility info. Agent can't evaluate relevance without clicking into each result.

### 19. The Stale Registry
Listed items haven't been updated in months/years. No indication of maintenance status. Agent installs something that's broken or abandoned.

---

## Webhook Anti-Patterns

### 20. The Fire-and-Forget Webhook
Sends webhook once with no retry on failure. If the agent's endpoint is briefly down, the event is lost forever.

### 21. The Unsigned Webhook
No signature or verification mechanism. Agent can't distinguish legitimate events from spoofed ones.

### 22. The Untyped Webhook
Webhook payload has no schema, no event type field, no version. Agent must reverse-engineer the structure from examples.

---

## Context Anti-Patterns

### 23. The Context Dump
Loads the agent's entire history, all documentation, every available tool at once. Overwhelms the context window with irrelevant information.

### 24. The Amnesia System
No mechanism for agents to persist state between sessions. Every interaction starts from zero.

### 25. The Implicit Contract
System behavior depends on undocumented assumptions. "Everyone knows you have to call init first" - except agents don't know until they fail.

---

*Found an anti-pattern not listed here? [Contribute it.](../CONTRIBUTING.md)*
