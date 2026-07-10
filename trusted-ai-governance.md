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
This paper defines an architectural thesis for governing agentic systems. Discovery is the precondition, because an enterprise cannot govern an agent it has not found. Identity and delegation form the keystone, because agents must be first-class actors with traceable authority. Boundary authorization, runtime safety, human oversight, policy authorship and distribution, observability and evidence, and economic control complete the model.
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

**Trusted AI governance is governance that produces behavior that is inspectable, attributable, and bounded, enough that a human or auditor can rely on the system deliberately.**

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

### Authorization is not safety.

An agent may be authorized to access a tool and still use it incorrectly. It may follow a malicious instruction embedded in retrieved content. It may be manipulated through prompt injection. It may be jailbroken. It may leak data through a path that is technically permitted. It may take a permitted action that is wrong for the business context.

Runtime safety addresses these risks. It must inspect the behavior of the agent while the agent is operating, not only the permissions assigned to it before execution.

Runtime safety must cover prompt injection, jailbreaks, tool misuse, data exfiltration through legitimate paths, unsafe retries, excessive fan-out, conflicting instructions, and permitted-but-wrong actions. This requires controls that understand context, not only access rights.

A simple example illustrates the difference. An agent may be authorized to send an email. That does not mean every email it drafts should be sent. It may include confidential data, misstate a commitment, respond to the wrong party, or execute a social engineering pattern. Authorization answers whether the agent may use the email tool. Safety asks whether this specific use is acceptable.

Runtime safety can be implemented inline, infrastructure enforced, or both. Inline safety rules can use local workflow context and domain logic. Infrastructure-enforced safety can detect unsafe patterns at shared boundaries and apply consistent enterprise controls. Neither model replaces the other. Trusted AI governance requires both.

### Human oversight

Human oversight is not a failure fallback. It is a deliberate control point.
In many systems, human intervention is treated as an exception path. The automation fails, confidence drops, or an error occurs, and the system escalates. Agentic governance needs a stronger model. Human oversight should be designed as a seam in the architecture where the agent halts and asks before acting.

The enterprise has to define at what point a human must deliberately approve, reject, or redirect the agent. That depends on risk, authority, reversibility, cost, regulation, and business impact. Low-risk actions may proceed autonomously. Medium-risk actions may require review based on confidence, policy, or context. High-risk actions may always require approval. Some actions should not be delegated to agents at all.

Human oversight should be specific. The system should not ask a human to approve a vague recommendation without evidence. It should present the proposed action, the authority being used, the context considered, the policy decision, the risk score where available, and the expected consequence. 

A human approval is meaningful only when the human can understand what is being approved.

Human oversight also creates accountability. The goal is not to keep humans in every loop. The goal is to place humans at the points where judgment, accountability, and organizational risk require deliberate control.

### Policy authorship and distribution

Policy authorship and distribution form the backbone of trusted AI governance.

Agentic systems will operate across teams, domains, tools, geographies, models, and business processes. A centralized bottleneck cannot approve every action. At the same time, fully local governance creates inconsistency, weak auditability, and uneven regulatory coverage. The enterprise needs central policy and distributed enforcement.

This requires a clear control plane and data plane separation.

![figure 3: control plane data plane](/media/figure-3-cp-dp.png)

The control plane is where policy is authored, versioned, reviewed, distributed, and monitored. It captures enterprise obligations, regulatory requirements, risk appetite, sovereign constraints, identity rules, delegation rules, data handling requirements, human oversight thresholds, evidence requirements, and economic limits. The control plane should include regulatory obligations such as the EU AI Act, NIST AI RMF, ISO 42001, sector-specific rules, internal risk policies, and sovereign requirements.

The data plane is where policy is enforced. Enforcement happens at the distributed boundaries where agents interact with models, tools, data, systems, and other agents. The enforcement point should be close enough to the action to apply context, reduce latency, and preserve domain autonomy.

Agents need federated governance. Policy is centrally authored and distributed. Enforcement is local, contextual, and domain-aware. Domains retain autonomy in implementation, but they operate inside enterprise policy. The control plane provides consistency. The data plane provides scale.

Inline governance also belongs in this model. Domain teams will still need to implement local rules inside agent and application code. The control plane should not eliminate that. It should make local rules visible, consistent where required, and connected to enterprise policy. Infrastructure-enforced governance then applies common controls at shared boundaries. Together, these models give the enterprise both local intent and enterprise assurance.

This is the load-bearing architectural claim. Without the control plane and data plane split, AI governance becomes either too centralized to scale or too fragmented to trust.

### Observability and evidence

Observability is the evidence leg of trusted AI governance.

Traditional observability focuses on logs, metrics, and traces. Agentic observability must go further. It must capture what the agent was trying to do, what context it used, what authority it carried, what tools it called, what parameters were passed, what decisions it made, what policies were evaluated, what boundaries were enforced, whether it stayed in bounds, and where human oversight occurred.

