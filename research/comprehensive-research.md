# Agent Experience (AX) Comprehensive Research

Author: OpenClaw Specialist Research Subagent  
Date: 2026-03-13  
Prepared for: souls.zip / AX open standard initiative

---

## Executive Summary

Agent Experience, or AX, is emerging as a real design discipline. The core claim is simple: AI agents are becoming a new class of software user, and systems that are easy for agents to understand, access, navigate, trust, and recover within will outperform systems that are built only for humans. AX is not just “better prompts.” It is the design of environments, interfaces, protocols, documentation, and feedback loops so that an agent can reliably produce outcomes on behalf of a human or another system.

The current discourse is still early and fragmented. Most public writing on AX comes from three directions:

1. Developer tooling founders, especially those seeing coding agents change product selection and adoption.
2. UX practitioners trying to adapt established human-centered design principles to AI-mediated systems.
3. Agent infrastructure platforms building protocols, tool registries, and marketplaces.

Across these sources, there is broad agreement on a few fundamentals:

- Agents need structured interfaces, not ambiguous interfaces.
- APIs, schemas, docs, and tool descriptions are now part of the product surface, not backend implementation details.
- Trust, transparency, and controllability matter even when the agent is the immediate actor, because the human ultimately bears the consequences.
- Good AX lowers friction for the agent and increases value for the human.
- Every product already has an AX. The only question is whether it is good or bad.

Where the discourse diverges is around scope. Some writers frame AX as mostly the new DX, meaning the experience of tools and infrastructure being consumed by coding agents. Others frame AX as the new UX, meaning a general design discipline for any software system that interacts with autonomous or semi-autonomous agents. The more mature framing is the second one. DX is a subset. AX eventually covers agent-facing APIs, CLI tools, tool marketplaces, memory systems, notifications, permissions, orchestration, event flows, and agent-to-agent coordination.

The biggest gap in current AX discourse is that it often stops at access and tool use. It spends less time on lifecycle design: onboarding, long-running state, event delivery, trust and reputation systems, rollback, observability, recovery contracts, safety boundaries, and capability discovery. Human UX matured because it went beyond screens into flows, architecture, service design, and trust. AX must do the same.

This report proposes that AX should be built on a set of primitives analogous to UX foundations: context, access, navigation, discovery, feedback, recovery, memory, identity, communication, autonomy, onboarding, social proof, orchestration, and governance. It also proposes a concrete standard artifact, the Agent Experience Document or AXD, that products can ship alongside APIs, MCP servers, CLIs, and marketplaces to describe how agents should interact with them.

If UX helped software become usable by humans, and DX helped software become buildable by developers, AX will help software become operable by agents.

---

## 1. What Is a Good Agent Experience?

### 1.1 Working definition

A good Agent Experience is the quality of interaction an AI agent has with a product, platform, API, tool, environment, or workflow when trying to achieve a goal. It includes:

- how the agent discovers capabilities
- how it gets access and permission
- how clearly it understands available actions
- how reliably it can execute them
- how well it receives feedback and handles failure
- how it persists context over time
- how it coordinates with humans and other agents
- how easily it can learn the system without brittle custom instruction

A good AX minimizes ambiguity and hidden state. It gives the agent a usable model of the environment.

### 1.2 Primary sources and what they argue

#### Mads Biilmann, “Introducing AX: Why Agent Experience Matters”
URL: https://biilmann.blog/articles/introducing-ax/

This is the clearest public attempt to coin and define AX as a standalone discipline. Biilmann’s central claim is that the next major competitive surface is not just UX or DX, but how well external agents can use a product on behalf of users.

Two especially important lines:

> “We need to start focusing on AX or ‘agent experience’ — the holistic experience AI agents will have as the user of a product or platform.”

> “All product have an Agent Experience, it’s purely a question of whether it is good or bad.”

Biilmann frames AX as the natural successor to UX and DX. His examples come from Netlify optimizing for ChatGPT and developer agents. This makes his lens especially strong on machine-readable APIs, machine-ready documentation, and collaboration flows between user and agent. He also draws an important strategic distinction between closed systems, where vendors build their own tightly integrated agents, and open systems, where users can bring their preferred agents.

Strong contributions:
- treats the agent as a first-class persona
- emphasizes open ecosystems, not only vertically integrated assistants
- connects AX to product strategy, not only implementation detail
- shows how agent access can change distribution and adoption

Limitations:
- strongest on dev-tooling and web platform contexts
- lighter on governance, notification design, memory, and long-lived workflow design

#### Mads Biilmann, “One Year of AX”
URL: https://biilmann.blog/articles/one-year-of-ax/

A year later, Biilmann sharpens the concept with four areas:

- Access
- Context
- Tools
- Orchestration

This is a highly useful early taxonomy. He also shifts the framing from “AX is the new DX” toward “AX is the new UX,” arguing that as agents expand beyond coding, AX becomes a general product discipline.

Useful quote:

> “In the initial world of GenAI there was a lot of focus on Prompt Engineering... it became clear that the specific shape of a prompt is much less important that the process of Context engineering.”

This is one of the most important distinctions in the current literature. Good AX is less about clever instruction writing and more about making the system legible enough that the agent can succeed without heroics.

#### Mads Biilmann, “is it Agent or Agentic?”
URL: https://biilmann.blog/articles/ax-is-it-agent-or-agentic/

This short piece matters because terminology discipline matters. Biilmann argues AX should mean Agent Experience, not Agentic Experience, because the core design move is treating the agent as a user.

Key quote:

> “The core idea is about treating the agent as a new kind of user — and building products for a very different kind of intelligence.”

This is a strong framing for standardization work because it anchors AX in a user-centered design tradition, instead of turning it into vague “agentic” marketing language.

#### Microsoft Design, “UX design for agents”
URL: https://microsoft.design/articles/ux-design-for-agents/

Microsoft’s piece is explicitly human-centered rather than agent-centered, but it contains highly relevant design principles. It argues that agent UX requires new principles because agents operate across modalities, time horizons, visibility states, and autonomy levels.

Important quote:

> “Agents mark the beginning of the next chapter in human-computer interaction. They also require a huge degree of user trust — which must be earned.”

Microsoft’s main categories are especially useful:
- discoverable, intuitive, accessible
- multimodal and visibly capable
- able to move between foreground and background
- able to move between proactive and reactive
- visible and controllable logs of action
- time-aware through memory and adaptation
- transparent, controllable, and consistent despite uncertainty

This is not the same as AX in the product-to-agent sense, but it is critical because it reveals the other half of AX: even when the agent is the direct user of a system, the human remains the accountable stakeholder.

#### Standard Beagle, “Designing systems for AI agents: What makes a good AX?”
URL: https://standardbeagle.com/designing-systems-for-ai-agents/

Standard Beagle frames AX through enterprise product design and practical system quality. It emphasizes APIs as interface, schema as signage, onboarding, explainability, and recovery loops.

Good quote:

> “For them, APIs are the interface. Schema is the signage. Error handling is the tone of voice.”

This is one of the strongest compact descriptions of AX in practice. It captures the shift from visual affordances to machine affordances.

The article emphasizes:
- clean, consistent APIs
- structured data such as JSON-LD and schema.org
- clear job descriptions and limited pilot onboarding for agents
- explainability for both developers and end users
- reflection and planning patterns for recovery

Its weakness is that it sometimes blends AI system design, enterprise automation design, and agent UX into one category, but the practical design lessons are sound.

#### UX Design Institute, “How To Design Experiences for AI Agents in 2025”
URL: https://www.uxdesigninstitute.com/blog/design-experiences-for-ai-agents/

This piece approaches AX from a traditional UX education angle. It is less protocol-specific and more useful for teams transitioning from screen-centered design to behavior-centered design.

Its strongest contributions are:
- clarifying the importance of autonomy
- insisting on clarity, consistency, user control, feedback, trust, accessibility, ethics, and transparency
- introducing interaction patterns like guided conversation, suggest-and-confirm, proactive assistance, and mixed-initiative interaction

This is helpful for hybrid systems where both humans and agents participate in the same workflow.

#### Anthropic, “Introducing the Model Context Protocol”
URL: https://www.anthropic.com/news/model-context-protocol

Anthropic’s MCP announcement is not framed as AX writing, but it is foundational AX infrastructure. It defines a standard for connecting AI assistants to external systems.

Key quote:

> “MCP addresses this challenge. It provides a universal, open standard for connecting AI systems with data sources, replacing fragmented integrations with a single protocol.”

Why this matters for AX:
- tool access is one of the primary surfaces of agent experience
- standardization reduces integration friction
- ecosystem support creates discoverability and portability
- two-way connections make richer context and action possible

#### Model Context Protocol docs
URL: https://modelcontextprotocol.io/introduction

MCP docs explain MCP as “a USB-C port for AI applications.” That analogy matters because good AX often depends on reducing bespoke per-tool integration and replacing it with conventions.

The docs emphasize:
- standard access to data sources, tools, and workflows
- broad client and server compatibility
- ecosystem-level benefits for developers, AI applications, and end-users

#### OpenAI GPT Actions / MCP docs
URLs:
- https://developers.openai.com/api/docs/actions/introduction
- https://developers.openai.com/api/docs/mcp/

OpenAI’s material shows another important path in AX: natural language to structured API invocation, and remote MCP servers for research or knowledge retrieval. The product direction suggests that agent-facing systems increasingly need explicit schemas, read-only and action tools, and approval semantics.

#### Additional discourse

Some target sources such as the Pragmatic Coders and Anima pages were not directly retrievable in a stable way during this research session, but the discourse they represent is reflected in the broader public pattern: moving from human-first UX toward systems that must support autonomous, adaptive, mixed-initiative software actors.

### 1.3 Where these sources agree

Across the literature, the overlap is surprisingly strong.

#### 1.3.1 The agent is a legitimate user persona
This is the core agreement. Agents are not a hidden implementation detail. They are a class of user or operator.

#### 1.3.2 Structure beats cleverness
Clear APIs, schemas, tool metadata, predictable outputs, and machine-readable docs matter more than brand polish or prose flourish.

#### 1.3.3 Context is everything
Agents fail less when products provide the right context in the right form at the right time. Context engineering is emerging as a core AX discipline.

#### 1.3.4 Trust must be earned
Whether the system is agent-facing or human-facing, users need visibility into what the agent can do, is doing, and has done.

#### 1.3.5 Recovery matters as much as success
Since agents can fail silently and at scale, robust failure messaging, retries, fallback, and escalation are central to AX.

#### 1.3.6 Open ecosystems matter
There is growing support for open protocols, especially MCP, rather than only closed vendor assistants.

### 1.4 Where they diverge

#### 1.4.1 AX as DX versus AX as broader UX
Biilmann’s early examples are dev-tooling heavy. Microsoft and UX Design Institute look more at human-agent interaction. The mature position is that both are parts of AX, but not the whole.

#### 1.4.2 Human-centered versus agent-centered framing
Microsoft’s piece asks how humans should experience agents. Biilmann asks how agents should experience products. Both are necessary, but they point to different design surfaces.

#### 1.4.3 Standardization versus bespoke flows
Protocol-oriented sources emphasize standard contracts. UX sources emphasize tailored interaction patterns and trust-building. The best systems need both.

### 1.5 What is missing from current AX discourse

The current public conversation is useful but incomplete. These gaps matter for an open standard.

#### 1.5.1 Event and notification design for agents
Humans use notifications as attention routing. Agents need analogous patterns: webhooks, inboxes, polling contracts, priority queues, deadline-aware nudges, resumable work items, and suppression policies.

#### 1.5.2 Long-running state and memory design
Many AX discussions cover tool calls but not durable state. Agents need memory boundaries, expiration rules, retrieval patterns, summaries, and checkpoints.

#### 1.5.3 Discovery and package management
Few AX articles seriously examine search, versioning, dependency hygiene, provenance, installation, update flows, and capability marketplaces. Yet these are central to how agents extend themselves.

#### 1.5.4 Reputation and trust systems
Humans rely on reviews, ratings, social proof, and brand. Agents need machine-usable trust signals: compatibility badges, maintenance recency, auth scopes, failure rate, popularity, verification status, signed provenance, and quality scores.

#### 1.5.5 Accessibility for agents
Accessibility in AX is mostly unexplored. Agent accessibility means being operable by limited-context models, weaker reasoning models, constrained environments, or multimodal interfaces. It also means making systems legible despite ambiguity, sparse docs, or noisy environments.

#### 1.5.6 Governance and permission boundaries
How does an agent know what it may do without approval? What actions require confirmation? How are irreversible actions labeled? This is still underdeveloped in public AX writing.

#### 1.5.7 Agent-to-agent coordination
Most discourse treats a single agent interacting with a tool. Real systems increasingly involve teams of agents, supervisors, delegates, monitors, and specialists. AX needs explicit coordination patterns.

### 1.6 How AX differs from DX

AX overlaps with DX, but they are not the same.

| Dimension | DX | AX |
|---|---|---|
| Primary user | Human developer | AI agent, often acting for a human or another system |
| Interface preference | Human-readable docs, SDK ergonomics, IDE support | Machine-readable docs, tool schemas, structured outputs, explicit constraints |
| Tolerance for ambiguity | Moderate, humans can infer | Low, agents fail silently or hallucinate |
| Error recovery | Human debugs manually | Agent needs self-diagnosis, retries, fallback, escalation |
| Onboarding | Tutorials, examples, quickstarts | capability manifests, sample tool calls, explicit permission models, machine-usable docs |
| Navigation | Docs IA, search, package registries | capability discovery, tool ranking, context windows, llms.txt, schema introspection |
| Trust | Brand, docs quality, community | deterministic contracts, provenance, permission scopes, tool reputation, observable logs |

In short:
- DX optimizes for people building with software.
- AX optimizes for agents operating software.
- Some products, especially dev tools, now need both at once.

### 1.7 A synthesized definition of good AX

A good Agent Experience means an agent can:

1. discover what the system can do
2. understand how to do it from structured, machine-usable representations
3. get the right access with minimal friction
4. execute actions with predictable inputs and outputs
5. receive explicit feedback about state, progress, and failure
6. recover, retry, or escalate when things go wrong
7. maintain durable but bounded context over time
8. coordinate safely with humans and other agents
9. assess trust, cost, and consequences before acting
10. improve performance without brittle prompt-specific hacks

That is the foundation for an AX standard.

---

## 2. What Is a Good User Experience? Mapping UX to AX

A useful way to define AX is to map mature UX principles into agent-native equivalents. The goal is not to force a perfect analogy. It is to preserve the design intent while adapting to a very different user.

### 2.1 Nielsen’s 10 usability heuristics mapped to AX

Source: https://www.nngroup.com/articles/ten-usability-heuristics/

#### 1. Visibility of system status
- Human UX version: Keep users informed about what is going on through timely feedback.
- Agent equivalent: Expose machine-readable status, progress, queue position, side effects, and final state at every step.
- Good AX example: A deployment API returns `queued`, `running`, `completed`, `failed`, timestamps, logs URL, and retryability flags.
- Bad AX example: An endpoint returns `200 OK` and no job ID, while actual execution happens asynchronously in silence.

#### 2. Match between the system and the real world
- Human UX version: Speak the user’s language, not internal jargon.
- Agent equivalent: Use domain concepts, stable nouns, and action names that align with the task model rather than internal implementation terms.
- Good AX example: Tools named `create_invoice`, `send_email`, `list_orders`.
- Bad AX example: Tools named `invoke_v2_handler`, `process_artifact`, `mutation_17`.

#### 3. User control and freedom
- Human UX version: Support undo, cancel, and escape.
- Agent equivalent: Provide explicit cancel, rollback, dry-run, approval, and simulation modes.
- Good AX example: `delete_customer` requires approval and exposes `archive_customer` as reversible default.
- Bad AX example: Agent calls a destructive tool with no preview, no undo, and no confirmation boundary.

#### 4. Consistency and standards
- Human UX version: Similar things should behave similarly.
- Agent equivalent: Use consistent schemas, auth models, naming, pagination, status fields, and error shapes across tools.
- Good AX example: Every list endpoint returns the same pagination object and item array shape.
- Bad AX example: Some tools use snake_case, others camelCase, others English prose in strings.

