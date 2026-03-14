# Every Action Needs Feedback

Agents can't see your success toast. Return structured results.

---

When a human submits a form, they see a green checkmark, a success message, maybe a confetti animation. An agent sees... the HTTP response. If that response is `200 OK` with an empty body, the agent has no idea what happened.

Agents have no screen. They rely entirely on structured responses to know if their actions worked.

**What this means for your site:**

- Every POST/PUT/DELETE returns the resulting state, not just a status code.
- Long-running operations return a job ID and a way to check progress.
- Success responses include what changed AND what to do next.
- Form submissions return structured confirmation, not a redirect to a "thank you" page with no data.

**Good example:**
```json
{
  "status": "order_placed",
  "order_id": "ORD-4521",
  "total": "$42.00",
  "estimated_delivery": "2026-03-18",
  "next_actions": ["track_order", "cancel_order"]
}
```

**Bad example:**
```
HTTP 302 → /thank-you
```
(Agent follows the redirect, gets an HTML page saying "Thanks for your order!" with no structured data.)
