# Autonomy Must Be Bounded

Label safe vs dangerous actions. Let agents move fast within limits.

---

An agent interacting with your site needs to know what's safe to do on its own and what requires human confirmation. Without this, agents either over-ask (slow and annoying) or over-act (dangerous).

The best sites make this explicit: read operations are always safe, writes are usually fine, deletes need confirmation, payments need approval.

**What this means for your site:**

- Label your API actions by risk level: read, write, destructive, admin.
- Make read-only operations lightweight and unrestricted.
- For destructive actions, support confirmation flows that agents can handle programmatically (not "are you sure?" popups).
- Document which actions are reversible and which aren't.
- Provide a "dry run" or preview mode for high-risk operations.

**Good example:** An API where `GET` endpoints require basic auth, `POST/PUT` require write scope, and `DELETE` requires a confirmation token from a separate endpoint. Risk levels documented per endpoint.

**Bad example:** Every endpoint requires the same auth level and there's no indication which actions are reversible. An agent can accidentally delete a user account with the same ease as fetching a profile.