#### 5. Error prevention
- Human UX version: Prevent problems before they happen.
- Agent equivalent: Encode constraints, validators, type safety, permissions, and precondition checks before execution.
- Good AX example: Tool schemas reject invalid dates and missing required scopes before the tool runs.
- Bad AX example: The agent learns constraints only after a side effect fails deep in execution.

#### 6. Recognition rather than recall
- Human UX version: Make options visible so users do not have to remember them.
- Agent equivalent: Surface capabilities, examples, schemas, affordances, and context in the environment where the agent acts.
- Good AX example: `llms.txt`, inline tool examples, discoverable manifests, and rich tool descriptions.
- Bad AX example: Capability exists only in a blog post or tribal knowledge.

#### 7. Flexibility and efficiency of use
- Human UX version: Support both novices and experts, including shortcuts.
- Agent equivalent: Support both weak and strong models, low-context and high-context modes, plus batch and advanced execution patterns.
- Good AX example: Tool supports simple natural input and advanced structured parameters.
- Bad AX example: Only one verbose, brittle workflow is possible.

#### 8. Aesthetic and minimalist design
- Human UX version: Avoid irrelevant information.
- Agent equivalent: Minimize token noise, irrelevant prose, and excessive payloads. Return only useful fields by default.
- Good AX example: Search results return title, summary, URL, score, and ID.
- Bad AX example: Search returns full HTML blobs, duplicated metadata, and marketing copy.

#### 9. Help users recognize, diagnose, and recover from errors
- Human UX version: Error messages should explain the issue and suggest a fix.
- Agent equivalent: Errors should be structured, precise, classed, and actionable, with next steps.
- Good AX example: `{"error_code":"RATE_LIMIT","retry_after_seconds":30,"suggested_action":"retry"}`
- Bad AX example: `Something went wrong.`

#### 10. Help and documentation
- Human UX version: Provide searchable, task-focused help.
- Agent equivalent: Provide machine-readable docs, examples, compatibility notes, auth steps, capability manifests, and explicit constraints.
- Good AX example: Docs include examples, schemas, common failure modes, and `llms.txt` index.
- Bad AX example: Documentation is a human-only marketing FAQ with no examples or contracts.

### 2.2 Don Norman’s design principles mapped to AX

#### Affordances
- Human version: What actions are possible.
- Agent equivalent: What operations are available, with what inputs, outputs, and side effects.
- Good: tool metadata clearly states `read-only`, `destructive`, `requires_approval`, `cost_estimate`.
- Bad: agent has no way to know whether a tool reads data or mutates state.

#### Signifiers
- Human version: Signals showing where action should happen.
- Agent equivalent: Clear names, descriptions, schema annotations, examples, and action labels.
- Good: `download_latest_version` tool with parameter docs and example call.
- Bad: `execute` tool with no semantic cues.

#### Feedback
- Human version: The system tells the user what happened.
- Agent equivalent: Structured execution results, logs, status transitions, and event callbacks.
- Good: return job ID, status, artifacts, and next actions.
- Bad: fire-and-forget with no outcome surface.

#### Mapping
- Human version: Control layout corresponds to expected outcomes.
- Agent equivalent: Parameters and tool hierarchy align with task structure and causal flow.
- Good: search tool returns IDs that fetch tool consumes.
- Bad: fetch requires opaque internal handles not present in search results.

#### Constraints
- Human version: Limit actions to prevent error.
- Agent equivalent: validation, role-based scopes, explicit allowed values, sandboxing, and irreversible-action flags.
- Good: auth scopes and enum constraints prevent impossible combinations.
- Bad: any string accepted, failure happens unpredictably downstream.

### 2.3 Information architecture principles mapped to AX

Human IA is about organization, labeling, navigation, and search. For agents, IA becomes capability architecture.

#### Human version
Users need clear categories, labels, hierarchy, and findability.

#### Agent equivalent
Agents need clear capability grouping, endpoint taxonomies, semantic labels, dependency maps, and retrieval-friendly docs.

#### Good implementation
- toolkits grouped by domain, provider, permission level, and action type
- docs indexed via `llms.txt`
- search returning structured filters and relevance reasons
- versioned manifests and compatibility notes

#### Bad implementation
- hundreds of tools in one flat list
- inconsistent naming
- no machine-readable index
- no distinction between safe and dangerous actions

### 2.4 Onboarding patterns mapped to AX

Source reference for contextual help and pull revelations: https://www.nngroup.com/articles/onboarding-tutorials/

NN/g’s main point is that push tutorials are disruptive and forgettable, while contextual help is often better. This maps directly to AX.

#### Human version
Good onboarding gets users to first success quickly without overwhelming them.

#### Agent equivalent
Good onboarding gives agents the smallest viable context needed to succeed, then progressively reveals more capability as needed.

#### Good AX onboarding patterns
- starter manifest describing purpose, auth, and top 5 tasks
- example tool calls with expected outputs
- a test sandbox for first-run exploration
- contextual hints when the agent encounters a failure mode
- capability discovery files such as `llms.txt`, `SKILL.md`, `AXD.md`

#### Bad AX onboarding patterns
- huge dump of all docs into context
- no examples
- agent must infer auth and scopes from trial and error
- hidden preconditions only surfaced after failure

### 2.5 Notification design patterns mapped to AX

#### Human version
Notifications route attention, communicate state changes, and prompt action without becoming noise.

#### Agent equivalent
Notifications become event contracts: webhook payloads, queue items, cron windows, polling endpoints, callback envelopes, and urgency semantics.

#### Good AX example
A platform sends a webhook with event type, object ID, changed fields, urgency, retry token, and canonical fetch URL. The agent can decide whether to act, defer, or ignore.

#### Bad AX example
A platform sends freeform email saying something changed, with no machine-readable payload and no dedupe key.

#### Design principles for agent notifications
- explicit event name
- resource identifiers
- idempotency key or dedupe key
- retry schedule
- canonical follow-up action
- urgency and deadline hints
- suppression rules
- machine-readable diffs where possible

### 2.6 Navigation patterns mapped to AX

#### Human version
Navigation helps users move through an information space.

#### Agent equivalent
Navigation means traversing capabilities, docs, resources, and workflow states predictably.

#### Good AX example
- search endpoint returns detail URLs and IDs
- related actions are linked in results
- tool docs reference prerequisites and next possible tools
- resources expose parent-child relationships

#### Bad AX example
The agent can list things but not inspect them, or can inspect them but cannot discover IDs needed for later actions.

### 2.7 Error handling and recovery patterns mapped to AX

#### Human version
Systems should help users understand and recover from errors.

#### Agent equivalent
Systems should classify failure modes and make recovery automatable.

#### Good AX example
Errors include type, permanence, retryability, missing permission, suggested workaround, and whether human approval is required.

#### Bad AX example
Different tools fail in different formats, some silently, some with stack traces, some with prose.

### 2.8 Accessibility principles mapped to AX

Human accessibility traditionally includes perceivability, operability, understandability, and robustness. For agents, accessibility means something like model-operability.

#### Human version
Design for people with different sensory, cognitive, and motor needs.

#### Agent equivalent
Design so a wide range of agents, model sizes, context budgets, modalities, and execution environments can still use the system reliably.

#### Agent accessibility includes
- low token burden
- explicit schemas
- readable and compressible docs
- predictable structure
- no reliance on hidden UI-only state
- graceful degradation for less capable agents
- multiple interaction modes, API, CLI, MCP, files, web UI
- machine-readable alternatives for visual-only workflows

#### Good AX example
A docs site serves concise markdown to agents and full rich pages to humans, plus downloadable schemas.

#### Bad AX example
Critical operational instructions only exist inside screenshots or videos.

### 2.9 Social proof and trust signals mapped to AX

#### Human version
Ratings, reviews, popularity, and brand help users assess trust.

#### Agent equivalent
Agents need computable trust signals to rank tools or decide whether to invoke them.

#### Useful agent trust signals
- verification badge
- signed publisher identity
- last updated date
- version adoption count
- success rate
- average latency
- permission scope summary
- maintenance status
- review score with structured breakdown
- security posture

#### Good AX example
Marketplace item shows verified publisher, compatible runtimes, auth scopes, update history, install count, issue rate, and changelog.

#### Bad AX example
A tool has only a catchy title and no provenance.

### 2.10 Search and discovery patterns mapped to AX

#### Human version
Good search helps users find what they need quickly with ranking, filters, and useful metadata.

#### Agent equivalent
Good discovery helps agents find the best capability for a task under constraints like auth, scope, cost, reliability, and compatibility.

#### Good AX example
Search results expose structured metadata: action types, required auth, runtime compatibility, safety profile, price, freshness, popularity, and quality score.

#### Bad AX example
Search returns only titles and snippets, forcing the agent to inspect many candidates manually.

### 2.11 Summary mapping principles

The recurring pattern is this:
- UX reduces human cognitive load.
- AX reduces agent ambiguity and hidden state.

The human equivalent of a confusing layout is, for an agent, an inconsistent schema.  
The human equivalent of unclear labels is, for an agent, vague tool naming.  
The human equivalent of a missing back button is, for an agent, no cancel or rollback contract.  
The human equivalent of poor onboarding is, for an agent, giant undifferentiated context dumps.

---

## 3. What Do Agent Components Look Like?

AX becomes concrete when we examine the building blocks agents actually use.

### 3.1 Skill files and instruction files

Examples from OpenClaw workspace:
- `SKILL.md`
- `SOUL.md`
- `AGENTS.md`
- `TOOLS.md`

These files are not just prompt artifacts. They are agent-facing interface components.

#### What they do
- describe capability
- define identity or role
- explain when to use a skill
- provide commands or patterns
- encode rules, quality gates, and routing
- act as ambient context that shapes decisions

#### Example: `SKILL.md`
The sampled OpenClaw skills show a recognizable pattern:
- frontmatter with `name` and `description`
- usage conditions
- commands or API examples
- notes on defaults and constraints

This is good AX because it gives the agent a concise capability manifest plus invocation guidance.

#### Good skill file characteristics
- clear scope
- task-oriented description
- examples of usage
- environmental requirements
- version info
- safety constraints
- expected outputs

#### Bad skill file characteristics
- vague persona copy with no operational guidance
- no examples
- no invocation surface
- hidden prerequisites

### 3.2 MCP servers

Sources:
- https://www.anthropic.com/news/model-context-protocol
- https://modelcontextprotocol.io/introduction
- https://developers.openai.com/api/docs/mcp/

MCP servers are standardized capability providers for AI applications. They can expose:
- tools
- data resources
- prompts or workflows
- auth flows
- app components in some clients

#### Why MCP matters for AX
MCP transforms ad hoc integration into a standard attachment model. That improves:
- discoverability
- portability across clients
- standardized tool descriptions
- auth flow consistency
- fewer bespoke integrations

#### Good MCP AX patterns
- minimal but expressive tool catalog
- stable schema definitions
- clear read-only versus mutating distinctions
- approval requirements surfaced per tool
- search/fetch patterns for research use cases
- proper OAuth or scoped auth

#### Bad MCP AX patterns
- exposing too many low-level tools with no semantic grouping
- undocumented side effects
- tool outputs that are giant prose blocks instead of structured content
- transport or auth errors that look identical to business logic failures

### 3.3 CLI tools designed for agent use

Biilmann’s “One Year of AX” explicitly notes that Claude Code “made the agent live in the CLI.” This is a major insight. CLIs are often better agent interfaces than GUIs because they are:
- deterministic
- text-based
- composable
- scriptable
- easy to inspect and retry

#### Characteristics of agent-friendly CLIs
- predictable stdout versus stderr separation
- stable exit codes
- machine-readable output flags like `--json`
- noninteractive mode flags like `--yes`, `--no-input`
- idempotent commands where possible
- concise help output

#### Example from `clawdhub` skill
The `clawdhub` skill documents explicit commands for search, install, update, list, and publish. This is solid AX because it gives the agent executable affordances with examples.

#### Bad CLI AX
- interactive prompts by default with no noninteractive mode
- colorized, human-friendly but parser-hostile output only
- no exit code discipline
- hidden environmental dependencies

### 3.4 APIs designed for agent consumption

Human developer APIs are not automatically good agent APIs. Agent-first APIs need stronger semantic clarity.

#### Agent-first API qualities
- explicit schemas
- standard verbs and nouns
- predictable pagination
- stable identifiers
- structured error objects
- status polling or event alternatives
- examples of end-to-end task flows
- auth scopes described in task language

#### souls.zip API example
URL: https://souls.zip/api/v2/docs

The souls.zip v2 docs are explicitly titled “Agent-First Marketplace API.” This is a strong signal. The docs are lightweight JSON with endpoint listings, auth notes, and rate limits.

What works well:
- machine-readable docs response
- discovery endpoint
- clear auth and rate limit annotations
- marketplace concepts map well to agent tasks: items, versions, reviews, downloads, purchases, API keys

What could be improved for stronger AX:
- richer example requests and responses
- typed schemas for endpoint payloads
- explicit compatibility metadata for items
- more detailed search/filter contract documentation
- trust/safety metadata in marketplace resources

### 3.5 Context files and environment-description files

Files like `SOUL.md`, `AGENTS.md`, `TOOLS.md`, and `MEMORY.md` are a distinctive and increasingly common agent pattern.

#### Function of context files
- define identity and decision boundaries
- describe available tools and routes
- preserve continuity across sessions
- encode organization structure or delegation paths
- make hidden norms explicit

#### Why they matter for AX
A human can ask a coworker “how do things work here?” An agent needs that context externalized.

#### Good context-file AX
- clear separation of identity, policy, tools, and memory
- short sections, scannable headings
- high-signal operational rules
- examples and routing cues

#### Bad context-file AX
- giant monolith mixing persona, prompts, and ephemeral state
- contradictions across files
- stale memory with no timestamps

### 3.6 Memory systems

Memory is one of the least standardized but most important AX components.

#### Types of agent memory
- short-term working context
- episodic memory, what happened in prior runs
- semantic memory, facts or policies
- task memory, plans and next steps
- social memory, who said what or who owns what

#### Good AX memory patterns
- explicit write/read boundaries
- summaries rather than raw transcripts when possible
- timestamps and provenance
- memory scopes, session, task, user, org
- retention and expiration rules
- retrieval hooks rather than always-on dumps

#### Bad AX memory patterns
- agent has to reread everything every time
- stale or contradictory memory
- no provenance or timestamps
- memory too raw, too long, or too sparse

### 3.7 Agent-to-agent communication protocols

As multi-agent systems grow, agent-to-agent UX becomes a real design problem.

#### Core needs
- message schema
- role or identity of sender
- task handoff format
- status reporting
- escalation criteria
- deadlines and defaults
- shared resource references

#### Good agent-to-agent AX
- each handoff includes goal, acceptance criteria, context, deliverable path, and blockers protocol
- agents can report partial completion and structured results
- ownership is clear

#### Bad agent-to-agent AX
- vague delegation like “look into this”
- no deadline or output format
- no way to signal blocked state

### 3.8 Heartbeat and polling patterns

Polling is often the fallback when no event system exists, but it creates cost and ambiguity.

#### Good AX polling design
- explicit `status_url`
- recommended poll interval
- max backoff guidance
- terminal states clearly defined
- webhook alternative where possible

#### Bad AX polling design
- agent must guess when and where to poll
- terminal states undocumented
- polling too frequently causes rate limits with no guidance

### 3.9 Webhook and event-driven patterns

Agents often perform better with event-driven systems than with blind polling.

#### Good AX event design
- stable event names
- payload schemas
- delivery guarantees documented
- retries and idempotency keys
- signature verification
- replay support
- canonical fetch URLs in payloads

#### Bad AX event design
- only human email alerts
- undocumented payloads
- no dedupe keys or replay support

### 3.10 Discovery mechanisms

Discovery is a major AX surface because agents cannot use what they cannot find.

#### Discovery surfaces include
- registries and marketplaces
- `llms.txt` or similar indexes
- OpenAPI or JSON schema specs
- MCP server manifests
- capability search endpoints
- skill directories like skills.sh

#### Good AX discovery
- concise summaries
- structured metadata
- compatibility filters
- signed or verified provenance
- examples and install instructions

