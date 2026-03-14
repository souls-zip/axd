# Trust Must Be Computable

Machine-readable provenance, not marketing badges.

---

When a human evaluates whether to trust a site, they look at design quality, brand recognition, reviews, SSL padlock. When an agent evaluates trust, it needs structured signals it can compute on.

"Trusted by 10,000 companies" as a PNG badge is useless to an agent. `{"verified": true, "users": 10000, "uptime_sla": "99.9%", "last_audit": "2026-01"}` is actionable.

**What this means for your site:**

- Expose trust signals as structured data, not just visual badges.
- Include version information and changelogs in your API responses.
- Publish your uptime status in a machine-readable format.
- Make security posture discoverable (HTTPS, CSP headers, signed responses).
- If you have certifications or audits, link to them in a structured way.

**Good example:** A SaaS site with a `/status` endpoint returning structured uptime data, a `/changelog` endpoint with versioned updates, and schema.org Organization markup with verified identity.

**Bad example:** A site with a "Trusted by Fortune 500 Companies" banner image and no structured data about reliability, versioning, or identity.
