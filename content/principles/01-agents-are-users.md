# Agents Are Users

Treat agents as a real user persona alongside your human users.

---

When you design a website, you think about who's using it. You create personas, user journeys, accessibility considerations. Agents need the same treatment.

An agent visiting your site has goals, constraints, and failure modes - just like a human user. The difference is how they interact: agents read structure, not pixels. They parse HTML, call APIs, and consume JSON - not click buttons and scan layouts.

**What this means for your site:**

- Add an agent persona to your design process. What does an agent need from your homepage? Your docs? Your checkout flow?
- Your API is an interface, not plumbing. Design it with the same care you'd put into your visual UI.
- Test your site with real agents, not just humans using agent-like tools.
- If your site works great for humans but agents can't use it, you've excluded a growing user base.

**Good example:** A docs site that ships both a visual interface and a machine-readable `llms.txt` index. Agents get the same content, formatted for how they consume it.

**Bad example:** A site that puts all its content behind JavaScript rendering with no API, no structured data, and no server-side HTML. Agents see an empty page.