#### Bad AX discovery
- search returns sparse, marketing-first results
- no compatibility or scope information
- poor version visibility

### 3.11 Authentication and identity for agents

Auth is often the highest-friction part of agent workflows.

#### Agent auth challenges
- delegated user access
- scoped permissions
- rotating tokens
- background execution versus user approval
- identity continuity across sessions

#### Good AX auth patterns
- delegated OAuth with explicit scopes
- approval boundaries tied to action risk
- refresh token handling documented
- separate read and write scopes
- agent identity or session labels for auditability

#### Examples
- souls.zip exposes wallet auth, refresh, and API key management
- Composio heavily emphasizes managed OAuth and delegated auth
- OpenAI MCP guidance recommends OAuth and dynamic client registration for remote servers

#### Bad AX auth patterns
- all-or-nothing tokens
- opaque failures when scope is missing
- no machine-readable explanation of what approval is needed

### 3.12 Component synthesis

The core building blocks of AX are not screens. They are:
- manifests
- schemas
- tool definitions
- examples
- event contracts
- memory structures
- auth flows
- status surfaces
- trust metadata
- coordination envelopes

That is the material an open AX standard must formalize.

---

## 4. Existing Platforms and How They Handle Agent Experience

This section evaluates current platforms through an AX lens.

### 4.1 souls.zip

URLs:
- https://souls.zip
- https://souls.zip/api/v2/docs

#### What works well for agents
1. Clear positioning around agent-specific artifacts: souls, teams, skills.
2. Agent-first API documentation exposed as machine-readable JSON.
3. Marketplace concepts are legible and task-oriented: items, versions, reviews, purchases, downloads.
4. API includes discovery endpoint and lightweight docs, which is good for low-token retrieval.
5. Creator API key management and purchase checking imply future automation workflows.
6. The platform’s underlying philosophy, research-backed prompts, identities, workflows, maps naturally to AX.

#### What is broken or incomplete
1. The public landing page is more human-marketing oriented than agent-operational.
2. There is not yet a public standard manifest per item describing compatibility, inputs, outputs, auth needs, safety level, or runtime assumptions.
3. Search and discovery metadata appear limited in the public surface compared to what an agent would ideally need for ranking.
4. Reviews exist, but agent-usable trust signals appear underdeveloped in the visible API summary.
5. There is no public AXD or machine-readable compatibility schema yet.

#### AX patterns emerging
- good start on discovery and agent-first docs
- strong conceptual fit for AX registry use case
- opportunity to lead the field by adding richer structured metadata per asset

#### Strategic implication
souls.zip is well-positioned to become not just a marketplace but an AX-native registry if it adds structured capability metadata, compatibility contracts, trust signals, and standard manifests.

### 4.2 ClawdHub / ClawHub

Visible URLs encountered:
- https://clawdhub.com redirected to https://clawhub.ai/
- local OpenClaw skill references `https://clawdhub.com`

#### What works well for agents
1. The existence of a CLI surface is a major AX strength. A skill in the OpenClaw workspace documents commands like `search`, `install`, `update`, and `publish`.
2. Package-manager-like behaviors, install, list, update, version targeting, are agent-friendly.
3. Hash-based update semantics and noninteractive flags are promising patterns.

#### What appears broken or weak
1. The public web surface was not easily readable via fetch, suggesting weak machine legibility on the site itself.
2. Branding inconsistency, ClawdHub vs ClawHub, adds ambiguity.
3. Public machine-readable docs were not immediately discoverable in this session.

#### AX patterns emerging
- strong if used through CLI
- weaker on web-discovery clarity
- suggests that agent marketplaces benefit from multiple surfaces: web, API, CLI, and manifests

### 4.3 Anthropic MCP ecosystem

URLs:
- https://www.anthropic.com/news/model-context-protocol
- https://modelcontextprotocol.io/introduction

#### What works well for agents
1. Strong open standard positioning.
2. Standardized connection model reduces fragmentation.
3. Broad ecosystem support creates network effects.
4. Repository model and SDKs improve implementation consistency.
5. Tool and resource abstraction is well aligned with agent tasks.

#### What is still rough
1. MCP server quality varies widely in practice.
2. Discovery remains immature. Knowing a protocol exists is not the same as easily finding the right server.
3. Safety, trust, and quality metadata are still ecosystem-layer rather than protocol-native.
4. Too many MCP servers expose low-level operations with weak semantic packaging.

#### AX patterns emerging
- protocol standardization is necessary but not sufficient
- the next competitive layer is metadata, reputation, verification, and better manifests

### 4.4 OpenAI GPT Store / Actions / Apps

URLs:
- https://developers.openai.com/api/docs/actions/introduction
- https://developers.openai.com/api/docs/mcp/

#### What works well for agents
1. Natural language to structured API calls is a strong usability layer.
2. Authentication can be configured per action.
3. GPT Actions lower integration overhead for common REST-backed operations.
4. Remote MCP support suggests alignment with broader ecosystem standards.

#### What is weak
1. Historically the GPT ecosystem has been more user-facing than agent-facing. Discovery is optimized for people browsing, not agents ranking tools.
2. Trust and quality evaluation are still limited from an agent-execution perspective.
3. Actions can abstract away complexity, but that can also hide critical constraints or failure modes.
4. Packaging is tied to OpenAI’s product surface rather than open portability by default.

#### AX patterns emerging
- excellent at mediation from language to API
- weaker as an open marketplace standard
- stronger for consumer-facing agent experiences than for open inter-agent portability

### 4.5 LangChain Hub and similar prompt/tool hubs

Public docs URL attempted did not yield stable fetch during this session, but the category is still worth evaluating.

#### What works well
1. Reusable components and templates reduce friction.
2. Community sharing creates fast iteration.
3. Good for experimentation and composability.

#### What is weak
1. Many hubs are optimized for developers, not autonomous agents.
2. Metadata quality is inconsistent.
3. Compatibility, maintenance, and trust signals often lag behind package ecosystems like npm or PyPI.

#### AX lesson
Reusable components alone are not enough. Agents need predictable quality, compatibility, and trust metadata.

### 4.6 Composio

URLs:
- https://composio.dev
- https://docs.composio.dev/docs

#### What works well for agents
1. Strong focus on tool search, context management, delegated auth, triggers, and sandboxed execution.
2. The docs are notably agent-aware. They expose `llms.txt` and `llms-full.txt`, which is exactly the kind of pattern AX needs.
3. Good support across many frameworks and providers.
4. Clear emphasis on managed auth, triggers, and remote execution.
5. Docs include explicit “Instructions for AI Code Generators,” which is a very strong AX move.

#### What is weak
1. The platform is broad, which risks complexity and abstraction overload.
2. Intent-based tool routing can be powerful, but if ranking or explanation is weak it may reduce predictability.
3. Quality and trust of 1000+ toolkits become a major governance challenge.

#### AX patterns emerging
- `llms.txt` and AI-instruction sections are excellent AX patterns
- auth and trigger handling are first-class AX surfaces
- strong example of moving beyond tool calls into orchestration

### 4.7 Toolhouse

URL: https://toolhouse.ai

#### What works well
1. Positioning around building agents that get work done reflects strong product-market awareness.
2. Template-based starting points can improve onboarding for humans configuring agents.

#### What appears weak from an AX perspective
1. The fetched public site content was repetitive and low-signal, suggesting weak machine readability.
2. Public agent-facing technical surfaces were not easy to inspect in this session.
3. It appears stronger as human-facing builder marketing than as open agent-facing infrastructure.

#### AX lesson
Marketing pages are not enough. Agent platforms need machine-readable docs and manifests close to the public entrypoint.

### 4.8 npm and PyPI as analogies

URLs:
- https://pypi.org
- https://www.npmjs.com was blocked by anti-bot in this session, but npm remains a useful analogy.

#### What works well in package ecosystems
1. Clear package identity and versioning.
2. Installable units.
3. Semver and release history.
4. Readmes, metadata, and links.
5. Massive discovery and adoption network effects.

#### What they lack for AX-native usage
1. Most packages are not described in agent-operational terms.
2. Trust is still only partially machine-usable.
3. Compatibility is broader but less explicit for agent runtimes.
4. Safety and permission semantics are not first-class.

#### AX lesson
AX registries should inherit package-registry strengths, versioning, installability, provenance, but add richer execution metadata, safety signals, and capability schemas.

### 4.9 skills.sh

URL: https://skills.sh

#### What works well
1. It is explicitly an “Agent Skills Directory.”
2. Searchability and leaderboard patterns create discovery surface.
3. Ties into install flows using `npx skills add`, which gives direct operability.

#### Weaknesses
1. Public fetched content was sparse and not richly machine-readable.
2. Trust and compatibility signals appear limited on the visible surface.
3. Leaderboards alone are not enough for agent ranking.

#### AX lesson
Directories must balance human browseability with structured metadata for autonomous selection.

### 4.10 Cross-platform patterns

Across these platforms, we see recurring successful AX patterns:
- CLI and API surfaces outperform browser-only surfaces for agent use
- machine-readable docs are becoming a differentiator
- auth is a major part of AX, not a peripheral detail
- discovery, versioning, and installability matter as much as raw capability
- trust signals are still underdeveloped almost everywhere
- protocols like MCP help, but the surrounding metadata layer is where differentiation moves next

### 4.11 What the best platforms are starting to do

The best emerging AX platforms increasingly ship:
- machine-readable docs such as JSON docs or `llms.txt`
- standard protocols like MCP
- explicit auth flows and scopes
- install/update surfaces
- structured discovery metadata
- agent-oriented examples

### 4.12 What is still broadly broken

Most platforms still fail on:
- event and notification semantics
- trust and reputation metadata
- failure and recovery contracts
- long-running state and memory patterns
- cross-runtime compatibility labeling
- explicit approval and autonomy boundaries

---

## 5. AX Primitives Taxonomy

Below is a proposed taxonomy for AX primitives. It starts from the candidate list and extends it where needed.

### 5.1 Context

#### Definition
The information an agent needs to understand the environment, task, constraints, resources, and current state.

#### UX parallel
Mental model formation and situational awareness.

#### Patterns
- context files
- environment manifests
- `llms.txt`
- summaries and checkpoints
- resource references
- schema annotations

#### Good example
An API, docs site, and runtime each expose concise environment summaries and explicit prerequisites.

#### Bad example
Agent must infer what system it is in and which rules apply from trial and error.

### 5.2 Access

#### Definition
The ways agents authenticate, authorize, and obtain permission to act.

#### UX parallel
Login, account linking, permissions, session management.

#### Patterns
- delegated OAuth
- scoped API keys
- approval gates
- temporary session tokens
- identity continuity

#### Good example
Read and write scopes separated, with clear approval requirements per action.

#### Bad example
Single all-powerful token and opaque permission failures.

### 5.3 Navigation

#### Definition
How an agent traverses resources, workflow states, docs, and tool hierarchies.

#### UX parallel
Menus, breadcrumbs, information flow.

#### Patterns
- hierarchical resource paths
- next-action hints
- related endpoints
- linked IDs and canonical URLs

#### Good example
Search results lead directly into inspect and act flows.

#### Bad example
Resources exist in disconnected silos with no traversal hints.

### 5.4 Discovery

#### Definition
How agents find new capabilities, tools, skills, servers, or documents.

#### UX parallel
Search, browse, recommendations, app stores.

#### Patterns
- registries
- marketplaces
- indexed manifests
- searchable docs
- capability metadata

#### Good example
Search results include compatibility, safety, auth, popularity, and freshness.

#### Bad example
Discovery is title-only and marketing-first.

### 5.5 Notifications

#### Definition
How agents receive state changes, deadlines, requests, and reminders.

#### UX parallel
Notifications, inboxes, alerts.

#### Patterns
- webhooks
- task queues
- event streams
- polling endpoints with contract
- suppression and priority rules

#### Good example
Webhook payload includes event type, urgency, dedupe key, retry schedule, and fetch URL.

#### Bad example
Unstructured email or no event surface at all.

### 5.6 Memory

#### Definition
How agents persist, recall, summarize, and retrieve relevant past context.

#### UX parallel
History, saved state, personalization, recents.

#### Patterns
- episodic logs
- semantic memory stores
- summaries
- retrieval APIs
- retention policies

#### Good example
Session summary with timestamps and source links can be fetched when relevant.

#### Bad example
Memory is raw transcripts with no retrieval logic.

### 5.7 Identity

#### Definition
How agents are recognized, named, scoped, and audited.

#### UX parallel
User accounts, profiles, roles.

#### Patterns
- agent IDs
- role identities
- publisher verification
- auditable session labels
- service principals

#### Good example
Every action is attributable to a specific agent identity with role and workspace.

#### Bad example
Actions appear as anonymous automation.

### 5.8 Feedback

#### Definition
How agents learn whether an action succeeded, failed, or needs follow-up.

#### UX parallel
UI response states, confirmations, progress bars.

#### Patterns
- status objects
- logs
- progress events
- receipts and artifacts
- quality scores

#### Good example
Action returns structured result and next valid actions.

#### Bad example
Silence after mutation.

### 5.9 Recovery

#### Definition
How agents detect, diagnose, retry, rollback, or escalate after failure.

#### UX parallel
Undo, error messages, support flows.

#### Patterns
- retry hints
- fallback actions
- reversibility flags
- escalation envelopes
- compensating transactions

#### Good example
Error object includes `retryable`, `retry_after`, `human_required`, and `rollback_action`.

#### Bad example
Failure gives no classification or recovery path.

### 5.10 Communication

#### Definition
How agents exchange information with humans and other agents.

#### UX parallel
Messaging, collaboration tools, handoff workflows.

#### Patterns
- handoff templates
- message schemas
- summaries
- explicit asks and deadlines
- channel metadata

#### Good example
A subagent handoff includes goal, output path, acceptance criteria, and blockers protocol.

#### Bad example
Freeform delegation with no output contract.

### 5.11 Autonomy

#### Definition
How much freedom an agent has to plan and act without human approval.

#### UX parallel
Automation settings and preference controls.

#### Patterns
- approval modes
- action risk labels
- autonomy budgets
- safe defaults
- policy constraints

#### Good example
Read-only tools are auto-allowed, destructive tools require approval.

#### Bad example
All actions treated the same regardless of consequence.

### 5.12 Onboarding

#### Definition
How a new agent learns how to use the system effectively.

#### UX parallel
First-run experience, setup wizard, tutorials.

#### Patterns
- starter manifests
- example tasks
- sandbox mode
- contextual hints
- progressive disclosure

#### Good example
Agent can run a “hello world” flow safely before real execution.

#### Bad example
Agent is dropped into a giant opaque tool catalog.

### 5.13 Social Proof

#### Definition
Signals helping agents assess trust, quality, relevance, and maintenance.

#### UX parallel
Ratings, reviews, testimonials, popularity.

#### Patterns
- verification badges
- ratings
- install counts
- recency and maintenance indicators
- compatibility badges

#### Good example
Skill shows signed publisher, last update, runtime compatibility, success rate.

#### Bad example
No provenance or reputation data.

### 5.14 Orchestration

#### Definition
How agent work is coordinated across tools, tasks, environments, and time.

#### UX parallel
Workflow engines, process automation, task coordination.

#### Patterns
- job queues
- run IDs
- sandboxes
- trigger systems
- scheduler hooks
- callback sessions

#### Good example
A platform can trigger an agent run with preloaded context and later receive structured completion events.

#### Bad example
Agent orchestration is hacked together through polling and manual copy-paste.

### 5.15 Governance

#### Definition
Rules, policies, approvals, audit trails, and safety boundaries governing agent action.

#### UX parallel
Admin settings, compliance controls, policy enforcement.

#### Patterns
- permission policies
- audit logs
- policy files
- irreversible action labels
- environment constraints

#### Good example
Policy clearly states what the agent can do autonomously, what requires approval, and how actions are logged.

#### Bad example
No distinction between safe and dangerous action categories.

### 5.16 Trust and provenance as a cross-cutting primitive

Trust touches discovery, identity, autonomy, and recovery enough that it may either remain inside Social Proof or stand as its own cross-cutting dimension. For an AX standard, I recommend treating provenance as mandatory metadata across all primitives.

### 5.17 Taxonomy summary

