# Memory and Events for Long Work

Agents don't stay on the page. Support async, webhooks, resumability.

---

Humans keep a browser tab open. Agents don't. They complete a task and move on. If your site requires continuous presence - keeping a session alive, staying on a page, waiting for a real-time update - agents can't use it.

**What this means for your site:**

- Long-running operations should be async. Return a job ID, let agents poll or subscribe for completion.
- Support webhooks so agents can be notified when something changes instead of polling.
- Sessions should be resumable. If an agent comes back tomorrow with the same token, it should pick up where it left off.
- Don't rely on WebSocket connections that agents can't maintain across sessions.
- Include timestamps and state in API responses so agents can detect what changed since their last visit.

**Good example:** A file conversion site that accepts an upload, returns a job ID, and sends a webhook when the conversion is done. The agent doesn't need to keep a connection open.

**Bad example:** A site where you upload a file and have to stay on the page watching a progress bar until it finishes. If you navigate away, the job is lost.
