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

Agentic workflows are more complex than traditional application calls. A user may authorize a client, the client may delegate to an agent, that agent may delegate a subtask to another agent, and the second agent may invoke a tool or external API. The downstream cell must understand the delegation chain well enough to decide whether the action is allowed. The implementation details are discussed later in the “**Security Boundaries: Identity, Delegation and Policy**” section.

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

## 8\. Conclusion

Agentic systems introduce autonomy into enterprise architecture. Agents can reason over context, choose tools, call APIs, access data, delegate work, invoke models, and trigger workflows at runtime. This makes them useful enterprise actors, but it also makes them difficult to govern through traditional integration and security controls alone. The core architectural challenge is not only how to give agents access to enterprise capabilities, but how to keep that access owned, scoped, observable, and accountable.

This paper positioned Domain-Driven Design as the principle for identifying boundaries, and Cell-Based Architecture (CBA) as the model for enforcing those boundaries at runtime. DDD helps determine where domain ownership, language, rules, and responsibilities belong. CBA turns those boundaries into deployable, manageable, observable, and secure runtime units. For agentic workloads, the cell becomes the containment unit for agents, tools, services, data, memory, policies, gateways, and audit controls. 

The cell is important because it provides multiple forms of containment at once. It is a trust boundary, where identity, delegation, scope, and runtime context are validated. It is a capability boundary, where tools, APIs, skills, and reusable components remain owned by the domain or shared capability that provides them. It is also an operational boundary, where sandboxing, quotas, credentials, observability, evaluation, and cost controls can be applied consistently. The security model follows the same principle. The cell edge becomes the zero trust enforcement point. Every crossing, northbound, southbound, eastbound, or westbound, is authenticated, authorized, scoped, filtered, metered, and logged. Agents do not receive implicit trust because they are internal, and they should not hold raw downstream credentials. Instead, gateways re-establish identity, narrow scope, attach credentials when needed, enforce policy, and record the actor chain for audit.

The reference patterns show how this model can be composed in real systems. Some use cases fit a single-agent cell. Others require multi-agent cells, supervisor and worker cells, tool cells, memory cells, or shared capability cells. The boundary should be drawn where there is a real difference in domain, ownership, privilege, or trust level. Drawing too few boundaries creates an agent monolith. Drawing too many creates unnecessary latency and operational complexity.

The HR recruitment reference implementation demonstrates how these ideas apply in a brownfield enterprise landscape. The Recruitment Supervisor Cell, Assessment Worker Cell, Interview Coordination Worker Cell, ATS Cell, Employee Profile Cell, Notification Cell, and Security Cell each own a clear responsibility. The pipeline can process CVs, evaluate candidates, request approvals, schedule interviews, and communicate outcomes without bypassing the systems that own candidate data, employee data, notifications, identity, or approval authority. The result is not a separate agent architecture, but an agentic layer composed through governed cell boundaries.

The main conclusion is that agents should not dissolve enterprise boundaries. They should operate within boundaries that are explicit, enforceable, observable, and owned. APIs, events, MCP tools, A2A interactions, workflows, model calls, and agent-facing skills should remain connected to the same governed capabilities already present in the enterprise. Cell-Based Architecture provides a practical way to introduce agentic systems incrementally while preserving modularity, composability, least privilege, trust, auditability, and operational control.