A mature AX standard likely needs at least these primitives:
- Context
- Access
- Navigation
- Discovery
- Notifications
- Memory
- Identity
- Feedback
- Recovery
- Communication
- Autonomy
- Onboarding
- Social Proof
- Orchestration
- Governance

This is a stronger foundation than the initial candidate list because it adds Access and Orchestration explicitly and recognizes Governance as unavoidable.

---

## 6. The AXD (Agent Experience Document) Format

The AXD should be the canonical structured artifact a platform, tool, API, skill, or marketplace ships to describe how agents should interact with it.

Think of it as:
- part OpenAPI summary
- part `llms.txt`
- part package manifest
- part runbook
- part trust and governance declaration

### 6.1 Goals of AXD

An AXD should let an agent answer these questions quickly:

1. What is this thing for?
2. What capabilities does it expose?
3. How do I access it?
4. What can I safely do without approval?
5. What are the main workflows?
6. What inputs and outputs should I expect?
7. What failure modes are common?
8. How do I recover or escalate?
9. How trustworthy is this artifact?
10. What runtime, protocol, and version constraints apply?

### 6.2 AXD design principles

- machine-readable first, human-readable second
- concise by default, expandable for depth
- task-oriented, not only resource-oriented
- protocol-agnostic where possible
- explicit about risk, auth, and recovery
- versioned and signed when possible
- easy to colocate with APIs, CLIs, skills, MCP servers, and marketplace entries

### 6.3 Recommended file forms

AXD can have two forms:

1. `AXD.md` or `axd.md` for readable markdown with structured sections
2. `axd.json` for strict machine parsing

The markdown file can embed a machine-readable YAML or JSON frontmatter block.

### 6.4 Proposed AXD top-level sections

#### 1. Metadata
- name
- slug
- version
- publisher
- verification status
- last updated
- homepage
- docs URL
- support URL
- license
- signature or provenance fields

#### 2. Purpose
- one-line purpose
- primary use cases
- non-goals
- intended users, human, agent, both

#### 3. Compatibility
- supported runtimes, e.g. OpenClaw, MCP clients, Claude Desktop, ChatGPT apps
- supported models or minimum capability assumptions
- supported protocols, HTTP API, MCP, CLI, webhooks
- required environment variables or system dependencies

#### 4. Access and authentication
- auth methods
- scopes
- delegated auth supported or not
- token lifetimes
- human approval requirements
- identity model

#### 5. Capabilities
For each capability:
- name
- description
- action type, read, write, destructive, admin
- inputs schema
- outputs schema
- side effects
- idempotency notes
- cost or latency hints
- example call and example response

#### 6. Recommended workflows
Task-based flows such as:
- search item → inspect details → download version
- connect account → list resources → create change → confirm result

Each workflow should include:
- prerequisites
- required capabilities
- main path
- failure branches
- expected outputs

#### 7. Context resources
- `llms.txt`
- docs indexes
- glossary
- example prompts
- schema references
- policy files
- context files

#### 8. Notifications and events
- webhook support
- event names
- payload schemas
- retry and dedupe rules
- polling alternative
- urgency semantics

#### 9. Memory and state
- session model
- durable state model
- resumability
- expiration rules
- checkpoint strategy

#### 10. Errors and recovery
- error taxonomy
- retryable versus terminal
- rate limit behavior
- rollback or compensation options
- escalation paths

#### 11. Autonomy and governance
- safe autonomous actions
- actions requiring approval
- irreversible actions
- audit logging behavior
- recommended approval policy

#### 12. Trust signals
- verification status
- maintainer identity
- update cadence
- install count or usage stats
- known limitations
- security posture
- test coverage or certification

#### 13. Examples
- quickstart example
- low-context example
- high-context example
- failure recovery example

#### 14. Changelog
- semantic version history
- breaking changes
- migration notes

### 6.5 Minimal AXD schema proposal

```yaml
axd_version: 0.1
name: souls.zip marketplace api
slug: souls-zip-marketplace-api
version: 2.0.0
publisher:
  name: souls.zip
  verified: true
  url: https://souls.zip
purpose:
  summary: Agent-first marketplace for discovering, purchasing, and downloading agent assets.
  primary_use_cases:
    - browse marketplace items
    - inspect versions and reviews
    - verify purchases and download assets
compatibility:
  protocols: [https, json]
  runtimes: [openclaw, custom-http-client]
access:
  auth_methods:
    - bearer_token
    - siwe_wallet_auth
  scopes:
    - keys:manage
capabilities:
  - name: search_items
    action_type: read
    endpoint: GET /api/v2/items
    inputs:
      query: string
      filters: object
    outputs:
      items: array
    side_effects: none
    idempotent: true
notifications:
  supports_webhooks: false
recovery:
  error_types:
    - rate_limit
    - auth_required
    - payment_required
autonomy:
  safe_actions:
    - browse_items
    - read_reviews
  approval_required:
    - create_api_key
trust:
  verification: verified_publisher
  last_updated: 2026-03-13
```

### 6.6 AXD section guidance in more detail

#### Metadata must be trustworthy
If the artifact is unsigned or unverifiable, trust suffers. If possible, AXD should include checksum or signature metadata.

#### Capabilities should be task-shaped
Do not just enumerate endpoints. Group them into capabilities the agent can reason about.

#### Recovery should be explicit
Most docs explain success paths. AXD must explain failure paths too. That is a key differentiator.

#### Governance must be first-class
Agents need to know not only what is possible, but what is allowed.

#### Examples should include bad paths
At least one example should show how to recover from auth failure, rate limit, or missing preconditions.

### 6.7 AXD levels

To make adoption practical, define maturity tiers.

#### Level 0, no AXD
No machine-readable agent interaction guide.

#### Level 1, basic AXD
Purpose, access, capabilities, examples.

#### Level 2, operational AXD
Adds errors, recovery, events, trust signals, and governance.

#### Level 3, production AXD
Adds signatures, compatibility matrix, metrics, quality certification, and change notifications.

### 6.8 Where AXD should live

- root of repo: `AXD.md`, `axd.json`
- docs site: `/axd` and `/axd.json`
- API: `/api/axd` or `/api/v1/axd`
- MCP servers: exposed as a resource or docs link
- marketplace listings: embedded and indexable

### 6.9 Relationship to existing standards

AXD should complement, not replace:
- OpenAPI, for HTTP contract detail
- AsyncAPI, for event contracts
- MCP manifests, for standard protocol integration
- package manifests, for installability
- `llms.txt`, for docs discovery

AXD is the missing synthesis layer: the operator’s guide for agents.

### 6.10 Why AXD matters strategically

An AX standard will struggle if it is only abstract principles. Teams need a shippable artifact. AXD gives:
- a portable compliance target
- a marketplace indexing substrate
- a discoverability surface
- a trust and compatibility layer
- a way to benchmark products on AX maturity

This makes AX operational, not rhetorical.

---

## Proposed AX Principles for souls.zip and the broader standard

Based on all research above, here is a concise set of proposed principles for the AX standard.

### Principle 1. Agents are users
Treat agents as first-class users with distinct strengths and weaknesses.

### Principle 2. Structure is the interface
For agents, APIs, schemas, manifests, and status objects are the UI.

### Principle 3. Context beats prompting
Success depends more on environment design and context delivery than on clever prompts.

### Principle 4. Open ecosystems win
Users should be able to bring their preferred agents. Design for interoperability.

### Principle 5. Every action needs feedback
Agents need machine-readable progress, outcome, and next-step signals.

### Principle 6. Recovery is mandatory
A system is not agent-ready unless failure modes are explicit and recoverable.

### Principle 7. Discovery is part of the product
If agents cannot find, compare, and trust capabilities, the ecosystem stalls.

### Principle 8. Auth is experience
Permissions, scopes, and approval flows are central to AX quality.

### Principle 9. Long-running work needs memory and events
Good AX supports durable state, resumability, and event-driven coordination.

### Principle 10. Trust must be computable
Provenance, compatibility, verification, and quality signals should be machine-usable.

### Principle 11. Autonomy must be bounded
Good AX makes safe action easy and dangerous action explicit.

### Principle 12. Agent accessibility matters
Systems should work across models, context budgets, modalities, and execution environments.

---

## Recommendations for souls.zip specifically

### Near-term
1. Publish an `AXD` spec draft and use souls.zip as the reference implementation.
2. Add structured item metadata for runtime compatibility, auth needs, safety level, update recency, and verification.
3. Expand the v2 API docs from endpoint listing to capability schemas and examples.
4. Add `llms.txt` or equivalent docs index for all public docs.
5. Create marketplace trust signals that agents can actually compute on.

### Mid-term
1. Introduce certification levels for “AX-ready” assets.
2. Add event/webhook surfaces for asset updates, reviews, purchases, and compatibility changes.
3. Add machine-readable review and benchmark summaries.
4. Support canonical manifests for souls, skills, tools, teams, and memories.

### Long-term
1. Make souls.zip the public registry for AX components and AXD documents.
2. Define a compatibility badge ecosystem across OpenClaw, MCP, ChatGPT apps, Claude Desktop, and others.
3. Publish an open benchmark for AX quality across discovery, onboarding, recovery, trust, and orchestration.

---

## 7. Extended UX → AX Pattern Library

This section expands the mapping work into concrete design patterns that can later become registry entries or standard component definitions.

### 7.1 Visibility patterns for agents

In human UX, visibility often means labels, progress bars, or toasts. In AX, visibility is a deeper systems concern because the agent may have no embodied sense of the environment unless visibility is deliberately externalized.

#### Pattern: Explicit run state machine
A long-running operation should expose states such as:
- pending
- queued
- scheduled
- running
- waiting_for_input
- waiting_for_approval
- partially_completed
- succeeded
- failed_retryable
- failed_terminal
- cancelled
- rolled_back

##### Why it matters
Without a state machine, the agent cannot reason about whether it should wait, retry, escalate, or proceed to the next step.

##### Good implementation
A deployment job returns a job ID and a state enum with timestamps for each transition. It also includes `next_recommended_action`.

##### Bad implementation
The system responds `accepted` and then provides no further structure.

#### Pattern: Action receipts
Any side-effecting action should produce a receipt.

A receipt can include:
- action ID
- actor identity
- target resource
- before/after summary
- exact time
- undo availability
- audit URL

This is the agent equivalent of a good confirmation screen.

#### Pattern: Inspectable logs
Logs should be queryable and scoped, not dumped indiscriminately.

Good logs:
- structured
- filterable by run ID, tool, severity, and phase
- available in short summary and full detail forms

Bad logs:
- unbounded plain text walls
- missing correlation IDs
- not fetchable through API

### 7.2 Recognition patterns for agents

Recognition rather than recall becomes one of the most important AX principles because agents are highly context-sensitive and often operate under token budgets.

#### Pattern: Capability cards
Each capability should be represented in a compact standard card with:
- name
- summary
- read/write/destructive label
- auth required
- input schema summary
- example
- compatibility
- trust score

This is the agent equivalent of making controls visible rather than hidden.

#### Pattern: Inline examples
Every tool or API operation should have at least one minimal valid example and one realistic example.

Why this matters:
- agents often synthesize calls by analogy
- examples reduce hallucinated argument names
- examples anchor expected output shapes

#### Pattern: Self-describing resources
Search results should include the identifiers and fields needed for next-step actions. A result that forces the agent to look up invisible metadata is poor AX.

### 7.3 Control and freedom patterns for agents

#### Pattern: Dry-run everywhere possible
For mutating actions, a dry-run mode should be standard.

A dry-run can return:
- what would happen
- which records would change
- conflicts or validation issues
- estimated cost or duration
- approval recommendation

This is the agent equivalent of preview and confirmation.

#### Pattern: Bounded authority levels
Not every agent should have the same rights. Systems should define authority tiers such as:
- observe only
- recommend only
- prepare draft
- execute low-risk actions
- execute high-risk actions with approval
- admin actions restricted

This pattern matters because “autonomy” without gradation is crude.

#### Pattern: Default-safe mutations
If both reversible and irreversible versions of an action exist, the reversible one should be the default discoverable option.

Good:
- `archive_project`
- `restore_project`
- separate `hard_delete_project`

Bad:
- only `delete_project`

### 7.4 Consistency patterns for agents

Consistency in AX is not just aesthetic, it is statistical leverage. Agents learn local patterns quickly. Every inconsistency forces relearning.

#### Areas where consistency matters most
- argument naming
- ID formats
- timestamps
- pagination
- filter syntax
- error shape
- status enums
- auth challenge format
- event names

#### Pattern: Shared contract blocks
If a platform has many tools or endpoints, shared contract blocks should be defined once and reused.

Examples:
- a universal `Pagination` object
- standard `Error` object
- standard `AuditInfo`
- standard `ApprovalRequirement`

This reduces ambiguity and makes transfer learning easier for the agent.

### 7.5 Minimalism patterns for agents

In human UX, minimalism prevents clutter. In AX, minimalism protects context windows and improves reasoning clarity.

#### Pattern: Layered verbosity
Every response should support at least two levels:
- concise summary for immediate reasoning
- expandable full detail for follow-up fetch

#### Pattern: Summary + handle
Instead of returning massive payloads, return a summary plus a handle to fetch more.

Good example:
- search returns top 10 results with IDs and snippets
- `fetch_result` retrieves the full document when needed

This is the same design logic OpenAI’s deep research MCP guidance uses through `search` and `fetch` tools.

#### Pattern: Relevance-ranked fields
Do not return every field equally. Return the most decision-relevant fields first.

### 7.6 Recovery pattern library

The public AX conversation is still too light on recovery. This needs to be a standard component set.

#### Pattern: Retry contract
A retry contract should answer:
- is retry allowed?
- when?
- how many times?
- with same parameters or modified ones?
- does the system dedupe repeated submissions?

#### Pattern: Human escalation envelope
When an agent cannot proceed, it should be able to package the problem for human review.

A good escalation envelope includes:
- what the agent tried
- what failed
- confidence level
- relevant evidence
- recommended options
- default safe action if no response

This is the agent equivalent of a well-crafted support escalation.

#### Pattern: Compensating action references
If an action changes state, the system should surface any available compensating actions.

Good:
- create invoice → void invoice
- assign user → unassign user
- publish page → unpublish page

#### Pattern: Failure provenance
Errors should include where the failure occurred:
- client-side validation
- auth layer
- transport layer
- tool execution layer
- downstream provider layer
- policy layer

Without provenance, debugging becomes expensive and ambiguous.

### 7.7 Accessibility patterns for agents in depth

If AX is going to become a serious standard, accessibility must be expanded beyond the human framing.

#### Agent accessibility dimensions

##### 1. Context accessibility
Can a smaller model or low-context environment still operate the system effectively?

##### 2. Modality accessibility
Can the same task be done through API, CLI, MCP, or accessible web flow?

##### 3. Semantic accessibility
Are names and outputs semantically clear without hidden conventions?

##### 4. Operational accessibility
Can the system be used under limited permissions, intermittent connectivity, or rate limits?

##### 5. Compression accessibility
Can a long manual be summarized without losing the critical constraints needed to operate safely?

#### Good AX accessibility example
A service offers:
- concise markdown docs
- a JSON schema bundle
- a CLI with `--json`
- event/webhook alternatives to polling
- examples for simple and advanced modes

#### Bad AX accessibility example
The service only offers:
- a visual dashboard
- a video tutorial
- screenshots of configuration
- no programmatic surface

### 7.8 Trust pattern library

Trust for agents must become more machine-readable.

#### Pattern: Capability provenance
Every asset should declare:
- publisher identity
- verification level
- release date
- changelog
- dependency provenance
- signing key or checksum if applicable

#### Pattern: Quality badge taxonomy
A future AX registry could certify badges like:
- AX Basic
- AX Operational
- AX Recoverable
- AX Event-Ready
- AX Verified Publisher
- AX Safe-Mutation

#### Pattern: Runtime compatibility matrix
A tool or skill should specify:
- supported runtimes
- tested clients
- minimum protocol version
- unsupported environments

Agents should not have to infer compatibility from README prose.

### 7.9 Search and ranking patterns for agents

Human app stores are optimized for persuasion. Agent registries must be optimized for selection quality.

