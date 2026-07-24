<h1 align="center">Cells as the Containment Unit for Agentic Systems</h1>
<h3 align="center">Applying cell-based architecture to governed, secure, and reusable agentic systems</h3>
<p align="center">
  <i>
    Version: Summer-2026<br/>
    <b>First Published On: Summer-2026</b>
  </i>
</p>

***Authors***

* [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO \- [WSO2, LLC](https://wso2.com/) | [@asankama](https://twitter.com/asankama)  
* [Ayesha Dissanayaka](https://www.linkedin.com/in/ayeshadissanayaka/) | Associate Director & Architect \- [WSO2, LLC](https://wso2.com/)  
* [Erandi Ganepola](https://www.linkedin.com/in/erandiganepola/) | Solutions Architecture | Technology Evangelist | [WSO2, LLC](https://wso2.com/)  
* [Senthalan Kanagalingam](https://www.linkedin.com/in/senthalank/) | Technical Lead | IAM Specialist | [WSO2, LLC](https://wso2.com/)

> *Enterprises are moving AI agents from pilots into production, introducing a new architectural challenge. Traditional enterprise systems were designed around predictable consumers such as web applications, mobile applications, backend services, event consumers, and partner integrations. These consumers usually interact with well-defined interfaces in expected ways. Agents change this model. They are probabilistic, make runtime decisions, and can choose tools, data sources, downstream agents, and action sequences based on user intent, prompts, skills, model behavior, and runtime feedback.*
>
> *This makes agents powerful, but it also introduces risks around ownership, trust, cost, observability, and control. Without architectural containment, agents can blur ownership, duplicate business logic, accumulate excessive permissions, cross domain boundaries without proper authorization, expose sensitive data, trigger unintended actions, and consume unbounded model or tool resources.*
>
> *This paper presents [Cell-Based Architecture](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) (CBA) as the runtime boundary for agentic systems in both greenfield and brownfield environments. A cell becomes the containment unit for agents, domain services, tools, skills, reusable capabilities, memory, knowledge sources, identity bindings, policies, gateways, and observability. By treating each cell as a trust boundary and a capability boundary, enterprises can introduce agentic capabilities incrementally while preserving domain ownership, least privilege, composability, auditability, and operational control.*

## 1\. Introduction

![Agentic access over existing and new enterprise capabilities](/media/media_agentic_systems/introduction.png)
<p align="center"><em>Agentic access over existing and new enterprise capabilities</em></p>

Enterprise architects have long organized distributed systems around systems of record, domain services, APIs, events, integrations, and user-facing applications. Patterns such as microservices, event-driven architecture, zero trust, API management, and platform engineering have helped make these systems modular, composable, secure, and observable.

The agentic era changes the interaction model. AI agents can now act as enterprise consumers and enterprise actors. They can use tools and skills, query data, summarize knowledge, invoke workflows, request approvals, and collaborate with other agents. Protocols such as [Model Context Protocol](https://modelcontextprotocol.io/docs/getting-started/intro) (MCP) and [Agent to Agent](https://a2a-protocol.org/latest/) (A2A) add new ways for agents to access enterprise capabilities. However, they do not replace existing domain ownership, system boundaries, or operational controls.

A business capability does not change just because an agent becomes a new consumer. For example, in an enterprise HR system, the Employee Profile capability still owns employee profile data whether the request comes from a REST API, an event consumer, an MCP tool invocation, or an HR agent. If the agentic interface bypasses the existing boundary of that capability, the architecture fragments. If it is added through the boundary, ownership, policies, contracts, and observability remain intact.

Most enterprises will not introduce agents into a clean-slate architecture. They will add them to brownfield systems that already contain APIs, services, systems of record, identity systems, integration layers, gateways, policies, and operational controls. The architectural question is therefore not only how to expose enterprise capabilities to agents, but how to do so without weakening ownership, least privilege, policy enforcement, auditability, and operational control.

[Cell-Based Architecture (CBA)](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) provides that runtime boundary. It allows agents to become new consumers and actors while preserving the existing ownership, contracts, security controls, and observability of the enterprise architecture.

## 2\. Why agentic systems need architectural containment

Agentic systems need containment because agents introduce autonomy into systems designed for predictable interactions. An API client usually follows a known path, but an agent may choose different tools, data sources, workflows, or downstream agents based on prompt context, intermediate results, model behavior, and prior conversation state. That flexibility is valuable for productivity and enhanced outputs, but it must be constrained by architecture.

Containment is more than sandboxing a process. It defines what an agent can see, call, change, access, spend, and delegate, and who owns the outcome. This boundary must apply consistently across development, testing, staging, and production.

Without clear architectural containment, several risks appear:

* **Ownership becomes ambiguous:** A single agentic task can cross multiple domains, tools, systems, and data sources, making it unclear who owns the agent, tool, data, and authorization boundary.  
* **Permissions can sprawl:** Agents are often granted broad access during pilots. In production, this becomes risky. An HR agent that only needs an employee’s role and reporting line should not be able to modify payroll records or access sensitive benefits data.  
* **Business logic can be duplicated:** The same capability may be exposed separately through APIs, events, MCP tools, prompts, or skills. This can create inconsistent behavior when the agent-facing implementation does not reuse the domain services that already own the business logic.  
* **Inter-cell trust risk increases:** Agents may call tools, delegate tasks, or invoke systems across domains. Without user identity, agent identity, delegation context, and requested scope, downstream cells cannot make reliable authorization decisions.  
* **Cost and operational risk increase:** Agents can loop, retry, invoke expensive models, or call tools repeatedly. They need token budgets, tool budgets, rate limits, and task-level controls.  
* **Auditability becomes harder:** Enterprises must know who called what, on whose behalf, with which permissions, against which data, through which tool, at what cost, and with what result.

Architectural containment makes the boundary explicit and enforceable. It provides a place to apply identity, authorization, policy, observability, cost control, data access rules, tool governance, and operational ownership.

## 3\. Domain-Driven Design as the design principle for boundaries

Domain-Driven Design (DDD) is an approach to software design and development that places the business domain at the center of the system. It focuses on building a domain model that captures the key processes, rules, language, and behaviors of a specific business area. The term was popularized by **Eric Evans in his 2003 book**, which introduced a catalog of patterns for applying this approach in complex software systems. **Vaughn Vernon** made DDD pragmatic and, as an industry practice, based on the books and thought leadership content he published.

For agentic systems, DDD is important because agents can call tools, access data, invoke workflows, and delegate tasks across domains. Without clear domain boundaries, agents can blur ownership, duplicate logic, bypass controls, or act on capabilities they should not own.

The key DDD concept for this paper is the **bounded context,** which defines where a domain model, its terms, rules, data, and behaviors are valid. For example, an "employee in an organization" may mean different things in Employee Profile, Payroll, Benefits, Recruitment, and Learning and Development contexts. DDD helps keep these meanings separate and assigns clear ownership to each domain.

For agentic architecture, DDD helps architects decide which business capability an agentic interaction belongs to, which team owns it, which data and tools are valid, which actions are allowed, and which downstream domains can be called. However, DDD identifies the boundary, it does not enforce it at runtime.

That is where Cell-Based Architecture (CBA) becomes important. **DDD defines the domain boundary, while CBA turns that boundary into a deployable, governable, observable, and secure runtime unit**.

## 4\. Cell-Based Architecture as the runtime boundary for agentic systems

![Anatomy of a cell](/media/media_agentic_systems/anatomy-of-a-cell.png)
<p align="center"><em>Anatomy of a cell</em></p>

Cell-Based Architecture (CBA) operationalizes the boundaries identified through Domain-Driven Design. If DDD helps architects decide where a boundary should exist, CBA provides a concrete way to implement that boundary in the enterprise architecture. 

In CBA, a cell is a collection of components grouped from design and implementation into deployment. A cell is independently deployable, manageable, and observable. It contains the components required to deliver a business or technical capability, and exposes that capability through governed interfaces. Components inside the cell can communicate through supported internal transports, while external and inter-cell communication must happen through cell gateways, proxies, or other controlled endpoints.

Please refer to the original paper of [Cell-Based Architecture (CBA)](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) for detailed information.

### 4.1. Anatomy of an agentic cell

![Anatomy of an agentic cell](/media/media_agentic_systems/anatomy-of-an-agentic-cell.png)
<p align="center"><em>Anatomy of an agentic cell</em></p>

For agentic systems, CBA is a natural fit. Agents need access to business capabilities, tools, data, memory, workflows, and other agents. Without a runtime boundary, those interactions become difficult to govern. The cell provides that boundary. It contains the agentic workload and controls how that workload interacts with the rest of the enterprise.

This does not mean every cell must host an agent. A cell may expose tools consumed by agents in other cells. Another cell may host an agent that orchestrates work inside its own domain. A shared capability cell may expose reusable capabilities such as document summarization, policy validation, customer identity verification, translation, notification delivery, or enterprise search.

The important architectural rule is that every capability has an owner, and every external interaction crosses a governed boundary. This prevents agentic interfaces from becoming a separate architecture.

For example, if the Employee Profile Cell already exposes employee APIs and events, adding an MCP server should not create a separate employee data implementation for agents. The MCP server should expose agent-friendly tools that delegate to the same domain services through the cell boundary. If an HR agent needs payroll or benefits information, that interaction should cross into the Payroll Cell or Benefits Cell through governed interfaces, where each cell applies its own policies, validates identity and delegation context, and decides whether the action is allowed.

With respect to an AI agent, a cell can be organized into the following layers:

* **Domain capability layer:** Domain services, integrations, APIs, events, and data access logic that implement the business capability owned by the cell. For example, the Employee Profile Cell owns employee profile data and related operations.  
* **Agent runtime layer:** The agent runtime, prompts, skills, plans, and domain-specific behavior that allow the agent to operate within the cell’s scope.  
* **Tool and skill layer:** MCP servers, tool adapters, skills, and reusable functions exposed to the agent through governed contracts, schemas, permissions, and rate limits.  
* **Knowledge and memory layer:** Domain-scoped memory, vector stores, document indexes, retrieval sources, and other knowledge assets the agent can use.  
* **Policy and trust layer:** Identity bindings, authorization rules, delegation context, data access policies, guardrails, and approval rules that decide what the agent is allowed to do.  
* **Sandbox and execution layer:** Sandboxed environments for code execution, browser actions, file access, workflow execution, and other agent-operated tasks.  
* **Gateway and control layer:** Cell gateways or proxies that enforce authentication, authorization, routing, throttling, cost controls, and inter-cell communication policies.  
* **Observability and audit layer:** Logs, traces, audit records, evaluation results, and cost telemetry for agent actions, tool calls, model interactions, and boundary crossings.

This structure makes the cell the containment unit for the AI agent. The agent can reason and act, but only through the capabilities, tools, data, policies, and gateways controlled by the cell.

### 4.2. Cells as trust boundaries for agents

![Cells as trust boundaries for agentic systems](/media/media_agentic_systems/trust-boundaries.png)
<p align="center"><em>Cells as trust boundaries for agentic systems</em></p>

An agentic cell is a trust boundary. It defines which agents, users, tools, systems, and data sources are trusted for a given domain, and under which conditions that trust is valid. Trust is not assumed because a caller is internal. Trust is established at the boundary through identity, authorization, policy, and runtime context.

Agentic workflows are more complex than traditional application calls. A user may authorize a client, the client may delegate to an agent, that agent may delegate a subtask to another agent, and the second agent may invoke a tool or external API. The downstream cell must understand the delegation chain well enough to decide whether the action is allowed. The implementation details are discussed later in the “**Security boundaries: identity, delegation and policy**” section.

For production use, every trust boundary should produce a reliable audit trail. The enterprise should be able to inspect agent activity by cell, user, agent, tool, data source, policy decision, model invocation, and cost. This makes the cell not only a runtime boundary, but also an accountability boundary.

### 4.3. Cells as capability boundaries for tools and reusable components

![Cells as capability boundaries](/media/media_agentic_systems/cells-as-capability-boundaries.png)
<p align="center"><em>Cells as capability boundaries</em></p>

Cells also act as capability boundaries. A cell owns a specific business or technical capability and exposes it through versioned, governed interfaces. This is important for agentic systems because agents consume enterprise capabilities through tools, skills, APIs, events, and other agents.

The key principle is that a capability should remain with the cell that owns the domain. If the Employee Profile Cell owns employee data, role information, reporting lines, and employment status, then agent-facing tools for those capabilities should be exposed by the Employee Profile Cell or delegate to services inside that cell. The enterprise should not create a separate HR agent tool that reimplements employee profile logic outside the owning domain.

This preserves consistency across consumer types. A web application, mobile application, partner API, event workflow, MCP tool, and agent all reach the same domain capability through governed interfaces. The cell remains the source of truth for the business operation, policy enforcement, data ownership, and lifecycle.

Reusable capabilities should also be organized as cells, not as an unbounded central tool hub. A central tool hub may look convenient at first, but it can become a tool monolith. It concentrates permissions, weakens ownership, creates a single point of failure, and makes it hard to determine which team is responsible for a tool’s correctness, security, cost, and lifecycle.

A better pattern is the capability cell. A capability cell owns a reusable capability that multiple domain cells can consume through governed interfaces. Examples include:

* Policy and compliance checks.  
* Document summarization.  
* Translation.  
* Notification delivery.  
* Customer identity verification.  
* Enterprise search.

Each capability cell should have a clear owner, versioned contracts, access policies, rate limits, cost controls, observability, and lifecycle management. Domain cells consume these capabilities through inter-cell communication, just as they would consume any other cell-owned capability.

Tool contracts are central to this model. An agent-facing tool should not be just a function description. It should be a governed contract. MCP servers can expose these tool contracts to agents, but the cell boundary determines which tools are available, under which identity, and with which policies. The tool catalog therefore needs to be policy-aware, not merely discoverable.

The capability boundary also protects data ownership. Agents should not bypass the owning cell to query databases, vector indexes, object stores, or internal services directly. If a knowledge source is domain-specific, it belongs inside or behind the owning cell’s boundary. If a knowledge source is shared, it should be governed as a capability cell with explicit access policies.

### 4.4. Sandboxing as runtime isolation inside the cell

![Sandboxing inside the agentic cell](/media/media_agentic_systems/sandboxing-inside-the-agentic-cell.png)

<p align="center"><em>Sandboxing inside the agentic cell</em></p>

Sandboxing is runtime isolation for agentic execution. It limits what an agent, tool, code interpreter, browser session, workflow action, or delegated subtask can do inside a cell. This matters because agents do not follow a fixed execution path. They can reason over context, select tools, call APIs, access memory, read documents, invoke workflows, write files, generate code, or delegate work to other agents.

In agentic systems, sandboxing is broader than isolating code execution. An agent can cause harm without running malicious code. It may call the wrong tool, read the wrong data, update the wrong record, invoke an expensive model repeatedly, or leak sensitive information to an external service.

An agentic sandbox should define limits across:

* **Compute:** where the agent, tool, or generated code runs.  
* **Network:** which internal services, external APIs, SaaS endpoints, model providers, or internet destinations it can reach.  
* **Data and files:** which databases, documents, vector indexes, memory stores, files, and workspaces it can access.  
* **Tools and actions:** which tools it can invoke, which operations are read-only or state changing, and which require human approval.  
* **Identity and cost:** which identity and delegated scopes apply, and how many model calls, tokens, tool invocations, or retries are allowed.

The cell is the right place to define and enforce these rules because it owns the domain context. For example, an HR agent may be allowed to summarize an employee policy or search approved HR knowledge, but not modify payroll records, access sensitive benefits data, or send a formal employee notification without approval.

Sandboxing is part of containment, not a replacement for it. The sandbox constrains execution. The cell constrains ownership, trust, data access, tool access, policy, observability, and accountability.

## 5\. Security boundaries: identity, delegation and policy

An agent's behavior cannot be enumerated in advance the way a service's code paths can: it selects from a growing tool surface and decides what to do at runtime. This raises two questions: where the security boundary sits around an actor that is mutable, and what that boundary must enforce.

![Cell boundary and its crossings](/media/media_agentic_systems/cell-boundary-and-crossings.png)
<p align="center"><em>Cell boundary and its crossings</em></p>

The cell answers the first. The boundary is the cell edge: every crossing passes through a gateway, and nothing reaches or leaves the interior any other way. A cell may run a distinct gateway per direction, northbound, southbound, eastbound, and westbound, extending the reference architecture's north-south/east-west convention into four separately enforceable edges.

### 5.1 The cell edge as a zero trust boundary

Zero trust grants no request standing based on origin: every request is authenticated, authorized, and scoped to least privilege, on the assumption that some component is already compromised. Perimeter security does not fit an agent, because the most dangerous caller is not outside the perimeter but the agent inside it, acting on a plan an attacker may have influenced through a poisoned document or a crafted tool response.

* **No implicit trust across the edge.** The cell interior is a distinct trust domain. A caller reaching the gateway inherits no standing inside the cell; the gateway re-establishes it as a cell-internal identity scoped to the request, the internal representation of whichever identity crossed at ingress, user or cell.  
* **Verification on every crossing.** Identity is verified inbound and privilege is re-established outbound, on every crossing, including agent-to-agent calls with no human in the path.  
* **Least privilege per hop.** The runtime holds no durable credential. The gateway issues short-lived, narrowly scoped credentials per hop, so privilege follows what is acting and what it is attempting, not who logged in.  
* **Assume breach, bound blast radius.** A hijacked plan is bounded by the tools, data, and identity scope granted to that one cell; the gateway is the last enforceable line before anything leaves.

### 5.2 The identities and why each matters

The **user** is the human or upstream system that initiated the request. Issued by the enterprise identity provider, it arrives northbound as a user token or westbound inside a delegation from another cell, and is required at audit so every action traces to its originator.

The **agent identity** is the runtime identity the agent holds independent of any user or container. It is a first-class managed identity, provisioned, rotated, and deprovisioned by the enterprise identity provider or a token service local to the cell on its own lifecycle rather than tied to a deployment. It is required at authorization: a tool decision turns on which agent is calling as much as on which user it acts for.

The **on-behalf-of identity** is what the agent presents downstream, built from the identity of the caller to the cell (representing the user or the delegating cell) and the agent's own identity. It is a scoped, short-lived assertion carrying only what one action needs: who is acting, on whose authority, and the declared intent, the specific action being attempted rather than the general capability to attempt it. It is established at each egress crossing, at the gateway, whenever the agent acts on behalf of another party rather than purely under its own agent identity.

An agent acting as the user is impersonation: it assumes the user's identity outright, exposing a fully privileged session to every tool and leaving nothing to distinguish the agent's actions from the user's own. An agent acting only as itself, with no reference to the user at all, breaks the audit link back to the user. Delegation is the alternative to both: the agent keeps its own identity and acts under it, but carries the user's authority forward explicitly, as the on-behalf-of identity, rather than assuming that authority as its own. Resolving all three at the gateway is what answers "who is acting, on whose authority, for what purpose" at every point it is asked.

### 5.3 Transporting identity and the actor chain

This applies whenever an agent acts on behalf of another party, the user or a delegating cell, rather than purely under its own agent identity. In these cases, two properties hold at every such crossing, independent of mechanism: identity is re-established for the next hop rather than passed through, what enters is reduced to the caller's identity and what leaves is scoped to an on-behalf-of identity for its destination, and the request carries an actor chain, so authorization and audit see every party behind it, not only the immediate caller.

Re-establishing identity at each hop keeps the runtime free of long-lived, high-privilege credentials: it requests a specific call, and a narrow, short-lived credential is established for that call alone. OAuth 2.0 Token Exchange (RFC 8693\) is one way to realize it, typically via its `act` claim for the acting party and `may_act` to constrain delegation, but the requirement holds under any scheme.

The actor chain makes delegation auditable by appending an actor at each hop rather than replacing the caller, so a downstream tool sees, for example, user U via triage agent A via action agent B.

### 5.4 Securing the inter-cell transports

What distinguishes the paths across a cell's edge is not the mechanics of enforcement, applied per edge below, but the security burden each carries.

**User to agent (northbound).** The caller sits outside the cell's trust domain, so every request is potentially adversarial, whether a payload crafted to attack the runtime or content meant to steer the agent's plan. This is also where the user's identity is established, starting the actor chain.

**Agent to external tool (southbound).** Third-party APIs, SaaS endpoints, and external MCP tool servers leave the enterprise trust boundary, carrying the highest exfiltration risk and the fullest egress policy.

**Agent to internal tool (eastbound).** Internal tools stay within the enterprise trust boundary, so exfiltration to a third party is not the primary risk, but internal reach is not implicit trust: scope narrowing, authorization, and the actor chain still apply. When the tool is itself a cell, the call passes through that cell's own gateway.

**Agent to LLM (southbound).** Model inference is southbound like any other tool call but carries the richest data stream, the prompt, retrieved context, and completion together. A model running as a local component inside the cell is the exception, since its inference never crosses the edge.

**Agent to agent (eastbound and westbound).** A call is eastbound leaving the calling cell and westbound arriving at the receiving cell. The risk specific to this path is a request reaching an agent it was never authorized to reach, or one that outlives its purpose. The discipline is the same regardless of communication style: authorize the call against the incoming actor chain before the receiving agent is driven, and bound how long a delegation remains valid.

### 5.5 Handling credentials at the boundary

Every transport depends on a credential: a downstream key, an internal credential, a model provider's API key, a cell credential. The boundary handles all of them under one rule: the agent runtime never holds a raw downstream credential.

The gateway is the credential custodian. Secrets for the cell's egress paths are held in a secret store inside the trust boundary and attached by the gateway at the moment of the outbound call; the runtime asks the gateway to make a call and receives only the result. A credential never enters the prompt, the model context, or the plan, closing the path by which prompt injection or a poisoned tool response could exfiltrate it.

Holding long-lived downstream credentials at the gateway makes rotation a cell operation: a key is replaced in the secret store without touching agent code, and a leak is revoked at one point rather than chased across components. The cell-internal and on-behalf-of identities are the only credentials that flow through the runtime, and their narrow scope and short lifetime bound what their exposure would cost.

Inbound credentials are validated, never trusted on presentation. A user token at the northbound edge and a calling cell's credential at the westbound edge are verified against their issuer before admission; the interior sees only the re-established cell-internal identity, never the original credential.

### 5.6 Policy: the gateway as the enforcement layer

A check inside the runtime is a check the runtime can bypass; a check at the gateway sees the actual call regardless of how the agent reached it. Prompt guardrails and runtime validators lower the probability of an unsafe action but do not survive a non-deterministic planner taking an unanticipated route. At scale, gateway enforcement is what holds.

**Ingress policy** decides whether a request reaches the runtime at all: authentication and token validation reduce the caller to a cell-internal identity; admission control enforces per-caller rate limits, abuse detection, input validation, and payload-size caps; and for westbound calls, delegation authorization checks the incoming actor chain against the scopes it may reach.

**Egress policy** governs what the agent sends out. Per-tool egress policy keeps the endpoint, scopes, rate limit, timeout, payload cap, and permitted data classes at the gateway rather than in agent code. Allowlist rules tie tool access to agent identity, so tool selection becomes a policy decision rather than a code path. Intent-based authorization checks the declared intent on the on-behalf-of identity against the specific call. For example, an HR agent may be allowed to read employee profile data, but the same invocation should be refused if the declared intent is to update payroll details without the required payroll authorization. This is narrower than an allowlist because it is evaluated per call, not only per role. Quotas treat the cell as the accounting unit for tool and model spend, enforced before the call leaves.

**Egress filtering** sits on top of egress policy as the last line against prompt injection, tool poisoning, and confused-deputy attacks. On southbound and eastbound paths the gateway applies data loss prevention (DLP), redacts outbound payloads, and blocks disallowed destinations. Model traffic is filtered the same way: guardrails on outbound prompts and inbound completions catch what inline runtime guardrails miss.

### 5.7 What the gateway enforces on each boundary

Applying ingress and egress policy per edge turns one undifferentiated perimeter into four distinct enforcement points.

**Northbound ingress** (user-facing requests) carries the heaviest inbound checks: token validation to a cell-internal identity, per-user and per-client rate limits and abuse detection, input validation and payload caps, and the correlation identifier that starts the trace every downstream hop carries.

**Westbound ingress** (calls from other internal cells) authorizes a delegation rather than a session: the gateway verifies the calling cell's identity, validates the delegation chain, checks the requested action against the scopes that chain may reach, and enforces per-caller quotas.

**Southbound egress** (calls outside the enterprise boundary, including hosted LLM inference) carries the fullest egress policy and filtering: endpoint allowlist, per-tool scopes, rate limits, timeouts, payload caps, intent-based authorization against the declared intent on the call, credential attachment at the gateway, DLP, and blocked destinations. Model traffic adds prompt-injection and jailbreak detection inbound, sensitive-data filtering outbound, model routing with failover, and per-model metering against the cell's quota.

**Eastbound egress** (calls to other internal cells) narrows the cell-internal identity to an on-behalf-of identity scoped to the destination, appends this cell to the actor chain, and applies per-destination quotas. It carries the same egress filtering as southbound (DLP, outbound redaction, and disallowed-destination blocking), so a confused deputy cannot carry tainted data to a peer cell.

The pattern across all four edges is the zero trust pattern the section opened with: identity resolved at ingress, scope narrowed at egress, no crossing trusted for its origin, every crossing logged.

### 5.8 Audit and traceability

An agent decides at runtime rather than running enumerable code paths, so the only reliable account of what it did is the record of what crossed its edge. Every crossing is logged with the full actor chain, intended target, scopes presented, request and response sizes, latency, and outcome; inter-cell calls are recorded at both ends, so a delegation can be reconstructed from either side.

A correlation identifier started at northbound ingress travels every downstream hop, so a single user request can be followed across cells as one coherent trace. Logs collected anywhere but the gateway are partial by construction, which is why enforcement and audit sit at the same edge.

## 6\. Reference patterns for agentic cells

A single agent cell is rarely the whole system. Enterprises adopt agents by adding them to a digital ecosystem that already has services, data, and domain boundaries, so an agentic system takes shape as several cells that call each other, share tools, and read from common knowledge sources. That shape, the set of cells and the boundaries drawn between them, is what decides the blast radius, the ownership, and how far a single failure can spread. The patterns that follow are the arrangements that recur in practice. They are not an exclusive list, and a production system usually combines them, for example a supervisor cell that delegates to worker cells, which in turn consume a shared capability cell.

### 6.1 Single-agent cell

One agent, its runtime, its domain-scoped memory, and its tool adapters, inside one cell. This is the default and the unit to reach for first. The cell owns exactly one agent's behavior, so its version pins one model, one system prompt, and one tool binding set, and a bad version rolls back without touching anything else.

It fits an agent with a well-defined job whose tools belong to that job: contract review, log triage, single-purpose retrieval. Because the cell is one trust boundary around one bounded capability set, the blast radius is the smallest available. When the right pattern is not obvious, this is the starting point. A second cell is justified by a distinct domain or a distinct trust level, per the bounded-context rule, not by agent count alone.

### 6.2 Multi-agent cell

Several agents that collaborate on one task inside a single cell, sharing memory and one trust domain. They communicate over the cell's internal transport rather than through the gateway, because they sit inside the same boundary. A planner, a critic, and an executor iterating on one task need each other's intermediate state at internal latency, and they operate at the same trust level on the same domain.

The consequence is direct: the cell is one trust boundary, so it is one capability domain and one blast radius. The gateway allowlist is drawn at the cell edge, not between agents, so any tool one agent in the cell can reach must be treated as reachable by every agent in it. That is acceptable when the agents genuinely share a task and a trust level. Using a multi-agent cell to avoid separating agents that belong to different domains or different privilege levels is the agent-monolith anti-pattern described below.

### 6.3 Supervisor and worker cells

A supervisor cell decomposes a task and delegates subtasks to worker cells, each in its own cell with its own gateway, trust boundary, and capability scope. This is the pattern for decomposable work whose subtasks differ in privilege or domain. A supervisor planning a customer action delegates read-only retrieval to one worker and record writing to another, and each worker's gateway grants only the scope its job needs.

What the composition buys is separation. Each worker is a distinct capability with its own bounded blast radius, versioned and rolled back on its own, so a change to how one subtask is handled does not ripple into the others. Privilege stays separated too: the supervisor never holds the union of its workers' scopes, so compromising the supervisor does not yield every downstream capability. Delegation is how the arrangement stays governed rather than what defines it, and its mechanics belong to the security section.

### 6.4 Capability cells: tool and memory specializations

The capability cell is a reusable capability owned by one cell and consumed by others through governed interfaces, in preference to a central tool hub. Two specializations recur in agent systems, and both are capability cells in that sense.

A **tool cell** exposes a governed tool surface, one or more MCP servers or API adapters, that many agent cells call. It holds the downstream credential so no agent cell does, which makes rotation one operation and keeps the credential-custody rule true across every consumer. Use it when several agent cells need the same sensitive or expensive downstream system: a payments API, a system-of-record connector, a metered third-party service.

A **memory cell** exposes a shared knowledge source, a vector store, a document index, or a feature store, so agent cells retrieve from one governed source rather than each holding a private copy. Read and write scopes are enforced separately at its gateway, which keeps a retrieval-only agent from writing to a store it should only read. Use it when knowledge must stay consistent and governed across agents, such as one product-documentation index behind both a retrieval agent and a support agent.

Both carry the same trade-off: a shared dependency to plan capacity and availability for, and a versioned contract that must stay stable for every cell pinned to it. Neither is a new construct; both are the capability cells applied to a specific kind of shared resource.

### 6.5 Composing the patterns

These patterns stack. A realistic customer-support system pairs a supervisor cell with single-agent worker cells for triage and action, a memory cell for the knowledge base, and a tool cell for the system-of-record connector. Each boundary in that arrangement is a gateway crossing, each crossing carries and narrows the actor chain, and each cell versions independently. The composition is governed for the same reason each cell is: nothing reaches or leaves a cell except through its gateway. The worked example works this through in full.

### 6.6 Anti-patterns

The patterns above show where a cell boundary earns its place. The anti-patterns show what goes wrong when a boundary is drawn for convenience instead of for a real difference in domain, ownership, or trust. Most reduce to the same mistake: a boundary in the wrong place, either absent where containment was needed or imposed where it was not. Some of these have already appeared as the failures the earlier principles exist to prevent, such as bypassing the gateway, sharing a credential across cells, cyclic delegation, and the tool monolith. Two more arise only once cells are composed, and they sit at opposite extremes of where the boundaries fall.

**The agent monolith.** Unrelated agents packed into one cell to avoid drawing boundaries. Because a cell is one trust domain and one blast radius, the monolith grants every agent the union of every agent's tool access, and a bad version of any one agent forces a rollback of all of them. This is the multi-agent cell used where separate cells were required. If two agents do not share a domain and a trust level, they belong in separate cells.

**Over-fragmentation.** The opposite failure: splitting one agent's coherent job across many cells, so a single task fans out through gateway crossing after gateway crossing. Every crossing adds latency, a token exchange, and an audit record, and none of it buys containment when the pieces share a domain and a trust level anyway. A cell boundary should mark a real difference in ownership, domain, or privilege. Where no such difference exists, the work belongs in one cell.

The rule behind both patterns and anti-patterns is the bounded-context rule: draw a cell boundary where a real domain or trust difference exists, and nowhere else. Where the boundaries match the domains, the containment properties from the rest of this paper hold. Where they are drawn for convenience, in either direction, the architecture pays for it without being any safer.

# 7\. Reference implementation: applying CBA to agentic workloads

This section instantiates the whole architecture in one working system. Nothing here is new machinery: every boundary, identity, and policy decision applies a principle already stated. The implementation is vendor-neutral, its components named by role. The cell gateway can be an API gateway, an AI gateway, an MCP gateway, or a combination at one edge; what matters is the contract enforced at the crossing, not the technology enforcing it.

### 7.1 Scenario and scope

The system is a recruitment pipeline in the HR landscape used throughout this paper. A candidate uploads a CV against an open requisition; the pipeline assesses it against the requisition and its rubric, prepares tailored questions, and evaluates the answers into a structured recommendation. The candidate advances to a panel interview only after the hiring manager approves that specific candidate; only then are interviews scheduled and the outcome sent.

The pipeline runs under three authorities in sequence: the candidate's authority at intake, the workflow's own for assessment and evaluation, and the hiring manager's, minted at approval, for the advance and scheduling. It lands in a brownfield landscape: the applicant tracking system and the employee profile services are exposed to agents as governed tools and are not modified. Background and reference verification, employment and education checks, and right-to-work confirmation are run by an external SaaS HR platform against specialized tools. The platform exposes this as an HR assistant agent, so rather than reimplement it the supervisor delegates verification to that agent over agent-to-agent, an agent the enterprise consumes but neither hosts nor manages.

### 7.2 Cell topology

![Cell topology of the recruitment pipeline](/media/media_agentic_systems/recruitement-pipeline-cell-topology.png)
<p align="center"><em>Cell topology of the recruitment pipeline</em></p>

Six cells sit inside the enterprise boundary; the model providers, the calendar service, and an external SaaS-provided HR assistant agent sit outside it. Each gateway marker on a cell edge is an enforcement point. Of the six cells, three contain agents and three are tool cells that front a system or a capability and hold no agent at all.

The **Recruitment Supervisor Cell** holds a single orchestrating agent. It receives the candidate's submission and the hiring manager's approval, drives the pipeline, holds state across the two waits, and delegates the domain work. It performs no assessment and no writes of its own beyond recording candidate-submitted content; its role is to route work to the cells that own it. It is also the one cell that reaches outside the enterprise for domain work: it delegates candidate verification to the external SaaS HR agent.

The SaaS agent is a distinct case: it is not a static endpoint but an autonomous agent on infrastructure the enterprise neither governs nor observes, so a call to it is agent-to-agent access that leaves the trust boundary, and the gateway at that edge is the last control the enterprise has over what is sent.

The **Assessment Worker Cell** holds several agents that share one task: a CV validator, question-preparation agents, and an evaluation agent. Because they share one domain and one trust level, they share the cell's memory and internal transport, and the rubrics and question banks they reason against live inside the cell as a local knowledge base. Calls among these agents, and to that knowledge base and the cell's local tool, stay inside the cell and cross no gateway. What the ensemble ingests is untrusted candidate content, which is why it is contained tightly and why it has no path to the employee directory.

The **Interview Coordinator Cell** holds one agent and local tools, and reaches a remote calendar service outside the enterprise through its gateway. It resolves the interview panel, books time on the calendar, and records the result. It holds the broadest reach in the system, but its most consequential actions are not standing capabilities; they are granted per candidate only after approval.

**The ATS Cell** is a tool cell fronting the brownfield applicant tracking system through one gateway, an MCP server being one natural realization, and it owns the candidate domain with row-level authorization matching the subject in the actor chain to the record in the call. It also holds the pipeline's decisive gate: the write that marks a candidate ready for interview passes only under an actor chain rooted in the hiring manager's validated approval whose subject matches the candidate, and only with the Interview Coordinator as the acting identity, so authority and capability must combine at the gate.

The three tool cells expose a bounded surface and nothing more. The **ATS Cell** fronts the applicant tracking system and owns the candidate domain. The **Employee Profile Mgt. Cell** fronts the staff directory and is read-only in this pipeline. The **Notification Cell** owns the single channel for human-facing messages; its contract names a recipient by role or purpose, never by address, so a caller cannot redirect a message to a destination of its choosing.

The requests that cross the system follow the phases of the use case. At intake, the candidate's submission enters the supervisor, which records the content in the ATS. The supervisor then delegates to the Assessment Worker Cell, which reads the CV and requisition from the ATS, prepares questions, writes its assessment artifacts back to the ATS, and asks the Notification Cell to deliver the questions to the candidate. The candidate's answers return through the supervisor, which delegates evaluation back to the same worker; the worker scores the answers and records the recommendation in the ATS. Before seeking approval, the supervisor delegates the verification checks to the external SaaS HR agent over A2A and records the returned results in the ATS. The supervisor then asks the Notification Cell to carry the recommendation to the hiring manager for approval. On approval, the supervisor delegates to the Interview Coordinator Cell, which reads the panel from the Employee Profile Mgt. Cell, advances the candidate and writes interview records in the ATS, books time on the external calendar, and asks the Notification Cell to send the outcome. Every agent cell also reaches its model provider throughout, for the reasoning each step requires.

Identity issuance and token exchange are provided by an identity plane, the enterprise identity provider and a token service, that every gateway depends on to validate inbound credentials and mint the scoped, short-lived credentials that flow between cells. It is omitted from the topology to keep the data flow legible, but no crossing described below completes without it.

### 7.3 Audit reconstruction

The walkthrough reads the pipeline forward; the audit trail reads it backward, and for an autonomous system the backward reading is the authoritative one. The correlation identifier started at intake threads every hop and survives both pauses, so a multi-day, multi-actor, pause-and-resume pipeline reconstructs as a single coherent trace.

Each crossing was logged at the gateway with the full actor chain, the intended target, the scopes presented, and the outcome, and each inter-cell hop was recorded at both ends. The trace answers the accountability questions directly: which actions ran under the candidate's authority, which under the workflow's, and which under the hiring manager's, and what the assessment cost against each cell's quota. The separation of duties is visible as a property of the chains themselves: every advance and every interview write carries an actor chain rooted in a validated approval, subject-bound to the candidate it advanced, and exercised by the one allowlisted agent identity. For every candidate who moved forward, the trail is standing proof that the authority existed before the action did.

### 7.4 What containment bought

Under the assume-breach lens the security section opened with, take each failure as given and measure what it reaches. The measure, in every case, is the gate at the ATS cell's edge: a chain rooted in the workflow's identity fails its first condition, any acting identity other than the Interview Coordinator fails its second, and the honest path passes both. Because the check lives at the gate rather than in agent code, and the honest path always carries the authority, a refused advance in the log is never routine traffic. It is an alarm.

If untrusted content steers the assessment ensemble, the compromise is shared within the cell (the accepted consequence of the multi-agent pattern) and stops at the cell edge. The hijacked ensemble is bounded by its grants: subject-bound reads by reference, one artifact write, and a metered model budget. It cannot advance the candidate, failing both conditions of the gate; it cannot touch employee records, holding no Employee Profile scope; and it cannot reach other candidates, every read bound to the subject its delegation names. It can leak only filtered, metered model traffic and question delivery whose destination it cannot choose, and corrupt only its own artifacts, whose worst outcome is a bad recommendation still gated behind human approval.

If the supervisor is compromised, it holds nothing at rest: no ATS scope, no candidate credentials, only state and references. Writes exist only as on-behalf-of assertions rooted in the candidate token being processed, so there is no cross-candidate write and no read scope through which a steered plan pulls content into its context. The advance is beyond it: a forged or replayed approval fails at northbound ingress, and even a valid approval's authority is useless at the gate under the supervisor's identity, since the acting party must be the Interview Coordinator. The most it can do with a real approval is delegate the work it would have delegated anyway.

If the Interview Coordinator is compromised, it holds the broadest reach and the only identity the advance gate accepts, but not authority: its writes run under per-candidate delegations rooted in a validated approval, not standing scopes, so absent that delegation the advance and interview writes are refused at the same gate, and its calendar egress is allowlisted, filtered, and metered. Capability without authority is as bounded as authority without capability.

If the external SaaS agent is compromised or turns hostile, it sits outside the enterprise's control by definition, so containment is measured by what the boundary let it receive and what it can do with it. It never receives a raw downstream enterprise credential; it is reached through a gateway-held credential and handed only a scoped, short-lived on-behalf-of assertion for the single verification step, whose audience, subject, intent, scope, lifetime, and reuse policy the gateway validates before that step proceeds. It therefore cannot act back into the enterprise beyond that assertion's scope and lifetime, and it cannot advance a candidate, which requires the ATS gate its chain does not satisfy. What it receives outbound is bounded by DLP and by the narrowed intent, so a hostile vendor agent sees only the data the verification needs, not the candidate's full record or the employee directory.

If a credential leaks, the system-of-record and delivery credentials live in the tool cells' custody, so rotation is one operation at one cell rather than a search across agent runtimes. The credentials that do flow through agent runtimes, the cell-internal identities, on-behalf-of assertions, and single-use grants, are short-lived, narrowly scoped, and identity-bound, so their exposure is bounded by construction.

None of these outcomes depends on the agents behaving well, or on telling an attack from normal operation, because the honest and adversarial paths run through the same gates. They depend only on where the boundaries sit and what the gateways enforce: the same six cells, four edges, and rules from the rest of this paper, arranged so the properties hold even when an agent does exactly the wrong thing.

## 8\. Conclusion

Agentic systems introduce autonomy into enterprise architecture. Agents can reason over context, choose tools, call APIs, access data, delegate work, invoke models, and trigger workflows at runtime. This makes them useful enterprise actors, but it also makes them difficult to govern through traditional integration and security controls alone. The core architectural challenge is not only how to give agents access to enterprise capabilities, but how to keep that access owned, scoped, observable, and accountable.

This paper positioned Domain-Driven Design as the principle for identifying boundaries, and Cell-Based Architecture (CBA) as the model for enforcing those boundaries at runtime. DDD helps determine where domain ownership, language, rules, and responsibilities belong. CBA turns those boundaries into deployable, manageable, observable, and secure runtime units. For agentic workloads, the cell becomes the containment unit for agents, tools, services, data, memory, policies, gateways, and audit controls. 

The cell is important because it provides multiple forms of containment at once. It is a trust boundary, where identity, delegation, scope, and runtime context are validated. It is a capability boundary, where tools, APIs, skills, and reusable components remain owned by the domain or shared capability that provides them. It is also an operational boundary, where sandboxing, quotas, credentials, observability, evaluation, and cost controls can be applied consistently. The security model follows the same principle. The cell edge becomes the zero trust enforcement point. Every crossing, northbound, southbound, eastbound, or westbound, is authenticated, authorized, scoped, filtered, metered, and logged. Agents do not receive implicit trust because they are internal, and they should not hold raw downstream credentials. Instead, gateways re-establish identity, narrow scope, attach credentials when needed, enforce policy, and record the actor chain for audit.

The reference patterns show how this model can be composed in real systems. Some use cases fit a single-agent cell. Others require multi-agent cells, supervisor and worker cells, tool cells, memory cells, or shared capability cells. The boundary should be drawn where there is a real difference in domain, ownership, privilege, or trust level. Drawing too few boundaries creates an agent monolith. Drawing too many creates unnecessary latency and operational complexity.

The HR recruitment reference implementation demonstrates how these ideas apply in a brownfield enterprise landscape. The Recruitment Supervisor Cell, Assessment Worker Cell, Interview Coordinator Cell, ATS Cell, Employee Profile Mgt. Cell, and Notification Cell each own a clear responsibility, with security and policy enforcement applied pervasively at every cell gateway. The pipeline can process CVs, evaluate candidates, request approvals, schedule interviews, and communicate outcomes without bypassing the systems that own candidate data, employee data, notifications, identity, or approval authority. The result is not a separate agent architecture, but an agentic layer composed through governed cell boundaries.

The main conclusion is that agents should not dissolve enterprise boundaries. They should operate within boundaries that are explicit, enforceable, observable, and owned. APIs, events, MCP tools, A2A interactions, workflows, model calls, and agent-facing skills should remain connected to the same governed capabilities already present in the enterprise. Cell-Based Architecture provides a practical way to introduce agentic systems incrementally while preserving modularity, composability, least privilege, trust, auditability, and operational control.

## References 

[1] Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md

[2] Abeysinghe, A. & WSO2. (2026, July). reference-architecture/trusted-ai-governance.md at master · wso2/reference-architecture. GitHub. https://github.com/wso2/reference-architecture/blob/master/trusted-ai-governance.md

[3] Domain-Driven Design: Tackling complexity in the heart of software: Evans, Eric: 9780321125217: Amazon.com: Books. (n.d.). https://a.co/d/0cgNqn6m

[4] Implementing Domain-Driven design: Vernon, Vaughn: 9780321834577: Amazon.com: Books. (n.d.). https://a.co/d/0cYLCrbF




