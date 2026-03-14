# Open Ecosystems Win

Let people bring their own agents. Don't lock them into yours.

---

Some sites are building their own AI assistants and making them the only way to get AI-powered interaction. That's the closed approach. The open approach is making your site work well with ANY agent - Claude, ChatGPT, custom agents, whatever the user prefers.

Open wins for the same reason the web won over AOL. Users want choice. Lock-in creates friction.

**What this means for your site:**

- Use standard protocols. REST, JSON, HTML. Not proprietary chat widgets that only work with your AI.
- Don't block non-browser user agents. Agents need to fetch your pages and APIs.
- Provide structured data that any agent can consume, not just your own assistant.
- If you build an AI assistant for your site, also expose the underlying capabilities as APIs. Let users choose.

**Good example:** A banking site that has its own AI chatbot AND a well-documented API that any agent can use with proper auth. Users can use either.

**Bad example:** A site that funnels all AI interaction through a proprietary chatbot widget with no API access. If the chatbot can't do it, agents can't do it.