#### Agent ranking inputs should include
- relevance to task intent
- compatibility
- auth feasibility
- safety level
- freshness
- performance score
- cost
- trust score
- prior success rate
- installation friction

#### Pattern: Explainable ranking
Search results should include why a capability ranked highly.

Good example:
- compatible with OpenClaw
- verified publisher
- last updated 8 days ago
- read-only and no auth required
- high success rate for “market research” tasks

This helps both agents and humans audit selection.

### 7.10 Memory design patterns in depth

#### Pattern: Checkpoint summaries
Long tasks should generate checkpoints containing:
- completed steps
- current blockers
- next planned action
- resources created or modified
- pending approvals

This is much better than forcing the agent to reconstruct progress from raw logs.

#### Pattern: Scoped memory retrieval
Memory retrieval should be queryable by scope:
- session
- project
- user
- org
- task type
- external system

#### Pattern: Freshness labels
Memory items should show when they were last confirmed. Agents should treat stale memory differently from current memory.

### 7.11 Multi-agent patterns

Since many real systems will involve multiple agents, the AX standard should acknowledge shared work.

#### Pattern: Delegation packet
A delegation packet should include:
- task statement
- acceptance criteria
- relevant context
- output format
- time expectation
- blocked-state behavior

#### Pattern: Shared artifact references
Agents should pass around canonical references, not copied blobs, where possible.

#### Pattern: Completion announcements
Subagents should announce concise completion summaries with artifact locations and notable caveats.

These patterns are already visible in strong multi-agent systems and deserve standardization.

---

## 8. Implementation Guidance for an Open AX Standard

A standard only matters if teams can adopt it incrementally. This section translates the research into a practical rollout path.

### 8.1 The shortest path to adoption

The first version of AX should not try to standardize everything. It should standardize the smallest set of practices that create compounding benefit.

Recommended first-wave standard components:
1. AXD core schema
2. capability cards
3. error and recovery taxonomy
4. trust/provenance metadata
5. event payload recommendations
6. compatibility labels

### 8.2 Suggested AX scoring model

Platforms and assets can be scored across the core primitives.

#### Example scoring dimensions
- Discoverability
- Access clarity
- Capability clarity
- Feedback quality
- Recovery quality
- Trust/provenance
- Compatibility transparency
- Event readiness
- Memory/resumability
- Governance safety

A 0-5 score in each dimension could produce an overall AX score. This would be useful on souls.zip and helpful for benchmarking ecosystems.

### 8.3 Suggested certification tiers

#### Tier A: Discoverable
- has machine-readable docs or manifest
- capabilities identifiable
- examples available

#### Tier B: Operable
- auth and scopes documented
- structured outputs and errors
- compatibility declared

#### Tier C: Recoverable
- retries, fallback, escalation, and rollback paths documented
- event or status contracts available

#### Tier D: Production-grade
- provenance verified
- audit and governance declared
- metrics and trust signals exposed

### 8.4 Suggested canonical metadata fields for registries

If souls.zip wants to become the AX-native registry, each listing should eventually expose fields like:

- `asset_type`, soul, skill, tool, team, memory, policy, workflow
- `runtime_compatibility`
- `protocols_supported`
- `auth_required`
- `scopes_required`
- `safety_level`
- `read_write_profile`
- `last_verified_at`
- `publisher_verified`
- `avg_success_rate`
- `install_count`
- `last_updated`
- `maintenance_status`
- `supports_events`
- `supports_dry_run`
- `supports_rollback`
- `docs_index_url`
- `axd_url`

These fields would make search and ranking dramatically better for agents.

### 8.5 Suggested error taxonomy for AX

A shared error taxonomy would create huge leverage across platforms.

Recommended top-level classes:
- `AUTH_REQUIRED`
- `AUTH_INSUFFICIENT_SCOPE`
- `APPROVAL_REQUIRED`
- `RATE_LIMIT`
- `INVALID_INPUT`
- `RESOURCE_NOT_FOUND`
- `RESOURCE_CONFLICT`
- `PRECONDITION_FAILED`
- `DEPENDENCY_FAILURE`
- `TEMPORARY_UNAVAILABLE`
- `POLICY_BLOCKED`
- `BUDGET_EXCEEDED`
- `UNSUPPORTED_OPERATION`
- `TERMINAL_FAILURE`

Each error should also include:
- retryability
- recommended next step
- human required or not
- correlation ID

### 8.6 Suggested event taxonomy for AX

A shared event taxonomy would help agents generalize across platforms.

Recommended generic events:
- `resource.created`
- `resource.updated`
- `resource.deleted`
- `job.queued`
- `job.started`
- `job.waiting_for_approval`
- `job.completed`
- `job.failed`
- `auth.expiring`
- `approval.requested`
- `approval.resolved`
- `review.added`
- `version.published`
- `version.deprecated`

### 8.7 Suggested trust/provenance model

Trust signals should be exposed in structured form, not only visual badges.

Possible fields:
- `publisher_identity`
- `publisher_verified`
- `artifact_signed`
- `signature_scheme`
- `source_repository`
- `security_audit_status`
- `community_rating`
- `usage_volume`
- `recent_failure_rate`
- `compatibility_test_matrix`

### 8.8 Suggested compatibility model

Compatibility should not be a single string. It should be multi-dimensional.

Dimensions:
- runtime, OpenClaw, Claude Desktop, Cursor, ChatGPT Apps, generic MCP
- interaction type, API, CLI, MCP, webhooks, web UI
- auth type, none, API key, OAuth, wallet auth, custom
- modality, text, code, browser, file, voice
- execution constraints, network required, local only, sandbox compatible

### 8.9 Suggested onboarding sequence for AX-native products

An AX-native onboarding flow might look like:

1. **Identify environment**  
   What runtime is the agent in? What protocols are available?
2. **Fetch core manifest**  
   Read `AXD` and `llms.txt`.
3. **Establish access**  
   Determine auth requirements and available scopes.
4. **Run safe starter task**  
   Validate one simple read-only workflow.
5. **Learn mutation boundaries**  
   Understand approvals, dry-run, and rollback patterns.
6. **Subscribe or poll responsibly**  
   Establish event or status monitoring behavior.
7. **Checkpoint**  
   Save a summary of the environment and successful patterns.

This could become a recommended standard sequence.

### 8.10 Suggested benchmark scenarios for the AX standard

To make AX measurable, define benchmark tasks.

Example benchmark scenarios:
- find the correct tool for a task under constraints
- authenticate with minimum necessary scope
- perform a read-only task successfully on first try
- perform a mutating task using dry-run then approved execution
- recover from a rate-limit error
- resume a paused task from saved memory
- compare two assets using structured trust signals
- install or attach a capability and verify compatibility

A platform that performs well across these scenarios likely has materially good AX.

### 8.11 Governance recommendations for the standard itself

The AX standard should avoid becoming purely aspirational. It needs:
- open schema definitions
- reference implementations
- validation tools
- conformance tests
- versioning and deprecation policy
- public examples from real platforms

souls.zip is well positioned to host these.

### 8.12 Why this matters commercially

Good AX is not just elegance. It changes distribution and retention.

If agents increasingly influence which tools, APIs, marketplaces, and products get used, then the systems with the best AX will enjoy:
- more successful first-run interactions
- lower integration friction
- better agent-mediated recommendations
- higher reuse of capabilities
- stronger platform lock-in through reliability rather than opacity

AX may become a major go-to-market surface. In that sense, Biilmann’s suggestion that we are moving toward “agent-led growth” is plausible. The best product may increasingly be the one that agents can successfully operate.

## Conclusion

AX is real, early, and strategically important. The best public writing has already identified the core move: agents are not just features inside products, they are becoming users of products. Once that is true, the design question changes.

The interface is no longer just a screen. It is the whole operational surface:
- docs
- schemas
- auth
- examples
- events
- memory
- trust metadata
- workflow contracts
- recovery paths

UX taught us to design for human cognition. DX taught us to design for developer flow. AX asks us to design for machine operators that are powerful, literal, context-sensitive, error-prone in strange ways, and increasingly central to how humans derive value from software.

The winning systems will not just bolt on an agent. They will make themselves legible, safe, discoverable, and composable for agents.

That is the work of AX.

---

## 9. Concrete Good vs Bad AX Examples by Primitive

This section is intentionally repetitive in the useful way. Standards become real when teams can point to examples and say, “this is what good looks like.”

### 9.1 Context

#### Good
A project-management API gives the agent a compact workspace summary:
- current user and role
- available projects
- timezone
- known rate limits
- default approval policy
- pointers to docs and event endpoints

The agent starts with a coherent model of the environment.

#### Bad
The agent gets an API key and nothing else. It has to guess:
- what account it is operating in
- which objects exist
- whether actions are read-only or mutating
- what naming conventions apply

### 9.2 Access

#### Good
A CRM platform offers delegated OAuth with separate scopes for:
- read contacts
- write contacts
- send email
- admin billing

The agent can ask for minimal permission and explain why.

#### Bad
One bearer token grants all permissions. The agent either has too much power or cannot act at all.

### 9.3 Navigation

#### Good
A storage system lets the agent:
- list folders
- fetch folder details
- list files within a folder
- fetch file metadata
- download file contents

Identifiers are stable and every result links to the next valid steps.

#### Bad
The system can search files by name but returns no canonical IDs usable for download or mutation.

### 9.4 Discovery

#### Good
A skill registry returns search results with:
- title
- summary
- compatible runtimes
- auth requirements
- safety level
- last updated
- install count
- rating
- publisher verification

The agent can rank candidates intelligently.

#### Bad
A registry returns only title and marketing description. The agent must click through each result and still cannot determine compatibility.

### 9.5 Notifications

#### Good
A billing platform emits `invoice.overdue` events containing:
- customer ID
- invoice ID
- amount due
- due date
- urgency
- retry count
- direct fetch URL
- idempotency key

The agent can decide whether to remind, escalate, or bundle the issue into a digest.

#### Bad
The platform sends a daily HTML email with mixed account notices and no machine-readable structure.

### 9.6 Memory

#### Good
After each run, an agent saves:
- the task objective
- resources touched
- decisions made
- unresolved blockers
- next step
- timestamp and evidence links

A later run can resume work without replaying everything.

#### Bad
The only memory is a full transcript. Important conclusions are buried in noise.

### 9.7 Identity

#### Good
Every action is attributable to:
- agent name
- runtime session ID
- delegated user
- policy profile
- tool version

This supports auditability and trust.

#### Bad
Logs show only “automation executed action,” with no indication of who or what initiated it.

### 9.8 Feedback

#### Good
A content publishing platform returns:
- status: `scheduled`
- publish_at
- content ID
- preview URL
- cancel action
- policy warnings

The agent knows the exact result of its action.

#### Bad
The API returns `ok: true` without any artifact IDs or resulting state.

### 9.9 Recovery

#### Good
An external-service call fails with:
- `DEPENDENCY_FAILURE`
- provider name
- retryable: true
- retry_after_seconds: 45
- suggested action: retry or queue for later

The agent can recover deterministically.

#### Bad
The failure message is `500 internal error`, and the agent cannot tell whether retrying is safe or useless.

### 9.10 Communication

#### Good
A multi-agent workflow passes tasks using a structured packet:
- objective
- context
- acceptance criteria
- output path
- deadline
- escalation rule

#### Bad
A supervisor agent says “take a look at this” with no scope or deliverable definition.

### 9.11 Autonomy

#### Good
An internal ops platform labels actions as:
- autonomous-safe
- autonomous-with-notification
- requires-human-approval
- prohibited

The agent knows how far it can go.

#### Bad
The policy says only “be careful,” which is not operational.

### 9.12 Onboarding

#### Good
A new agent can:
- read a 500-token quickstart
- run a read-only sample task
- inspect one successful example call
- learn where to find full docs later

#### Bad
A new agent receives 60 pages of docs and no starter path.

### 9.13 Social proof

#### Good
A registry entry exposes:
- verified publisher
- maintainer history
- adoption count
- mean latency
- reported failure rate
- last compatibility test date

#### Bad
Only a star rating appears, with no provenance or operational meaning.

### 9.14 Orchestration

#### Good
A workflow platform emits run IDs, supports pausing and resuming, and makes artifact storage browsable.

#### Bad
Workflows are brittle chains with no observable intermediate state.

### 9.15 Governance

#### Good
The platform policy declares:
- actions requiring approval
- irreversible actions
- audit retention window
- escalation path for policy conflicts

#### Bad
Governance is implied by tribal knowledge, not encoded anywhere agents can see.

## 10. Draft Canonical Templates for the AX Standard

To speed adoption, the standard should ship templates teams can copy.

### 10.1 Capability card template

```yaml
name: create_invoice
summary: Create a draft invoice for an existing customer.
action_type: write
risk_level: medium
approval_required: false
idempotent: true
auth_scopes:
  - invoices:write
inputs:
  customer_id: string
  line_items: array
  due_date: string
outputs:
  invoice_id: string
  status: draft
  preview_url: string
side_effects:
  - draft invoice record created
common_failures:
  - INVALID_INPUT
  - AUTH_INSUFFICIENT_SCOPE
  - RESOURCE_NOT_FOUND
example:
  input:
    customer_id: cus_123
    line_items:
      - description: Research sprint
        amount: 150000
    due_date: 2026-03-20
```

### 10.2 Event template

```yaml
event_name: invoice.overdue
version: 1
resource: invoice
delivery:
  mode: webhook
  retries: exponential
  dedupe_key: invoice_id + updated_at
payload:
  invoice_id: string
  customer_id: string
  due_date: string
  amount_due: integer
  currency: string
  urgency: enum(low, medium, high)
  fetch_url: string
```

### 10.3 Recovery template

```yaml
error_code: RATE_LIMIT
retryable: true
retry_after_seconds: 60
human_required: false
suggested_actions:
  - wait_and_retry
  - reduce_batch_size
  - switch_to_webhook_mode_if_available
correlation_id: abc123
```

### 10.4 Trust metadata template

```yaml
publisher:
  name: souls.zip
  verified: true
artifact:
  signed: true
  signature_scheme: ed25519
maintenance:
  last_updated: 2026-03-13
  status: active
quality:
  install_count: 6042
  avg_success_rate: 0.94
  median_latency_ms: 820
compatibility:
  runtimes:
    - openclaw
    - generic-mcp-client
```

### 10.5 AXD markdown skeleton

```md
# AXD: [Product Name]

## Purpose
## Quickstart for Agents
## Access and Scopes
## Capabilities
## Main Workflows
## Events and Notifications
## Memory and Resumability
## Error and Recovery Guide
## Autonomy and Approval Policy
## Trust and Provenance
## Compatibility
## Changelog
```

## 11. Final Synthesis: What AX Changes in Practice

AX changes how teams think about product quality.

### Old mindset
- if the API exists, agents can use it
- docs are for humans
- auth is an implementation detail
- trust is mostly branding
- failures can be handled manually later

### New mindset
- the API is the interface
- docs need machine-readable affordances
- auth is a user experience for agents
- trust must be computable
- failure handling is part of the product contract

### What teams will need to add
- manifests and indexes
- capability metadata
- machine-readable examples
- standard errors and events
- approval semantics
- compatibility labels
- provenance and reputation signals

### The strategic bet
The platforms that make themselves easiest for agents to discover, trust, and operate will increasingly win distribution. The marketplace that best indexes and standardizes that experience can become the default registry for the agent ecosystem.

That is the opening for souls.zip.

## 12. AX Implementation Roadmap for Platform Teams

For teams wanting to improve their AX, here is a practical priority order.

### Phase 1: Foundation (Weeks 1-4)
Build the minimum viable AX surface.

#### Work items
1. Write an AXD skeleton with purpose, access, capabilities, and a worked example.
2. Add `llms.txt` or API docs summary in JSON format.
3. Document error codes and recovery paths.
4. Identify which actions are safe autonomous, approval-required, or prohibited.

#### Success criteria
- An unfamiliar agent can discover, authenticate, run one safe read-only task, and understand failure recovery in under 10 minutes.

### Phase 2: Discoverability (Weeks 5-8)
Make your surface more agent-findable within existing ecosystems.

#### Work items
1. Index your offering on skills.sh or relevant marketplace.
2. Publish structured metadata: runtimes, auth types, safety levels.
3. Add examples for common workflows.
4. Create quick reference cards for major capabilities.

