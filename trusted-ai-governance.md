<h1 align="center"> Trusted AI Governance </h1>
<h3 align="center"> An architectural thesis for governing agentic systems </h3>
<p align="center">
<i>
Version: Summer-2026<br/>
<b>First Published On: Summer-2026<br/>  </b>
</i>
</p>

**_Author_**

+ [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO - [WSO2, LLC](https://wso2.com/) | [@asankama](https://twitter.com/asankama)

> *This paper presents an architectural thesis for governing agentic systems in the enterprise. The core shift is from model trust and output review to a system of control that governs boundaries, delegation, runtime behavior, evidence, and economic exposure.
The paper is intentionally vendor-neutral. It defines the governance problem and the required architecture based on enterprise needs, not on any product, platform, or implementation boundary.*

## Introduction

Enterprise AI governance is often framed as a problem of model trust. That framing is too narrow for agentic systems. In deterministic software, governance is built around specification. A contract is defined, the output is verified before deployment, and the same contract is expected to hold at runtime. Agentic systems break that assumption. An agent does not have a fixed output specification in the same way a service, workflow, or API does. Each input, context change, tool result, memory state, and delegated action can alter the output and the path used to produce it.

![figure 1: deterministic vs probabilistic system governance](/media/figure-1-deterministicvsprobabilistic.png)

This changes the center of gravity for governance. The enterprise can no longer govern only by approving the output before deployment. Governance must move closer to the point where intent becomes action and must produce evidence after the action. Trusted AI governance is therefore not blind trust in a model. It is a system of control that makes agent behavior verifiable, attributable, and bounded. The agent inherits trust from the architecture around it.
This paper defines a capability model for governing agentic systems. Discovery is the precondition, because an enterprise cannot govern an agent it has not found. Identity and delegation form the keystone, because agents must be first-class actors with traceable authority. Boundary authorization, runtime safety, human oversight, policy authorship and distribution, observability and evidence, and economic control complete the model.
The model also distinguishes two enforcement approaches. 
1. Inline governance 
2. Infrastructure-enforced governance

Inline governance is injected into the agent or application code path by engineers. Infrastructure-enforced governance is applied outside the agent implementation by gateways, proxies, runtimes, service meshes, identity infrastructure, model gateways, API gateways, and other policy enforcement points. Both are needed. Inline governance captures local intent and domain logic. Infrastructure-enforced governance provides consistent control at shared boundaries and enables parameter-level enforcement. The integrated architecture depends on a clear control plane and data plane separation: policy is authored centrally, enforced at distributed boundaries, and proven through evidence.

## The inversion

Traditional enterprise governance assumes that software behavior can be specified before deployment. A service exposes an API contract. A workflow follows a defined sequence. An integration transforms data according to a known mapping. A human approves the business process, engineers test the implementation, and the organization monitors whether the deployed system continues to meet its expected behavior.

This is specification-based governance. It works because deterministic systems have stable contracts. The same input, under the same conditions, should produce the same output. Governance can therefore inspect the design, test the output, approve the release, and rely on the contract during runtime. Runtime governance still matters, but it usually confirms that the system is behaving according to what was already specified.

Agentic systems do not fit that model. An agent is not only a component that produces an answer. It can reason over context, call tools, retrieve data, invoke APIs, delegate work, coordinate with other agents, and decide when to continue, stop, escalate, or retry. The output is not the only artifact of concern. The path matters. The authority used matters. The data accessed matters. The tool calls matter. The decision to act matters.

This creates an inversion in governance. In deterministic systems, governance can begin with the output specification. In probabilistic agentic systems, the output cannot be fully specified in advance. The enterprise must instead govern the boundary where intent becomes action and the evidence created after action. The first question is not only, “Was the output correct?” It is also, “Was this agent allowed to do this, under this delegation, with this context, through this tool, at this time, for this purpose?”

Pre-deployment review still has value. Models, prompts, tools, policies, and workflows should be evaluated before release. But pre-deployment verification cannot carry the full governance burden. There is no final output contract to verify once and trust forever. The runtime path is part of the governed surface.

The enterprise governance model must therefore shift from output approval to controlled action. The system must decide what an agent may access, what it may invoke, what it may delegate, when it must stop, when a human must approve, how cost is bounded, and what evidence must be retained. Governance becomes architectural, not procedural.

## Defining trust

Trust is often used as a soft term in AI discussions. For agentic systems, it must be treated as an architectural outcome. The enterprise does not trust the model in isolation. It trusts the system of control around the model.

A model may be capable, but capability is not trust. A model may be accurate in a benchmark, but benchmark performance is not runtime assurance. A model may produce useful responses, but usefulness does not prove that the response was authorized, safe, attributable, or economically bounded. In an enterprise, trust must survive audit, incident review, regulatory scrutiny, and executive accountability.

**Trusted AI governance is governance that produces behavior that is verifiable, attributable, and bounded, enough that a human or auditor can rely on the system deliberately.**

Inspectable means the enterprise can inspect what happened. The system must capture the reasoning path where appropriate, the tool calls made, the data accessed, the policies applied, the authority used, the decisions taken, and the points where human oversight occurred. The record must be strong enough to support review after the fact.

Attributable means the enterprise can assign responsibility to the right actor and authority chain. An agent should not act as an anonymous workload, a shared service account, or an invisible extension of a user session. It must have identity. Its delegated authority must be explicit. Its actions must be traceable to the human, application, process, or agent that authorized it.

Bounded means the agent acts within defined limits. Those limits include access boundaries, tool boundaries, data boundaries, policy boundaries, cost boundaries, jurisdictional boundaries, and human approval boundaries. Boundaries do not remove all risk, but they make risk governable.
Trust is therefore inherited. The agent inherits trust from identity, delegation, authorization, runtime controls, policy distribution, observability, evidence, oversight, and economic limits. Without that architecture, trust collapses into hope.
Trusted AI governance has two enforcement models.

The first is inline governance. Inline governance is implemented inside the agent or application code path. Engineers add policy checks, validation logic, safety rules, human approval steps, logging, and exception handling directly into the agent implementation. This model gives application teams fine-grained control because the enforcement logic has direct access to local intent, state, workflow context, and domain rules. It is useful, but it is not sufficient by itself. Inline governance depends on each implementation doing the right thing consistently. In a large enterprise, that creates uneven coverage, duplicated logic, and weak assurance across domains.

The second is infrastructure-enforced governance. Infrastructure-enforced governance applies controls outside the agent code through the execution fabric around the agent. This includes gateways, proxies, policy enforcement points, identity infrastructure, API gateways, model gateways, service meshes, runtimes, and agent-to-agent communication boundaries. This model is critical because it gives the enterprise a common enforcement layer that does not depend on every agent implementation being correct, current, or complete.

Infrastructure-enforced governance must be parameter-aware. It is not enough to know that an agent is calling a tool, API, model, database, workflow, or another agent. The governance layer must inspect and constrain the parameters of the action. Which customer record is being accessed? Which fields are being sent? What amount is being refunded? Which recipient is receiving the message? Which query is being executed? Which file is being attached? Which authority is being delegated? Parameter-level enforcement is where infrastructure turns broad permission into bounded action.
Both models are required. Inline governance captures local business intent and domain-specific rules. Infrastructure-enforced governance provides consistent enterprise control at shared boundaries. Inline governance without infrastructure enforcement becomes fragmented. Infrastructure enforcement without inline context can become too coarse. Trusted AI governance needs both, connected through a control plane that authors policy and distributed enforcement points that apply it where agents act.

## The requirements

The capability model begins with discovery. Discovery is not one of the optional governance functions. It is the precondition for every other control.

### Discovery

An enterprise cannot govern an agent it has not found.

Discovery creates the inventory of agents, models, tools, delegated authorities, agent-to-agent interactions, and shadow AI usage. It identifies where agents exist, who owns them, what models they use, what tools they can invoke, what data they can reach, and what business process they affect.

![figure 2: capability model](/media/figure-2-capability-model.png)

Discovery must sit in front of identity. Identity makes actors addressable, but discovery finds the actors in the first place. Without discovery, identity coverage will be incomplete. Undiscovered agents will continue to operate through user credentials, service accounts, embedded keys, local scripts, unapproved SaaS tools, or undocumented automation.

The first enterprise question is simple: “What agentic systems are operating in the environment?” If the enterprise cannot answer that question, it cannot answer any of the harder questions that follow.

Discovery must also cover shadow AI. Agentic behavior will not appear only in approved platforms. It will appear in notebooks, workflow tools, CI/CD scripts, customer support systems, productivity suites, integration logic, internal portals, and consultant-built prototypes. Governance must assume that the agent estate is broader than the official architecture.

Discovery produces and maintains the inventory of agents, models, tools, and shadow AI, with MCP registries and API catalogs acting as important systems of record for what agents can discover, invoke, and expose. Identity makes that inventory addressable and governable.

### Identity and delegation
Identity and delegation are the keystone of trusted AI governance.

An agent must be a first-class actor. It must have an identity separate from the human who requested the action, the application that hosts it, and the infrastructure where it runs. That identity must be usable for authorization, audit, policy evaluation, rate control, cost attribution, and incident response.

Delegation is equally important. Agents rarely act only on their own behalf. They act for a user, a team, a business process, another agent, or an application. Governance must capture the delegation chain. The system must know who initiated the action, what authority was delegated, what scope was granted, how long it remains valid, and whether the agent stayed within that scope.

This requirement is immature at the standards level. Existing identity and authorization standards provide useful building blocks, but the enterprise model for first-class agent identity and multi-step delegation is still developing. That immaturity should be stated plainly. Pretending the problem is solved creates false assurance.

The enterprise question is: “Who is this agent, and on whose authority is it acting?”

If that cannot be answered, every downstream control weakens. Authorization becomes approximate. Audit becomes incomplete. Cost attribution becomes unclear. Incident response becomes slower. Human accountability becomes blurred.
Identity does not make an agent safe by itself. It makes the agent addressable. Addressability is the condition required for governance.

### Boundary authorization
Agentic governance must enforce authorization at the boundary where intent becomes action. That boundary has three faces.

The first face is model traffic. Requests to and from models must be governed. This includes which models can be used, what data can be sent, what prompts are allowed, what responses require filtering, what rate limits apply, and what logging is required.

The second face is tool and context access. Agents become operationally meaningful when they can retrieve data, call APIs, execute workflows, update systems, send messages, or trigger business processes. This is where the risk moves from language to action.

The third face is agent-to-agent traffic. Agents will not operate only as isolated assistants. They will coordinate, delegate, negotiate, and hand off tasks. That traffic must be governed. The receiving agent must understand who is calling, what authority is being carried, what context is being shared, and what policy applies.

[Cell-based architecture](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) makes these boundaries explicit: each governed cell preserves local autonomy while enforcing enterprise policy at ingress, egress, delegation, and evidence points.

Boundary authorization is the primary surface for infrastructure-enforced governance. It operates outside the agent implementation at the shared boundaries where agents reach models, tools, APIs, context, data, and other agents. The enforcement point must apply authorization, redaction, scoping, rate control, transformation, approval routing, and termination before the action crosses the boundary.

Boundary authorization must be parameter-aware. The risk is rarely in the tool name alone. The risk is in the specific action, the specific data, the specific recipient, the specific amount, the specific query, and the specific delegation being attempted. An agent may be authorized to call a payment API, but not to refund a specific amount. It may be authorized to use an email tool, but not to send regulated data to an external recipient. It may be authorized to query customer records, but not to retrieve fields outside the purpose of the task.

Authorization must be dynamic. Static access grants are not enough. The same agent may be allowed to read a record but not update it. It may be allowed to summarize a contract but not send it externally. It may be allowed to retrieve customer history for support but not use that same data for marketing. It may be allowed to call a tool under human supervision but not autonomously.

Boundary authorization is where policy becomes enforcement.