Evidence must be useful to engineers, auditors, risk teams, security teams, compliance teams, and business owners. Each group asks a different question. Engineers need to debug behavior. Security teams need to detect abuse. Auditors need an accountable record. Risk teams need patterns and exposure. Business owners need to know whether the agent acted within its intended purpose.

Reasoning evidence must be handled carefully. Not every system will expose full chain-of-thought-style reasoning, and not every enterprise should retain sensitive reasoning artifacts. The governance requirement is not to store every internal token. It is to retain enough structured evidence to reconstruct the decision path, authority chain, tool usage, parameter values where appropriate, policy evaluation, and outcome.

Risk quantification sits on top of evidence. The evidence captures what the agent did. Risk quantification scores the likelihood and impact of that behavior into a graded signal. That signal can then be used by the control plane, human oversight, incident response, and business review.

Post-action audit is part of the governance loop. Evidence should not only support compliance review after the fact. It should feed back into boundary design, policy tuning, oversight thresholds, and runtime safety controls. Each audit should improve where the boundary is placed, what parameters are constrained, when a human is required, and what evidence must be captured next time.

Without evidence, governance becomes assertion. With evidence, governance becomes inspectable.

### Economic control

Cost is a governance dimension, not an operations afterthought.

Agents consume metered capacity non-deterministically. They loop. They retry. They fan out. They call models, tools, APIs, vector stores, search systems, workflow engines, and other agents. A single user request may trigger many downstream actions. A small design flaw can become a large bill. 

A malicious prompt can become an economic attack.
Economic control requires budgets, quotas, per-agent attribution, rate limits, throttling, and kill switches. The system must know which agent consumed capacity, under which authority, for which business purpose, and against which budget. It must be able to stop runaway behavior before it becomes operational or financial damage.

Economic control begins as a runtime mechanism: budgets, quotas, rate limits, throttling, and kill switches that prevent runaway consumption. At enterprise scale, those controls must mature into economic governance. Each agent should have a budget owner, a cost attribution model, and a link to the business process or customer outcome it supports. Without that ownership layer, rate limits only contain the damage. They do not answer whether the consumption was justified.

Economic control should not be treated as separate from safety and policy. A runaway loop is both an economic problem and a governance problem. Excessive fan-out can create cost, privacy, security, and reliability risk at the same time. The control architecture must treat consumption limits as part of the governed boundary.

## The integrated control architecture

The requirements are not independent controls. They form an integrated architecture.

Discovery finds the actors and surfaces they act on. Identity makes them addressable. Delegation defines whose authority they carry. Boundaries enforce policy where intent becomes action. Runtime safety evaluates whether authorized behavior is safe in context. Human oversight creates deliberate control points. Policy authorship and distribution provide central consistency with distributed execution. Observability and evidence prove what happened. Economic control bounds consumption and prevents runaway behavior.

The control plane and data plane separation is the core architectural pattern.

The control plane owns policy. It defines obligations, risk thresholds, delegation rules, access patterns, oversight requirements, evidence requirements, and economic limits. It provides a common language for governance across legal, security, compliance, engineering, architecture, and business teams. It does not need to execute every decision directly. Its role is to define, distribute, coordinate, and inspect.

The data plane enforces policy. It sits at the operational boundaries where agents interact with models, tools, data, APIs, workflows, and other agents. The data plane must be distributed because agents are distributed. Enforcement must happen near the action. That is where context exists. 

That is where latency matters. That is where domain autonomy must be preserved.

![figure 4: inline and infra enforced](/media/figure-4-inline-and-infra.png)

Inline governance and infrastructure-enforced governance fit into this architecture differently.

Inline governance lives inside the agent or application implementation. It is closest to the domain workflow. It can understand business intent, local state, user experience, and task-specific logic. It is necessary for domain-specific behavior, but it cannot be the only governance model because it depends on every team implementing controls consistently.

Infrastructure-enforced governance lives in the execution fabric around the agent. It is closest to the shared boundary. It can enforce common policy across model calls, tool calls, API calls, data access, and agent-to-agent communication. It provides the enterprise with a consistent enforcement surface, especially when it is parameter-aware.

The control plane must coordinate both. It should publish common policy, track which controls are enforced inline, track which controls are enforced through infrastructure, and collect evidence from both. Otherwise, governance will split into uncoordinated application logic on one side and generic infrastructure control on the other.

This architecture avoids two common failure modes.

The first failure mode is centralized approval theater. Every AI action is routed through a central governance process that cannot scale. Teams work around it. Shadow AI grows. Policy becomes disconnected from runtime behavior.

The second failure mode is local autonomy without enterprise control. Each team governs agents differently. Some enforce strong identity and evidence. Others rely on shared credentials and informal review. Regulatory obligations become inconsistent. Audit becomes fragmented. Risk accumulates in the seams.