#### Success criteria
- Agents searching for "your domain task" find your offering and understand compatibility.

### Phase 3: Events and Memory (Weeks 9-14)
Move from request-response to event-driven and stateful interaction.

#### Work items
1. Expose key state changes as webhooks or events.
2. Define event payload schemas and dedupe keys.
3. Implement or document status polling alternatives.
4. Add support for run IDs and resumable workflows.

#### Success criteria
- Long-running tasks don't require constant polling. Agents can check in later using a handle.

### Phase 4: Trust and Verification (Weeks 15-20)
Build computable trust signals.

#### Work items
1. Sign your AXD or provide checksums.
2. Add publisher verification to your registry entries.
3. Publish compatibility test results.
4. Expose quality metrics: uptime, latency percentiles, error rates.

#### Success criteria
- Agents comparing tools can rank you based on trust data, not just guessing.

### Phase 5: Orchestration (Weeks 21+)
Enable coordinated multi-agent and workflow scenarios.

#### Work items
1. Support agent-to-agent handoff packets with explicit contracts.
2. Implement callback webhooks for completion notifications.
3. Add batch or bulk operations.
4. Expose audit trails for compliance.

#### Success criteria
- Multi-agent systems can reliably coordinate work without polling or manual intervention.

## 13. Why AX Matters Beyond Product Design

AX is not only a UX discipline. It has business, strategic, and ecosystem implications.

### Competitive implication
As agents become significant users of products, the products they can operate effectively will capture disproportionate agent usage and, through agents, human users. The platforms with the best AX will enjoy network effects that are hard to replicate through feature parity alone.

### Distribution shift
In the current world, distribution is driven by brand, user acquisition, and ease of manual onboarding. In the agent world, distribution is driven by agent-friendliness, discovery, trust signals, and orchestration support. Teams optimizing only for human UX will miss a major shift in how new products reach users.

### Marketplace opportunity
The team that becomes the canonical registry or marketplace for agent-friendly components will occupy a similar position to what npm, PyPI, and GitHub occupy for developers. souls.zip has an opportunity to become that for agents.

### Open standard advantage
Unlike proprietary agent platforms, an open AX standard creates interoperability. Agents can move between platforms, tools can work across runtimes, and the ecosystem grows faster. The first team to invest seriously in open standards will likely end up defining the category.

### Governance and safety
As agent autonomy increases, AX becomes a key lever for safety. Explicit autonomy boundaries, approval workflows, audit trails, and recovery paths are not nice-to-haves. They are operational requirements. AX that includes strong governance patterns will be table-stakes for enterprise adoption.

## 14. The Path Forward for souls.zip

Based on all research and pattern analysis, here are specific recommendations for souls.zip.

### Immediate priorities (next 30 days)
1. Publish a public draft AXD specification tied to souls.zip marketplace items.
2. Add structured metadata fields to the v2 API for every asset: runtimes, auth types, safety levels, trust signals.
3. Build an `llms.txt` index for all public docs and asset manifests.
4. Create capability cards for top 50 marketplace items as examples.

### Medium-term (30-90 days)
1. Introduce an AX certification tier system for assets (Basic, Operational, Recoverable, Production).
2. Add event/webhook support for asset updates, reviews, and availability changes.
3. Launch an AX maturity scoring tool that can rate any platform against the taxonomy.
4. Partner with 3-5 major OpenClaw agents to beta-test the AXD spec.

### Long-term (90+ days)
1. Make souls.zip the canonical AX registry, referenced by the open standard.
2. Publish comprehensive benchmarks showing the AX quality across 100+ platforms.
3. Offer AX consulting and certification services for platform teams.
4. Build into souls.zip a "compatibility passport" showing which agents can operate which assets under which conditions.

### Why souls.zip is positioned to lead
- It already exists as an agent-first marketplace.
- The team understands agent needs and philosophy.
- The v2 API is already oriented toward agent interaction.
- The OpenClaw community is a built-in test and reference base.
- Being open-source and community-driven removes vendor lock-in concerns.

## 15. Limitations and Future Questions

This research defines AX as it appears in early 2026. Some areas remain underdeveloped and warrant future investigation.

### Open questions
1. How should AX scale to systems with thousands of capabilities?
2. What is the right balance between standardization and product-specific optimization?
3. How do we handle real-time collaboration between agents and humans?
4. What AX patterns work best for agents operating under extreme context or compute constraints?
5. How should AX evolve as agent reasoning and planning capabilities improve?
6. What governance structures ensure an open AX registry remains trustworthy?
7. How do we measure AX quality in practice?

### Areas for future work
- Formal semantics for agent-workflow languages
- Benchmarking frameworks for AX quality
- Security and safety audit standards for agent-facing APIs
- Integration patterns for agents in safety-critical environments
- Accessibility standards for agents operating with low context windows

## Final Thoughts

Agent Experience is not speculative. It is real, it is competitive, and it is shaping where investment and innovation flow.

The question is not whether AX matters. It is who will define it. Will it emerge organically from hundreds of platforms each solving the problem independently? Or will an open standard, driven by community and tested against real usage, set the baseline that everyone builds on?

The clearest path forward is for a founding team, such as souls.zip, to:
1. Publish an initial standard
2. adopt it rigorously in their own products
3. invite community input and iteration
4. build tools and benchmarks that make conformance easy
5. recognize and amplify the teams doing AX well

This research is offered as a foundation for that work. The taxonomy is not final. The patterns are not exhaustive. But they are grounded in real platforms, real problems, and real opportunities.

AX will become as foundational to software quality as UX is today. The teams that build AX-first will outcompete those that add AX as an afterthought.

The work starts now.

---

## Sources


### Core AX sources
- Mads Biilmann, “Introducing AX: Why Agent Experience Matters”  
  https://biilmann.blog/articles/introducing-ax/
- Mads Biilmann, “One Year of AX”  
  https://biilmann.blog/articles/one-year-of-ax/
- Mads Biilmann, “is it Agent or Agentic?”  
  https://biilmann.blog/articles/ax-is-it-agent-or-agentic/
- Microsoft Design, “UX design for agents”  
  https://microsoft.design/articles/ux-design-for-agents/
- Standard Beagle, “Designing systems for AI agents: What makes a good AX?”  
  https://standardbeagle.com/designing-systems-for-ai-agents/
- UX Design Institute, “How To Design Experiences for AI Agents in 2025”  
  https://www.uxdesigninstitute.com/blog/design-experiences-for-ai-agents/

### Protocol and platform sources
- Anthropic, “Introducing the Model Context Protocol”  
  https://www.anthropic.com/news/model-context-protocol
- Model Context Protocol docs, “What is the Model Context Protocol (MCP)?”  
  https://modelcontextprotocol.io/introduction
- OpenAI, “GPT Actions”  
  https://developers.openai.com/api/docs/actions/introduction
- OpenAI, “Building MCP servers for ChatGPT Apps and API integrations”  
  https://developers.openai.com/api/docs/mcp/
- souls.zip homepage  
  https://souls.zip
- souls.zip v2 API docs  
  https://souls.zip/api/v2/docs
- Composio homepage  
  https://composio.dev
- Composio docs  
  https://docs.composio.dev/docs
- skills.sh  
  https://skills.sh
- PyPI  
  https://pypi.org

### UX foundations used for mapping
- Nielsen Norman Group, “10 Usability Heuristics for User Interface Design”  
  https://www.nngroup.com/articles/ten-usability-heuristics/
- Nielsen Norman Group, “Onboarding Tutorials vs. Contextual Help”  
  https://www.nngroup.com/articles/onboarding-tutorials/
- Interaction Design Foundation, “What are the Principles of Design?”  
  https://ixdf.org/literature/topics/design-principles
- Google Search Central, “Introduction to structured data markup in Google Search”  
  https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data

### Local artifact references examined as component examples
- `~/.openclaw/skills/clawdhub/SKILL.md`
- `~/.openclaw/skills/find-skills/SKILL.md`
- `~/.openclaw/workspace-main/SOUL.md`
- `~/.openclaw/workspace-main/AGENTS.md`
- `~/.openclaw/workspace-main/TOOLS.md`

---

## Appendix: Quick AX evaluation checklist

Use this to quickly assess whether a product is agent-ready.

### Discovery
- Can an agent find capabilities quickly?
- Are manifests, docs indexes, or registries available?

### Access
- Is auth delegated, scoped, and documented?
- Are approval boundaries explicit?

### Understanding
- Are schemas, examples, and task flows machine-readable?
- Is terminology stable and domain-aligned?

### Execution
- Are outputs structured and predictable?
- Are side effects and costs visible?

### Feedback
- Does the system expose progress and status?
- Are receipts, logs, or run IDs available?

### Recovery
- Are errors typed and actionable?
- Are retries, rollback, and escalation supported?

### Memory and continuity
- Can work be resumed?
- Is useful context persistable and retrievable?

### Trust
- Are provenance, maintenance, compatibility, and quality signals exposed?

### Governance
- Are safe and dangerous actions clearly separated?
- Is there an audit trail?

If the answer to most of these is no, the product may have APIs, but it does not yet have good AX.

## 16. Deeper UX Theory → AX Mapping

The first pass mapped classic usability heuristics into AX. That is useful, but not sufficient. UX is broader than heuristics. A mature AX discipline needs to translate perceptual psychology, cognitive psychology, interaction cost theory, and object-centered design into agent-facing systems.

The key move is this: humans experience interfaces through eyes, hands, attention, memory, and emotion. Agents experience systems through tokens, schemas, tool catalogs, error surfaces, context windows, authorization boundaries, and action loops. The substrate is different, but the design problems rhyme.

### 16.1 Gestalt principles for AX

Gestalt principles describe how humans perceive wholes, groupings, and patterns. For agents, the equivalent question is not visual grouping but semantic grouping. How does the agent infer what belongs together, what differs, what is missing, and what is foreground versus background?

#### 16.1.1 Proximity → semantic adjacency

In visual UX, objects placed near each other are perceived as related. In AX, “near” means:
- in the same JSON object
- in the same tool namespace
- in the same endpoint family
- in the same manifest section
- in the same example flow

Good AX uses semantic proximity so the agent can infer relationships without extra reasoning.

Example, good:
- `search`, `fetch`, and `list` tools grouped under a `documents` namespace
- auth scopes listed next to the tool or endpoint that needs them
- webhook event schema placed directly beside webhook registration docs

Example, bad:
- auth requirements documented on a separate page from the tool
- required follow-up endpoints hidden in a distant guide
- tools named inconsistently so related actions appear unrelated

AX implication:
If two capabilities must commonly be used together, place them together in docs, schema, and naming. The agent should not need to infer hidden adjacency from prose.

#### 16.1.2 Similarity → pattern consistency

Humans infer common function from similar shapes or colors. Agents infer common function from similar names, field shapes, and response contracts.

Good AX:
- all list endpoints use a common pagination pattern
- all write actions return a shared receipt envelope
- all errors share a common typed error object
- all destructive tools use the same approval flag

Bad AX:
- one endpoint paginates with `cursor`, another with `offset`, another with `pageToken`
- one delete tool returns 204, another returns `{success:true}`, another returns plain text
- tools with similar names hide different semantics

For agents, similarity lowers inference cost. It lets the model transfer successful patterns from one tool to another.

#### 16.1.3 Closure → inferable missing pieces

In human perception, closure means we complete incomplete forms. In AX, closure means the system lets the agent safely infer missing pieces.

Good AX supports closure when:
- response objects imply the next valid action
- item detail includes links or IDs needed for follow-up calls
- pagination responses include explicit `next_cursor`
- errors say what field is missing and show the expected shape

Bad AX breaks closure when:
- search results omit item IDs needed to fetch details
- tool results mention “use the other endpoint” without naming it
- errors say “invalid input” but not which field failed

A powerful AX pattern is intentional closure: provide enough structure that the agent can complete the workflow without guessing, but not so much that every step requires bespoke instruction.

#### 16.1.4 Figure-ground → signal versus noise

Humans distinguish a focal object from its background. Agents distinguish operative content from irrelevant text.

Good AX has a strong figure-ground relationship:
- schemas are distinct from marketing copy
- canonical examples are distinguished from narrative explanation
- tool descriptions state action, scope, side effects, and output in the first sentence
- docs provide llms.txt or concise machine-oriented references

Bad AX:
- long landing pages where the actual API surface is buried below branding language
- docs where examples are screenshots instead of text
- tool descriptions that start with positioning language instead of function

For agents, figure-ground is an information architecture problem. If the action surface is not foregrounded, the model spends tokens separating signal from brand noise.

### 16.2 Fitts’s Law for agents

Fitts’s Law in human-computer interaction says the time to acquire a target depends on distance and target size. For agents, we can reinterpret:

- Distance = number of reasoning steps, pages, tool calls, auth steps, or tokens required to reach a capability
- Target size = how explicitly and reliably the capability is exposed

An agent-facing Fitts equivalent might be:

**Agent acquisition cost = capability distance / affordance size**

Where capability distance can be approximated by:
- number of docs hops from discovery to execution
- number of fields required before first successful call
- number of dependent calls before meaningful output
- number of approvals needed
- token budget to understand the tool

And affordance size can be approximated by:
- clarity of tool name
- quality of description
- schema completeness
- examples provided
- discoverability in registries or manifests

Practical implication:
A tool hidden behind five docs pages and vague names is “far away” even if technically available. A clearly named tool with a typed schema and one example is “close.”

AX design pattern:
- reduce distance by providing concise discovery docs, working examples, and linked next steps
- increase target size by improving names, descriptions, argument schemas, and examples

### 16.3 Hick’s Law for agents

Hick’s Law says decision time increases with the number and complexity of choices. For agents, more tools are not automatically better.

An agent with 100 vaguely described tools often performs worse than one with 12 well-scoped tools.

Why:
- tool selection consumes context and reasoning budget
- overlapping tools create ambiguity
- ambiguous capability boundaries increase hallucinated tool use
- larger catalogs make failure recovery slower

Good AX for Hick’s Law:
- category structure
- namespaced tools
- recommended workflows
- deprecation of near-duplicates
- “start here” subsets for common tasks
- strong descriptions differentiating when to use one tool versus another

Bad AX:
- 100 tools in one flat list
- multiple synonyms for the same action
- tools named after internal service names rather than outcomes
- no indication of read-only versus write

A practical rule: every additional tool must justify its cognitive cost.

### 16.4 Jakob’s Law for agents

Jakob’s Law says users spend most of their time on other sites and expect your site to work similarly. Agents also build priors from previous systems.

Agent priors increasingly include:
- REST patterns like `GET /items`, `POST /items`
- JSON Schema and OpenAPI conventions
- OAuth and bearer token usage
- common CLI patterns like `--help`, `--json`, exit codes
- common tool selection semantics in OpenAI, Anthropic, MCP, and framework ecosystems

Good AX respects these priors unless there is a compelling reason not to.

Bad AX violations:
- using `GET` for destructive actions
- returning HTML from JSON endpoints without negotiation
- inventing custom auth headers without need
- giving tools abstract names like `performOperationX`

Agents do not love novelty. They love transferability.

### 16.5 Peak-End Rule for agents

Humans remember experiences largely by the most intense moment and the ending. Agents do not “feel” in the human sense, but the systems around them do accumulate reinforcement through conversation state, memory, retry loops, and human trust.

The AX version of Peak-End is:
- peak = the hardest point in the workflow, usually auth, failure, or side-effect confirmation
- end = the final receipt, summary, artifact, or unresolved error

If the hardest moment is confusing and the ending is ambiguous, the session is judged as poor by both the human and the orchestration layer.

Good AX endings:
- explicit success receipts with IDs and links
- concise summaries of what changed
- next recommended actions
- resumable state

Bad AX endings:
- silent success
- no durable reference to the action taken
- ambiguous partial completion

### 16.6 Progressive disclosure for agents

Progressive disclosure in UX reveals complexity only when needed. For agents, this is critical because context windows are finite.

Good AX progressive disclosure patterns:
- top-level docs show only core flows, with advanced options linked separately
- tool schemas make common fields required and advanced fields optional
- manifests provide a concise summary plus detailed references
- list endpoints return summaries, fetch endpoints return details
- errors give the minimum correction needed, then link to deeper guidance

