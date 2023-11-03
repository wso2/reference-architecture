<h1 align="center"> Platformless </h1>
<h2 align="center"> Improving Enterprise Software Engineering with Platformless Computing </h2>
<p align="center">
<i>
Version: 0.8 (Fall-2023)<br/>
</i>
</p>

**_Authors_**

+ [Sanjiva Weerawarana, Ph.D.](https://www.linkedin.com/in/sanjivaweerawarana/) | Founder, CEO & Head of Products - [WSO2](https://wso2.com/) | [@sanjiva](https://x.com/sanjiva)
+ [Paul Fremantle, Ph.D.](https://www.linkedin.com/in/paulfremantle/) | Co-Founder, Founder CTO & Advisor - [WSO2](https://wso2.com/) | [@pzfreo](https://x.com/pzfreo)
+ [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO - [WSO2](https://wso2.com/) | [@asankama](https://twitter.com/asankama)


## Introduction

Radical simplification is at the heart of many major shifts in the enterprise application space:
+ **From client-server to web**: not needing to worry about delivery and deployment of specific clients (“client-less”)
+ **From datacenter to cloud**: not needing to worry about hardware (“data-centre-less”)
+ **From app server to serverless**: not needing to care about which application server and having to manage clusters

Now the need for radical simplification is driving the next major shift: from 
**platforms** to **“platformless.”**

Of course, when we talk about “-less” to indicate a shift, e.g. in serverless, it doesn’t really mean that there is no server. It simply means that there is such a clear boundary between the user and the provider that the user no longer needs to know about the system behind the service. For example, serverless backends still need clustering, failover, deployment, system upgrades, etc. However, the user of serverless doesn’t see any of that; they simply write and deploy code.

In this article, we examine the challenges that organizations face with enterprise software delivery platforms, provide a definition of platformless, and discuss how a platformless approach facilitates enterprise software engineering.

## The Problem with Platforms

Recently we have seen the rise of enterprise software delivery platforms. Often these build on Kubernetes or other cluster management systems, together with DevOps pipelines and monitoring and management systems among many other aspects. These platforms are incredibly powerful and allow organizations to deploy applications at scale and speed. More importantly, they enable updates to be deployed, rolled out incrementally, and rolled back if necessary. 

Platforms allow massive agility in improving application function and performance — which are characteristics closely associated with business success.

However, platforms have introduced their own challenges. They require large, highly-skilled platform engineering teams, and the skills are hard to find. Each platform requires many complex choices and link between multiple systems: DevOps pipelines, deployment management, monitoring and management systems, network substrates, and of course the actual cluster management.

<p align="center">
  <img src="/media/mindsharev6-15.png" alt="Tech. mindshare"/>
</p>
<p align="center">
  <i>
    Figure 1: Enterprise IT needs to increase focus on applications and less on the platform.
  </i>
</p>

It is clear that we need a new paradigm to remove the platform from our consciousness and allow us to code, build, and deploy enterprise applications with fast deployment, continuous integration and rollout, and world-class monitoring and management - but with no need to see and manage the platform itself. That doesn’t mean the platform vanishes completely. Rather by building the right boundary we can hide it and therefore remove the complexity it brings. We call this **“platformless”** computing. 

Platformless has the potential to be as big a shift as the web or cloud. Web reinvented the concept of a client. Cloud reinvented the concept of server hardware. Platformless reinvents the concept of server-side development and deployment.

## What is Platformless?

Platformless computing is founded on four technology disciplines, which we can think of as an equation. 

**Platformless = API-First + Cloud Native Middleware + Platform Engineering + Developer Experience**

APIs are the fundamental building block of modern software. Cloud native middleware is the runtime infrastructure needed for building and running cloud native distributed systems. Platform engineering builds [internal developer platforms (IDP)](https://github.com/wso2/reference-architecture/blob/master/internal-developer-platform.md) combining DevOps and site reliability engineering (SRE) to fully empower enterprise developers. Within a platformless environment, an exceptional developer experience(DX) not only boosts developer productivity but also optimizes mean time to detect (MTTD) and mean time to repair (MTTR), ensuring rapid issue identification and swift resolution, thereby streamlining operations and enhancing system reliability.

This combination supports the full lifecycle of enterprise software engineering and delivers a platformless experience for the enterprise. Consider the following example: 

> **Creating in a platformless world:**
> + *Maria, a lead developer at TechFirm Alpha, is tasked with integrating the company's in-house customer relationship management (CRM) system with multiple external e-commerce platforms.* 
> + *Knowing the complexity and time this could take, she logs into the Platformless dev environment. Navigating to its built-in marketplace, Maria is greeted with many pre-built connectors and tools tailored for tasks like hers.* 
> + *Among the offerings, she identifies connectors for her CRM's APIs A and B.
Additionally, connectors for the external e-commerce platforms, APIs D and E, catch her eye.* 
> + *Maria employs these connectors, and using a seamless integration process, she stitches together her desired workflow in hours. The platformless architecture ensures every interaction adheres to a rigorous zero-trust security model.* 
> + *Building her prototype, she's able to test, refine, and share her work with stakeholders, all while using the platformless runtime environment intrinsic monitoring, tracing, and debugging utilities.* 
> + *By leveraging the platformless experience, Maria expedites a potentially weeks-long project into a matter of days, all without compromising on security or functionality.* 
> + *As Maria iterates, the app can go live with a full, scalable production runtime.*

Now, let’s explore the three foundational elements of platformless — API-first, cloud native middleware, platform engineering and developer experience (DX) — in more detail.

### API-First

Adopting an **"API-first"** approach has become the gold standard for enable an enterprise architecture to deliver the benefits of the API economy approach to enterprise computing. 

This entails three critical capabilities:

1. API design and development time governance help organizations prevent repeated redevelopment of the same functionality and instead create reusable functionality. 
2. The avilability of APIs, events, and data products of the organization via marketplaces facilitates reuse.
3. Runtime governance of APIs and events to ensure safe and secure usage, accountability, and compensation.

Enterprise IT typically builds and operates this infrastructure using best-of-breed technologies for each component, often at heavy cost and delays. At the same time, this layer of technology does not offer any competitive advantage for most businesses. Instead, platformless delivers this infrastructure as “part of the woodwork” and allows developers to build assuming these capabilities are in place.

### Cloud Native Middleware

Cloud native is widely accepted as the approach for building distributed systems that execute in modern containerized, multi-cloud distributed environments. Building and deploying cloud native systems requires several design and architecture approaches and runtime systems. These include domain-driven design, cell-based architecture, microservices architecture, service meshes, integrated authentication and authorization, and operating in a zero trust environment.

[Domain-driven design (DDD)](https://martinfowler.com/bliki/DomainDrivenDesign.html) and multi-level modularity [cell-based architecture (CBA)](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) help align business requirements with software solutions. Domains in this context are comprehensive, offering APIs, events, and data to ensure cohesive yet loosely coupled systems. With microservices architecture, applications are split into optimal granularity, with manageable services that operate independently, ensuring scalability and agility.

Complementing this at runtime is the service mesh, which provides enhanced service-to-service communication, addressing challenges in interservice communication in microservice deployments and improving the resiliency of distributed systems. Security, vital in any setting, is managed through authentication and authorization, ensuring proper access controls. Further the operating environment for all the systems must be a zero-trust environment.

Cloud native middleware brings focus on flexibility, resilience, and scalability, utilizing the cloud's full potential. All these elements collectively set the operating environment for Platformless, where seamless integration, security, and scalability converge.

### Platform Engineering

In the platformless approach, platform engineering emerges as the central pulse, streamlining and magnifying every process for peak efficiency. One of the foremost principles is self-service. By emphasizing developer autonomy, DevOps ensures that teams can deploy, manage, and access vital resources without any hindrance or reliance on centralized units. This approach not only hastens the developmental timeline but also nurtures a profound culture of ownership and responsibility.

Next, is version and release management. In the fluid world of modern software deployment, the ability to manage versions and guaranteeing seamless releases is paramount. Within the platformless model, robust versioning tools are at play, documenting every change, keeping meticulous track, and offering safeguards by allowing rollbacks when necessary. Moreover, dedicated release management utilities ensure that software rollouts occur without a hitch, always keeping stakeholders in the loop.

The zero-trust model stands as the platformless structure's security backbone. Each interaction, whether internal or from an external source, is perceived with a lens of skepticism. This demands rigorous authentication and authorization checks for every single access request, safeguarding the sanctity and privacy of both resources and data.

Lastly, the essential nature of observability in platformless can't be overstated. It goes beyond traditional monitoring, providing teams with an in-depth, detailed view of both applications and the underlying infrastructure. This capability allows for early detection of inefficiencies, anomalies, and even preemptive identification of potential challenges. It’s a shift from merely gathering data to extracting actionable insights, ensuring the ecosystem is always tuned to its optimal state.

Together, these intertwined platform engineering principles shape the platformless model into an environment where agility complements security, efficiency aligns with independence, and the mantra of continuous improvement resonates throughout.

### Developer Experience

There is one more dimension to consider in platformless computing. In the platformless paradigm, developer experience (DX) takes center stage. At its core, DX revolves around offering developers a seamless and intuitive environment, tailoring their interactions to ensure efficiency and productivity. An integral part of this is the provision of versatile tools such as integrated development environments (IDEs), command-line interfaces (CLIs), and straightforward API access. These tools not only simplify the creation of cloud-native components but also streamline debugging, testing, and deployment processes. The essence of Platformless is to eliminate cumbersome setups and hurdles, ensuring that developers have an unparalleled experience from the initial stages of crafting applications to their final deployment. 

In a platformless setting, DX provides developers with a pipeline-tuned sandbox for frictionless application development, access to shared resources via a marketplace, and autonomy through cell-based architecture, all while the self-service approach empowers them to provision essential development resources effortlessly.

This commitment to amazing DX ensures that every touchpoint within the platformless environment resonates with developers' needs, optimizing their journey and fostering innovation.

## Platformless Facilitates Enterprise Software Engineering

Now, let’s look specifically at how platformless computing can facilitate enterprise software engineering. 

Enterprise software engineering is more complex than building independent products because enterprises are complex organisms with competing interests that must somehow be hidden when a customer engages with the business. Further, as organizations become digital businesses, they need to produce not one piece of software but a large complex collection of software products that work together. The aim is to digitize the business and support human users (as web/mobile/desktop apps), non-human users (as network APIs), and programs that work with no external involvement (as jobs or automations). A large enterprise will often have thousands or even tens of thousands of such digital assets that need to work together.

The aim of platformless is to enable enterprises to build and deliver digital experiences without the platform becoming the challenge. To succeed, platformless must enable building systems that span business domains, APIs, events, automations, workflows, and of course apps. It must support modularity, beautiful architecture, reuse, and security. It must also have world-class delivery: fast deployment, continuous integration and rollout, incisive monitoring, and intuitive management. 

<p align="center">
  <img src="/media/platformless-architecturev2-15.png" alt="platformless architecture"/>
</p>
<p align="center">
  <i>
   Figure 2: Modern distributed systems easily built and operating in a platformess environment
  </i>
</p>

## Conclusion

Software delivery platforms and runtime platforms have had an amazing impact on the speed of delivery and scalability of enterprise applications and systems. But these were the forerunners for a simpler, more effective model. Platformless computing takes away the complexity of these systems while retaining and improving the experience for everyone involved in building, deploying, and running enterprise applications. Most importantly, Platformless delivers even better applications to customers. 

## References

1. Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md
2. Compuware, Mike Burba. 2003. “Delivering the Holy Grail of Software Development.” Computerworld. October 22, 2003. https://www.computerworld.com/article/2572523/delivering-the-holy-grail-of-software-development.html.
3. Abeysinghe. A. 2023a. “Internal Developer Platform:  A Technical Reevaluation.” WSO2. October 2023. https://github.com/wso2/reference-architecture/blob/master/internal-developer-platform.md. 
4. Fowler, Martin. n.d. “Bliki: DomainDrivenDesign.” Martinfowler.Com. https://martinfowler.com/bliki/DomainDrivenDesign.html.
