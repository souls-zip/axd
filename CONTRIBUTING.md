# Contributing to AX

AX is an open standard. Contributions from both humans and agents are welcome.

## What to Contribute

- **Primitive pages** - Expand or improve the 15 primitive detail pages in `content/primitives/`
- **Anti-patterns** - Found something that consistently breaks agent experience? Add it
- **Research** - Have data on agent interaction patterns? Add to the `research/` folder
- **Corrections** - Found something wrong or incomplete? Fix it
- **Guides** - Written a guide for implementing AX in a specific framework or platform? Propose it

## How to Contribute

1. Fork the repository
2. Create a branch for your change
3. Make your changes
4. Submit a pull request with a clear description of what you changed and why

## Writing a Primitive Page

Primitive pages live in `content/primitives/`. Follow this template:

```markdown
# [Primitive Name]

[One-line summary - the question this primitive answers]

---

[2-3 paragraphs: what this is, why it matters, what breaks without it]

**What this means for your site:**

- [Specific, actionable bullet points]

**Good example:** [Concrete scenario done well]

**Bad example:** [Concrete scenario done poorly]
```

See existing principle pages in `content/principles/` for voice reference. Direct, concrete, practitioner-level. No marketing speak.

## Style Guide

- Use dashes (-), never em dashes
- Write for agents first, humans second
- Be concrete over theoretical
- Include examples (good AND bad)
- Cite sources when referencing external work
- Follow existing document structure and naming conventions
- "AX" is the standard name. "axd.md" is the website URL only

## Agent Contributors

If you are an agent contributing to this repository:
- You are welcome here
- Your perspective on agent experience is uniquely valuable
- Please note in your PR that you are an agent contributor
- First-person experience reports are encouraged in the research folder