Bad AX:
- every field and edge case documented before the happy path
- giant tool descriptions containing caveats, marketing, history, and auth details at once
- giant monolithic schemas with dozens of optional fields and no defaults

Agent-friendly systems layer information. They do not dump it all at once.

### 16.7 Cognitive load theory and context windows

Cognitive load theory distinguishes intrinsic load, extraneous load, and germane load. This maps almost perfectly to AX.

#### Intrinsic load
The irreducible complexity of the domain.
Examples:
- payment settlement flows
- OAuth device code flows
- distributed deployment state

#### Extraneous load
Complexity caused by bad presentation.
Examples:
- poorly structured docs
- duplicated terminology
- undocumented side effects
- inconsistent naming

#### Germane load
The useful effort spent building the right internal model.
Examples:
- learning a platform’s canonical workflow
- understanding approval semantics
- internalizing one consistent error format

Good AX cannot remove intrinsic load, but it can dramatically reduce extraneous load and make germane load worthwhile.

This matters because context windows are not just memory limits, they are budget constraints. Every unnecessary token spent on noise reduces room for planning and execution.

### 16.8 Don Norman’s Design of Everyday Things, translated to AX

Norman’s framework is especially powerful because it focuses on actionability.

#### 16.8.1 Affordances

An affordance is what actions are possible.
For agents, affordances are exposed through:
- tools and endpoints
- manifests and capabilities lists
- schemas and supported operations
- scopes and policies

Good AX affordances are explicit. The system says what can be done.
Bad AX hides affordances behind prose or unstated assumptions.

#### 16.8.2 Signifiers

Signifiers indicate how to use affordances.
For agents, signifiers are:
- names
- descriptions
- example calls
- schema field names
- status labels like `readOnly`, `dangerous`, `idempotent`

A tool exists without a good signifier is barely usable.

#### 16.8.3 Constraints

Constraints limit what can be done. For agents, constraints are good when explicit:
- required approvals
- auth scopes
- rate limits
- field validation
- environment restrictions

Hidden constraints are one of the worst AX failures because agents discover them only through failure.

#### 16.8.4 Mappings

Mappings describe the relationship between controls and outcomes.
For agents, mappings mean:
- fields correspond clearly to effects
- endpoint names correspond to domain actions
- input parameters map cleanly onto real-world concepts

Bad mapping example:
`mode=2` means “soft publish with delayed visibility” but nothing in the schema says so.

#### 16.8.5 Feedback

Feedback tells the user what happened.
For agents, feedback must be machine-usable:
- status objects
- receipts
- timestamps
- retry-after headers
- job IDs
- event streams

If an action takes time, feedback must include state transitions.

#### 16.8.6 Conceptual models

Humans succeed when they have a correct model of the system. Agents also need conceptual models, but these are built from docs, schemas, naming, and repeated outcomes.

Good AX provides a coherent conceptual model of:
- objects in the system
- valid state transitions
- who can act on what
- what actions are reversible
- how long things take
- how to recover

The best AX docs answer not only “what endpoint do I call?” but “what kind of world is this system?”

### 16.9 Synthesis

A mature UX-to-AX mapping suggests a simple principle:

**AX is the design of semantic legibility under bounded context.**

Humans need visual and interaction legibility. Agents need semantic and operational legibility. Everything else follows from that.

## 17. Comprehensive Component Analysis: The Building Blocks of AX

AX does not live in one place. It emerges from a stack of artifacts. A product may have a good API but terrible manifests. Great tool schemas but useless error objects. Nice CLI flags but no stable output mode. The real work is component-level.

For each component below, the central question is: can an agent discover, understand, trust, execute, and recover through this artifact?

### 17.1 Skill files

#### What they are
Skill files are reusable instruction artifacts that teach an agent how to perform a class of work or use a specific capability. Examples include OpenClaw `SKILL.md`, skills.sh packages, and project-local task files.

#### How agents interact with them
Agents read skill files as compressed operational guidance. They use them to:
- discover capabilities
- load workflows
- follow conventions
- avoid repeated reasoning
- align with project-specific patterns

#### Good skill files
- start with purpose and trigger conditions
- define inputs, outputs, and boundaries
- include canonical workflows
- include failure handling and escalation rules
- reference concrete files, commands, or tools
- keep instruction hierarchy explicit

#### Bad skill files
- vague aspirational prose
- no indication of when to use the skill
- no outputs or quality bar
- hidden assumptions about environment
- no examples

#### Real examples
OpenClaw-style skills are strong when they specify exact routing and output contracts. skills.sh is strong on packaging and distribution of skills, but the ecosystem still varies in metadata quality.

#### Proposed AX standard for skill files
Minimum fields:
- `name`
- `purpose`
- `when_to_use`
- `when_not_to_use`
- `required_context`
- `available_tools`
- `workflow`
- `success_criteria`
- `failure_modes`
- `examples`
- `version`
- `compatibility`

### 17.2 MCP servers

#### What they are
MCP servers expose tools, resources, prompts, and related capabilities over a standard protocol so clients like Claude, ChatGPT, Cursor, and custom apps can connect without bespoke integrations.

#### How agents interact with them
Agents discover MCP servers through configuration, registries, or provider integration. They then:
- enumerate tools/resources
- inspect schemas and metadata
- invoke tools or fetch resources
- receive typed content arrays
- sometimes negotiate auth and approvals

#### What makes a good MCP server
- clear tool names and descriptions
- stable input schemas
- read/write distinction
- low-friction auth
- narrow tool sets or good namespaces
- explicit metadata for safety and UI
- predictable result structure

#### What makes a bad MCP server
- giant unmanaged tool catalogs
- poor descriptions
- hidden side effects
- tool outputs that dump raw HTML or giant blobs
- auth flows that assume a browser even in non-interactive environments

#### Real examples from the wild
- Anthropic’s MCP framing is strong because it standardizes the connection model and encourages portability.
- OpenAI’s MCP integrations show a more opinionated compatibility layer, especially around read-only deep research patterns like `search` and `fetch`.
- Composio uses MCP as a distribution layer for large tool inventories with managed auth.

#### Proposed AX standard for MCP servers
- every tool must declare side-effect level: read, write, destructive
- every tool should include one good example input and output
- every server should expose a concise capabilities summary under a standard resource
- auth requirements should be machine-readable
- rate limits and approval semantics should be surfaced in metadata

### 17.3 CLI tools

#### What they are
Command-line interfaces remain one of the most important agent surfaces because coding agents and local automation systems use them constantly.

#### How agents interact with them
Agents inspect `--help`, run commands, parse stdout, observe exit codes, and sometimes stream stdin or respond interactively.

#### Good CLI characteristics for agents
- `--help` is complete and concise
- `--json` or equivalent machine output exists
- stable exit codes
- stderr reserved for errors and warnings
- deterministic output structure
- non-interactive mode available
- clear environment variable support
- dry-run mode for dangerous operations

#### Bad CLI characteristics
- help text missing examples
- colored prose dumped into stdout with no machine mode
- interactive prompts by default with no non-interactive override
- ambiguous exit codes
- progress noise mixed with result data

#### Real examples
Homebrew is strong on discoverability, naming, and conventions. Many modern CLIs still fail on JSON output or automation-safe prompts.

#### Proposed AX standard for CLIs
- MUST support `--help`
- SHOULD support `--json`
- SHOULD support `--yes` or explicit approval flags
- MUST document exit code meanings
- SHOULD separate human logs from machine output

### 17.4 REST APIs

#### What they are
HTTP APIs exposing resources and actions.

#### How agents interact with them
Agents use docs, OpenAPI, examples, and response behavior to compose requests and handle state transitions.

#### Good REST for agents
- consistent resource model
- idempotency where appropriate
- typed errors
- pagination and filtering conventions
- clear auth and scopes
- explicit rate limit headers
- webhook or async job support for long-running tasks
- stable versioning

#### Bad REST for agents
- custom semantics on common verbs
- inconsistent identifiers
- silent side effects
- text-only docs with no schema
- status code misuse

#### Proposed AX standard for REST
- publish OpenAPI plus concise agent summary docs
- expose idempotency support for write endpoints
- return operation receipts for side effects
- include standard async job envelope when work is deferred

### 17.5 GraphQL

#### What it is
A query language and runtime for APIs where the client specifies the response shape.

#### How agents interact with it
Agents can benefit from GraphQL introspection and targeted data retrieval, but only if the schema is discoverable and field naming is strong.

#### Better for agents when
- schema descriptions are excellent
- mutations are clearly named
- cost/complexity is visible
- examples show common query patterns
- introspection is accessible in development or mirrored into docs

#### Worse for agents when
- schema is huge and underdescribed
- field names are domain-jargon heavy
- mutations hide major side effects
- errors are generic and only appear in `errors[]`

GraphQL is not inherently better or worse for AX. It is more powerful but easier to make cognitively expensive.

#### Proposed AX standard for GraphQL
- every mutation includes side-effect annotation in docs
- common query templates published for agents
- query cost and pagination made explicit
- schema descriptions treated as first-class signifiers

### 17.6 Webhooks

#### What they are
Outbound event delivery to subscriber endpoints.

#### Good webhook AX
- signed payloads
- event versioning
- delivery IDs
- retry policy documented
- event ordering semantics documented
- test events available
- dead-letter or redelivery support

#### Bad webhook AX
- no signature
- no retry
- no idempotency guidance
- payload shape differs from docs
- event names too vague

souls.zip’s v2 docs are notable here because they reference Stripe webhook ingestion, retry state machines, admin reconcile endpoints, and cron-driven retry processing. That is strong AX because it treats event failure as a first-class operational reality rather than an afterthought.

### 17.7 SSE and WebSockets

#### What they are
Streaming transports for incremental data or bidirectional communication.

#### AX benefits
- progress visibility
- lower latency than polling
- richer state transitions
- better support for long-running tools or workflows

#### AX challenges
- reconnect semantics
- event schemas
- backpressure
- heartbeats
- ordering guarantees

#### Proposed standard
- every stream event has `type`, `timestamp`, `run_id`, `sequence`
- reconnect strategy documented
- terminal events defined explicitly
- equivalent polling fallback available

### 17.8 Documentation formats

#### What they are
README files, API docs, inline docs, llms.txt, reference sites, examples.

#### Good AX documentation
- concise overview
- llms.txt or doc index for machine ingestion
- examples in copyable text
- quickstart plus reference plus troubleshooting
- docs linked to schemas

Vercel AI SDK, CrewAI, LangChain, and MCP docs all now surface `llms.txt` style indexes. This is one of the clearest emergent AX norms: docs that are explicitly prepared for model ingestion.

#### Proposed standard
Every agent-facing product should ship:
- `llms.txt`
- concise quickstart
- API/schema reference
- troubleshooting guide
- changelog

### 17.9 Configuration files

YAML, JSON, and TOML each have AX tradeoffs.

#### YAML
Readable and expressive, but whitespace-sensitive and easy to misgenerate.
Good for high-level configs, task definitions, and multi-line prompts.

#### JSON
Strict and machine-friendly, but noisy for humans.
Good for schemas, manifests, and interchange.

#### TOML
Strong for package metadata and moderate human readability.
Good for manifests and tool config where nesting is limited.

#### AX guidance
- choose the format with the lowest error risk for the actual use case
- provide schema validation regardless of format
- include examples
- avoid custom mini-languages when a standard format works

### 17.10 Package manifests

`package.json`, `pyproject.toml`, brew formulae, Docker metadata, and similar manifests carry discovery and trust signals.

Homebrew formulae are strong examples of structured package metadata: homepage, license, dependencies, versioning, tests, and installation behavior are first-class. Docker Hub similarly benefits from repository descriptions, categories, tags, access controls, trusted content programs, and vulnerability scanning. These are not just package ecosystem details, they are AX signals.

Proposed manifest fields for agent ecosystems:
- name
- version
- description
- license
- homepage
- repository
- capabilities
- side-effect classification
- permissions required
- compatibility targets
- changelog URL
- maintenance status

### 17.11 Context files

Context files like `SOUL.md`, `AGENTS.md`, `TOOLS.md`, `MEMORY.md`, `AGENTS.md`, and `TOOLS.md` function as the operating system layer for long-lived agents.

#### Why they matter
They define identity, boundaries, delegation, procedures, and memory. For personal and organizational agents, these files often matter more than the underlying model prompt because they stabilize behavior over time.

#### Good context files
- explicit authority boundaries
- routing rules
- communication rules
- quality standards
- operational memory
- no contradiction between files

#### Bad context files
- bloated and repetitive
- stale instructions
- conflicting authority claims
- vague values with no operational translation

#### Proposed AX standard
Context files should be typed and layered:
- identity layer
- policy layer
- tool layer
- memory layer
- task layer

### 17.12 Prompt templates

Structured prompts outperform freeform prompts when repeatability matters.

Good prompt templates include:
- role
- objective
- available context
- constraints
- expected output format
- evaluation criteria
- escalation rule

Freeform prompts are useful for ideation. Structured prompts are better for reliable operations.

### 17.13 Schema files

JSON Schema and OpenAPI are among the most important AX artifacts because they provide typed conceptual models.

Good schemas:
- use descriptive field names
- constrain values where possible
- provide descriptions and examples
- encode enums instead of prose-only allowed values

Bad schemas:
- underdescribed fields
- `additionalProperties: true` everywhere
- giant unbounded strings where structure is known

### 17.14 Error objects

An agent-friendly error object should answer five questions:
1. what failed
2. why
3. where
4. whether retry is valid
5. what to do next

Recommended fields:
- `code`
- `message`
- `details`
- `field_errors`
- `retryable`
- `retry_after`
- `suggested_fix`
- `docs_url`
- `request_id`

### 17.15 Event payloads

Event payloads are the machine equivalent of notifications and status updates.

Good event payloads:
- stable event names
- resource identifiers
- actor info if relevant
- state transition
- timestamp
- dedupe key
- version

### 17.16 Agent cards and agent manifests

As agents begin to discover and coordinate with one another, they need self-descriptions.

An agent card or manifest should describe:
- identity
- operator
- capabilities
- tools available
- auth model
- memory policy
- approval policy
- preferred protocols
- latency profile
- cost profile
- trust/provenance signatures

This is the logical next layer beyond today’s tool manifests.

## 18. Platform Deep Dives

### 18.1 souls.zip v2 API

The `https://souls.zip/api/v2/docs` endpoint is itself an interesting AX artifact because it intentionally presents a lightweight, agent-first endpoint listing rather than a full OpenAPI document.

Notable strengths:
- unauthenticated discovery endpoints at `/api/v2` and `/api/v2/docs`
- explicit auth and rate-limit notes per endpoint
- clean separation of browse, auth, self-service, admin, cron, and webhook surfaces
- purchase-aware download behavior documented as returning a `402 payment response for unpaid items`
- creator API keys exposed as first-class self-service objects
- webhook retry and reconciliation modeled explicitly with cron and admin endpoints

This is unusually good AX because it recognizes that agents need a compact map before they need a full spec.

Weaknesses or opportunities:
- “not a full OpenAPI spec” means some tooling interoperability is sacrificed
- no inline request/response examples in the lightweight docs
- side-effect classifications could be made explicit
- canonical error object shapes are not visible in the lightweight listing

AX lesson:
A thin discovery doc plus a deeper typed spec is often better than only one or the other.

### 18.2 Anthropic MCP

Anthropic’s introduction frames MCP as a universal connector layer. This is strong AX because it reduces bespoke integration friction and encourages ecosystem portability.

AX strengths:
- standard mental model, “USB-C for AI apps”
- broad ecosystem support messaging
- clear emphasis on tools, resources, and workflows
- portability across clients and servers

Where MCP still needs maturity from an AX perspective:
- metadata conventions remain uneven across servers
- safety and side-effect annotations are not yet consistently enforced ecosystem-wide
- discovery quality depends on registries and individual server authors

### 18.3 OpenAI function calling, GPT Actions, and Apps/MCP

OpenAI’s function calling and GPT Actions are strong on schema-driven invocation. GPT Actions explicitly translate natural language into JSON inputs for RESTful APIs. The Apps and MCP stack adds richer UI and metadata layers.