A trusted AI governance architecture must avoid both. It must provide central policy, distributed enforcement, domain autonomy, and enterprise evidence.

The architecture also needs feedback. Evidence from the data plane should inform the control plane. Incidents should refine policy. Risk quantification should adjust oversight thresholds. Economic patterns should update budgets and quotas. Discovery should continuously update the inventory. 

Governance is not a one-time design review. It is a runtime operating model.

## Scope and intent

This capability model is intentionally vendor neutral. It does not define governance by product category. It defines governance by enterprise need.

The test is simple: the model should remain true even if no specific vendor existed. An enterprise still needs discovery. It still needs agent identity and delegation. It still needs boundary authorization. It still needs runtime safety. It still needs deliberate human oversight. It still needs central policy and distributed enforcement. It still needs evidence. It still needs economic control.

This paper also avoids treating governance as a single platform problem. Agentic systems will span multiple models, infrastructure providers, application platforms, integration layers, identity systems, observability systems, and business applications. Governance must work across that reality. 

A narrow product boundary cannot define the governance model.

The intent is to define the capability architecture first. Implementation mapping should come later. A companion implementation paper can map these capabilities to concrete systems, standards, products, and deployment patterns. That mapping should not change the underlying model.

That implementation mapping should also cover the engineering disciplines required to build and operate governed agents. Harness engineering focuses on the scaffolding around the model: prompts, tools, context, memory, evaluation, testing, and runtime controls. Agentic engineering extends that discipline to autonomous behavior: planning, delegation, tool use, human oversight, failure handling, and evidence generation. These are important implementation concerns, but they depend on the governance architecture defined here rather than replacing it.

The model is also not a claim that all agentic systems require the same level of control. Governance must be proportional. A low-risk summarization agent does not need the same oversight as an agent that approves refunds, changes infrastructure, updates medical records, transfers funds, or negotiates with external parties. The architecture must support graded control based on risk, authority, reversibility, regulation, and business impact.

The purpose of trusted AI governance is not to slow down engineering. It is to make agentic systems safe enough to scale. Without governance, adoption becomes fragile. With the right architecture, teams can move faster because the boundaries, evidence, and escalation points are clear.

## Conclusion

Agentic systems force a governance inversion.

![figure 5: gov runtime model](/media/figure-5-gov-runtime-model.png)

Deterministic systems can be governed largely through specification. Define the contract, verify the output, deploy the system, and monitor whether the contract holds. Agents do not provide that same assurance. Their outputs vary with input, context, tools, memory, delegation, and interaction. 

Pre-deployment verification still matters, but it cannot be the center of governance.

Trusted AI governance must govern where intent becomes action and must produce evidence after the action. The enterprise does not trust the model by itself. It trusts the architecture around the model.
That architecture begins with discovery. It depends on first-class agent identity and explicit delegation. It enforces policy at the boundaries of model traffic, tool and context access, and agent-to-agent interaction. It separates authorization from runtime safety. It treats human oversight as a deliberate seam. It authors policy centrally and enforces it at distributed boundaries. It captures evidence strong enough for audit and review. It treats cost as a governed dimension of agent behavior.

The model also requires clarity about enforcement. Inline governance is injected into the agent or application code path. Infrastructure-enforced governance is applied through the execution fabric around the agent. Inline governance gives domain teams local control. Infrastructure enforcement gives the enterprise consistent control at shared boundaries. Parameter-level enforcement makes that infrastructure control real.

The load-bearing pattern is the control plane and data plane split. Central policy without distributed enforcement becomes a bottleneck. Distributed enforcement without central policy becomes fragmentation. Inline governance without infrastructure enforcement becomes inconsistent. Infrastructure enforcement without inline context becomes coarse. Trusted AI governance requires all of these to work as one architecture.

The agent inherits trust from the architecture around it. That is the capability model enterprises need before agentic systems can operate at scale.

## References 

[1] Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md

[2] Abeysinghe, A. (2024, August 13). What’s happening to middleware in the Cloud-Native era? Forbes. https://www.forbes.com/councils/forbestechcouncil/2022/10/03/whats-happening-to-middleware-in-the-cloud-native-era/

[3] Magic Quadrant for AI Governance Platforms. (2026). In https://gartner.com (No. G00841467). Gartner. Retrieved July 9, 2026, from https://www.gartner.com/interactive/mq/8006369?ref=solrAll&refval=571598562

[4] EU Artificial Intelligence Act | Up-to-date developments and analyses of the EU AI Act. (n.d.). https://artificialintelligenceact.eu/

[5] AI Risk Management Framework | NIST. (2026, June 10). NIST. https://www.nist.gov/itl/ai-risk-management-framework

[6] AB 853: California AI Transparency Act. (2025, October 13). https://calmatters.digitaldemocracy.org/bills/ca_202520260ab853






