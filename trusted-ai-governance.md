<h1 align="center"> Trusted AI Governance </h1>
<h3 align="center"> An architectural thesis for governing agentic systems </h3>
<p align="center">
<i>
Version: Summer-2026<br/>
<b>First Published On: Summer-2026<br/>  </b>
</i>
</p>

**_Current Author_**

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