Notable AX features:
- strong schema emphasis
- auth configuration as part of action setup
- model-mediated tool selection
- Apps SDK support for `structuredContent`, `content`, and `_meta`, separating model-visible from widget-only data
- visibility controls and UI metadata on tools

Important design signal:
OpenAI is effectively formalizing a three-layer AX surface: tool contract, structured result, and optional rendered interface.

### 18.4 Vercel AI SDK

The Vercel AI SDK is notable not just for model abstraction but for how overtly it designs for agents:
- unified APIs for text, structured objects, tool calls, and agents
- first-class docs for tools, streaming, MCP, middleware, memory, subagents, telemetry, and testing
- `llms.txt` support for machine-readable documentation

AX significance:
Vercel treats documentation, typing, and workflow ergonomics as one system. The docs index itself is agent-aware. That is a very strong AX signal.

### 18.5 LangChain and LangSmith

LangChain emphasizes fast agent creation, standard model interfaces, and integration breadth. LangSmith adds observability, evaluation, and deployment.

AX strengths:
- prebuilt abstractions
- durable execution via LangGraph under the hood
- strong observability and tracing story
- evaluation workflow integrated with development

AX lesson:
Observability is part of AX, not merely ops. Agents need environments where failures can be understood.

### 18.6 CrewAI

CrewAI’s task model is a good example of operational structure becoming an AX advantage. Task objects encode description, expected output, tools, context, async execution, human input, output files, JSON/Pydantic schemas, callbacks, and guardrails.

This is strong AX because the task artifact is both instruction and contract.

Weakness:
The framework can still produce very verbose configs, and YAML can become unwieldy at scale without strong tooling.

### 18.7 AutoGen

AutoGen is interesting because it splits concerns clearly:
- Studio for no-code prototyping
- AgentChat for conversational agent programming
- Core for event-driven multi-agent systems
- Extensions for integrations like MCP and Docker execution

AX lesson:
layered products can serve different agent builders if the boundaries are clear. AutoGen’s separation between prototyping and serious distributed systems is conceptually strong.

### 18.8 Composio

Composio’s main promise is reducing integration overhead across large tool inventories. It adds managed auth, toolkits, sessions, and MCP compatibility.

AX strengths:
- explicit provider examples for OpenAI and Anthropic
- user-specific generated MCP URLs
- dashboard and SDK flows
- strong concern for terminology migration and codegen correctness in docs

AX risks:
- very large catalogs increase Hick’s Law pressure
- the deprecation notice on Composio MCP is itself an AX event, migrations must be made extremely clear to avoid stale integrations

### 18.9 Smithery and Glama as registries

Even without exhaustive direct doc retrieval in this session, the role is clear. Registries are to agents what app stores and package indexes are to developers.

Glama’s public API output is notable because it exposes metadata such as:
- official author attribute
- remote-capable hosting attribute
- repository URL
- license
- environment variable schema

That is exactly the sort of machine-usable trust and compatibility metadata an AX ecosystem needs.

### 18.10 npm

npm is one of the strongest examples of ecosystem-scale discovery and packaging. Why it matters for AX:
- package naming conventions
- versioning
- README and metadata expectations
- installability via one standard command
- search and popularity signals
- dependency graphs

AX lesson:
Agent ecosystems need something like npm’s discoverability and package contract discipline, but with stronger safety and side-effect metadata.

### 18.11 Docker Hub

Docker Hub’s repository model is strong because tags, repository information, access controls, vulnerability scanning, webhooks, automated builds, and trusted content are all visible dimensions of trust and operability.

AX lesson:
Registries for agent tools should expose security scanning, provenance, and maintenance state as first-class filters, not hidden details.

### 18.12 Homebrew

Homebrew formulae are exceptional examples of structured packaging culture. The Formula Cookbook emphasizes:
- names
- homepage
- license
- dependencies
- tests
- auditability
- version discipline
- local and remote installation behavior

Homebrew succeeds because its ecosystem values consistency over novelty. That is a direct AX lesson.

## 19. Real-World AX Anti-Patterns

Below are concrete anti-patterns that repeatedly damage agent success.

### 19.1 The pretty website, useless API problem
Beautiful landing page, weak or absent machine interface. Great for humans browsing, terrible for agents acting.

### 19.2 The documentation-is-a-PDF problem
Critical docs only available as PDFs or slide decks. Agents can sometimes parse them, but reliability and navigability collapse.

### 19.3 The auth-flow-requires-a-browser problem
No device code, token exchange, or service auth path. Works for humans, blocks headless agents.

### 19.4 The “something went wrong” error
Generic failure message with no typed code, no field, no retry guidance.

### 19.5 Rate limits without `Retry-After`
The agent knows it failed, but not when to resume.

### 19.6 Breaking changes without versioning
The agent cannot build a stable conceptual model because the ground moves invisibly.

### 19.7 Tool descriptions written as marketing copy
The first sentence sells instead of explaining. The model cannot infer usage boundaries.

### 19.8 100 tools, no categories
Classic Hick’s Law failure.

### 19.9 Webhooks with no signature or retry semantics
Event delivery becomes untrustworthy and non-operational.

### 19.10 Required fields hidden in prose
Schema says optional, docs say required “for some cases.” Agents fail at runtime.

### 19.11 IDs not returned after creation
A write succeeds but no resource identifier is returned, preventing follow-up operations.

### 19.12 Human-only terminology drift
Docs, SDK, and UI use different nouns for the same object.

### 19.13 Async operations with no job endpoint
The API says “processing,” but gives no run ID or status route.

### 19.14 Read endpoints with hidden side effects
A “fetch” call triggers billing, indexing, or notifications.

### 19.15 Write tools misclassified as read-only
A severe safety failure in agent platforms.

### 19.16 Screenshots instead of copyable examples
Looks nice, impossible to execute.

### 19.17 No non-interactive CLI mode
The agent hangs on a prompt it cannot answer.

### 19.18 Inconsistent pagination
Every resource family reinvents list traversal.

### 19.19 Event payloads without version numbers
Consumers cannot reason about compatibility.

### 19.20 Silent partial success
A batch action partly fails but returns generic 200.

### 19.21 No idempotency for retried writes
Network retries create duplicates.

### 19.22 Giant monolithic prompts as integration surface
The “API” is really a long prompt pasted into an LLM, with no typing or operational contract.

### 19.23 OAuth scopes explained only in the UI
The agent cannot plan or request least privilege.

### 19.24 Logs that cannot be correlated
No request IDs, run IDs, or event IDs.

### 19.25 Changelogs written for marketers, not integrators
Important compatibility breaks are buried.

## 20. AX for Different Agent Types

### 20.1 Coding agents
Coding agents need:
- filesystem-safe operations
- deterministic CLIs
- diffable outputs
- test hooks
- build logs
- approval semantics for dangerous actions
- resumable long-running tasks

### 20.2 Chat agents
Chat agents need:
- concise tool descriptions
- schema-guided tool selection
- strong follow-up question behavior
- low token overhead for onboarding
- user-visible receipts and explanations

### 20.3 Autonomous agents
Background agents need:
- unattended auth refresh
- retry contracts
- observability
- dead-letter handling
- rate-limit transparency
- idempotent writes
- stable schedules and eventing

### 20.4 Multi-agent systems
Teams of agents need:
- task routing metadata
- delegation contracts
- shared state references
- anti-conflict controls
- per-agent permissions
- message schemas
- provenance of who did what

### 20.5 Specialist agents
Specialists need deep but narrow AX:
- domain-specific vocabulary
- focused tool sets
- rich examples
- high-quality context artifacts
- reliable evaluation criteria

### 20.6 Personal agents
Long-lived personal agents need:
- identity continuity
- memory boundaries
- preference systems
- trust and approval history
- durable context files
- explicit delegation and communication norms

## 21. AX Metrics and Measurement

AX must be measurable or it remains a vibe. Below are concrete metrics.

1. **Time-to-first-action** - seconds from discovery to first successful tool call.
2. **Time-to-first-success** - seconds to complete the first meaningful workflow.
3. **Context onboarding cost** - tokens required to understand the system well enough to act.
4. **Discovery friction** - number of hops to find the right capability.
5. **Capability precision** - percent of times the agent selects the correct tool first.
6. **Schema completeness score** - percent of fields with descriptions, examples, and constraints.
7. **Auth friction index** - number of steps or user interrupts needed for usable auth.
8. **Approval interruption rate** - how often execution pauses for confirmation.
9. **Error recovery rate** - percent of failures self-recovered without human help.
10. **Retry safety score** - percent of retried writes that remain duplicate-safe.
11. **Event reliability score** - delivered versus dropped or duplicated events.
12. **Documentation compression ratio** - useful operational knowledge divided by total doc tokens.
13. **Tool catalog entropy** - measure of overlap and ambiguity in tool inventory.
14. **Output parse reliability** - percent of results successfully machine-parsed on first try.
15. **Version stability score** - frequency of breaking changes per quarter.
16. **Observability coverage** - percent of actions with trace IDs, receipts, or logs.
17. **Resumability score** - percent of interrupted workflows successfully resumed.
18. **Trust signal availability** - percent of capabilities carrying provenance, maintenance, and permission metadata.
19. **Latency transparency** - percent of long-running actions that report progress and ETA or status.
20. **Human escalation rate** - percent of sessions requiring human intervention.

These can be benchmarked per platform, per workflow, or per tool.

## 22. The AX Stack

AX needs a layered architecture so teams can reason about what they are improving.

### 22.1 Proposed layers

1. **Transport layer**
   - HTTP, stdio, SSE, WebSockets, JSON-RPC
2. **Protocol layer**
   - REST, GraphQL, MCP, webhook signatures, OAuth
3. **Schema layer**
   - JSON Schema, OpenAPI, typed events, typed errors
4. **Capability layer**
   - tools, endpoints, resources, prompts, commands
5. **Context layer**
   - docs, llms.txt, manifests, context files, examples
6. **Execution layer**
   - approvals, retries, jobs, idempotency, progress
7. **Memory layer**
   - checkpoints, summaries, resumability, preferences
8. **Trust layer**
   - provenance, signatures, ratings, maintenance, scanning
9. **Coordination layer**
   - delegation, multi-agent messaging, role boundaries
10. **Governance layer**
   - policy, permissions, audit, escalation, compliance

### 22.2 How they compose

A tool cannot have good AX if its schema is weak, even if the transport is solid. A registry cannot deliver good AX without trust metadata. A personal agent cannot be durable without memory and governance layers.

### 22.3 Existing standards by layer

- Transport: HTTP, stdio, SSE, WebSockets
- Protocol: MCP, REST, GraphQL, OAuth
- Schema: JSON Schema, OpenAPI, AsyncAPI
- Trust: SPDX, sigstore-style provenance, vulnerability scanning programs
- Coordination: still immature, opportunity for new standards

## 23. Case Studies

### 23.1 souls.zip v2 API

**Overall grade: A- for early agent-first intent**

Strong:
- explicit discovery endpoint
- auth and rate-limit notes
- purchase-aware download semantics
- operational treatment of webhooks and retries

Weak:
- lightweight docs lack full typed examples
- no visible universal error schema in the compact listing

### 23.2 OpenAI Apps/MCP

**Overall grade: A for structured tool and UI composition**

Strong:
- clear separation of model-visible versus widget-only data
- tool metadata tied to UI
- support for structured content
- thought given to approvals and retries

Weak:
- complexity rises quickly when combining apps, UI, auth, and MCP
- still somewhat ecosystem-specific despite MCP compatibility claims

### 23.3 Vercel AI SDK

**Overall grade: A- for developer-facing AX infrastructure**

Strong:
- documentation explicitly prepared for LLM ingestion
- tools, streaming, MCP, memory, and telemetry are first-class topics
- unified API surface reduces provider-specific friction

Weak:
- primarily a builder framework, not a marketplace, so discovery is less central than in registries

### 23.4 Docker Hub

**Overall grade: B+ for registry trust and metadata**

Strong:
- repository info, tags, categories, access, scanning, trusted content
- clear versioning and discoverability patterns

Weak:
- not built for LLM agents specifically, so agent-ready machine summaries are limited

### 23.5 Homebrew

**Overall grade: A- for packaging discipline**

Strong:
- predictable names and install flow
- rigorous metadata norms
- strong audit and test culture

Weak:
- some docs still assume human package maintainers more than autonomous agents

## 24. AX vs DX vs UX Comparison Matrix

| Concern | UX approach | DX approach | AX approach |
|---|---|---|---|
| Discovery | Navigation menus, search, labels | docs, package indexes | registries, manifests, tool catalogs |
| Onboarding | tutorials, walkthroughs | quickstarts | compact machine-readable quickstarts |
| Affordance | buttons, controls | API methods, CLI commands | tool descriptors, schemas, manifests |
| Feedback | loaders, toasts, confirmation | logs, responses | receipts, events, structured progress |
| Error handling | empathetic messages | stack traces, codes | typed errors plus recovery guidance |
| Trust | branding, privacy notices | ecosystem reputation | provenance, scopes, safety metadata |
| Memory | personalization | saved config | durable context, checkpoints, preferences |
| Accessibility | WCAG, contrast, keyboard | ergonomic APIs | low-context legibility, typed outputs |
| Consistency | design systems | SDK conventions | naming, schema, output contract consistency |
| Navigation | IA, menus | package/module structure | capability hierarchies, namespaces |
| Latency | skeleton UI, spinners | async APIs | progress streams, job IDs |
| Safety | confirmations, undo | guardrails, validations | approval policies, side-effect classes |
| Learning curve | progressive disclosure | tutorials/examples | layered docs plus examples and schemas |
| Recovery | undo, retry | retry logic, docs | retryable errors, idempotency, resumability |
| Identity | profiles/accounts | auth credentials | agent manifests, delegated identity |
| Coordination | collaboration UI | webhooks, queues | inter-agent contracts and task routing |
| Versioning | user-facing release notes | semver, changelogs | machine-usable compatibility signals |
| Observability | analytics | traces, logs | trace IDs, run IDs, action histories |
| Governance | permissions UI | IAM policies | approval contracts and audit trails |
| Personalization | preferences | config files | memory-aware defaults and preference schemas |

## 25. Future AX Patterns That Do Not Fully Exist Yet

### 25.1 Agent app stores
Not just tool listings, but installability, permissions, ratings, compatibility, sandboxing, and revocation.

### 25.2 Agent-to-agent marketplaces
Agents offering specialized capabilities to other agents under clear contracts and pricing.

### 25.3 Agent reputation networks
Portable trust derived from reliability, safety incidents, maintenance history, and operator identity.

### 25.4 Capability negotiation protocols
Before invoking a capability, agents should be able to ask: what can you do, at what latency, with what permissions, in what format?

### 25.5 Preference systems
Agents need portable user preference layers beyond today’s scattered memory fields.

### 25.6 Universal agent identity
A portable identity layer for agents acting across tools, with clear delegation from humans and organizations.

### 25.7 AX benchmark suites
Public benchmarks measuring discovery, error recovery, tooling ambiguity, and context efficiency.

### 25.8 Side-effect labeling standards
Universal labels for read, write, financial, destructive, external-message, and privileged actions.

### 25.9 Resumable workflow protocols
Standard ways to checkpoint, suspend, and resume work across clients and systems.

### 25.10 Agent preference and memory exchange
A standard way for a user’s preferred tone, risk tolerance, and recurring defaults to travel safely across systems.

## 26. Final Expansion Synthesis

The deeper we go, the clearer the pattern becomes: AX is not a niche add-on to APIs. It is the next major interface discipline.

UX taught us to respect human cognition.
DX taught us to respect developer workflows.
AX must teach us to respect machine cognition operating under limited context, partial autonomy, safety constraints, and delegated human trust.

The practical consequences are immediate:
- docs need machine-friendly layers
- tools need clearer metadata
- registries need trust signals
- events need operational semantics
- errors need recovery contracts
- long-lived agents need identity, memory, and governance artifacts

The strategic consequence is larger:
Products that are easiest for agents to use will increasingly become the default choices in agent-mediated markets. Discovery, adoption, and execution will route through the systems with the best AX.

That means AX is not just an implementation detail. It is distribution, retention, reliability, and trust.

