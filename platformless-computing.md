<h1 align="center"> Platformless Computing </h1>
<h2 align="center"> Improving Enterprise Software Engineering with Platformless Computing </h2>
<p align="center">
<i>
Version: 0.9 (Fall-2023)<br/>
</i>
</p>

**_Authors_**

+ [Sanjiva Weerawarana, Ph.D.](https://www.linkedin.com/in/sanjivaweerawarana/) | Founder, CEO & Head of Products - [WSO2](https://wso2.com/) | [@sanjiva](https://x.com/sanjiva)
+ [Paul Fremantle, Ph.D.](https://www.linkedin.com/in/paulfremantle/) | Co-Founder, Founder CTO & Advisor - [WSO2](https://wso2.com/) | [@pzfreo](https://x.com/pzfreo)
+ [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO - [WSO2](https://wso2.com/) | [@asankama](https://twitter.com/asankama)


## Introduction

Many of the major shifts in the enterprise application space have happened due to radical simplification:
+ From client-server to web: not needing to worry about delivery and deployment of specific clients (“client-less”)
+ From datacenter to cloud: not needing to worry about hardware (“data-centre-less”)
+ From app server to serverless: not needing to care about which application server and having to manage clusters

When we talk about “-less” to indicate a shift, e.g. in serverless, it doesn’t really mean that there is no server. It simply means that there is such a clear boundary between the user and the provider that the user no longer needs to know about the system behind the service. For example, serverless backends still need clustering, failover, deployment, system upgrades, etc. However, the user of serverless doesn’t see any of that - they simply write and deploy code.

Recently there has been the rise of enterprise software delivery platforms. Often these build on Kubernetes or other cluster management systems, together with DevOps pipelines, monitoring and management systems as well as many other aspects. These platforms are incredibly powerful and allow organizations to deploy applications at scale and speed. More importantly, they enable updates to be deployed, rolled out incrementally, and rolled back if necessary. 

Platforms allow massive agility in improving application function and performance — which are characteristics closely associated with business success.

However, the platform has become a challenge in itself. These platforms require large, highly-skilled platform engineering teams, and the skills are hard to find. Each platform requires many complex choices and linkages between multiple systems - DevOps pipelines, deployment management, monitoring & management systems, network substrates, and of course the actual cluster management. 

<p align="center">
  <img src="/media/mindsharev3-15.png" alt="Tech. mindshare"/>
</p>
<p align="center">
  <i>
    Figure 1: Enterprise IT needs to increase focus on apps and less on the platform.
  </i>
</p>

We need a new paradigm to remove the platform from our consciousness and allow us to code, build, and deploy enterprise applications with fast deployment, continuous integration and rollout, and world-class monitoring and management - but with no need to see and manage the platform itself. Of course that doesn’t mean the platform vanishes completely - but by building the right boundary we can hide it and therefore remove the complexity it brings. We call this **“platformless”** computing. 

Platformless has the potential to be as big a shift as the web or cloud. Web reinvented the concept of a client. Cloud reinvented the concept of server hardware. Platformless reinvents the concept of server-side development and deployment.

## What is Platformless?

> **Platformless = APIs + Cloud Native + DevOps**

APIs are the fundamental building block of modern software. Cloud native is the modern approach for building distributed systems. DevOps and SRE are evolving into internal developer platforms to fully empower enterprise developers. 

This combination supports the full lifecycle of enterprise software engineering and delivers a platformless experience for the enterprise. Let us explore each of these in some detail.

> **Creating in a platformless world:**
> *Maria, a lead developer at TechFirm Alpha, is tasked with integrating the company's in-house CRM system with multiple external e-commerce platforms. Knowing the complexity and time this could take, she logs into the Platformless dev environment. Navigating to its built-in marketplace, Maria is greeted with many pre-built connectors and tools tailored for tasks like hers. Among the offerings, she identifies connectors for her CRM's APIs A and B. Additionally, connectors for the external e-commerce platforms, APIs D and E, catch her eye. Maria employs these connectors, and using a seamless integration process, she stitches together her desired workflow in hours. The Platformless architecture ensures every interaction adheres to a rigorous zero-trust security model. Building her prototype, she's able to test, refine, and share her work with stakeholders, all while using the Platformless runtime environment intrinsic monitoring, tracing, and debugging utilities. By leveraging the Platformless experience, Maria expedites a potentially weeks-long project into a matter of days, all without compromising on security or functionality. As Maria iterates, the app can go live with a full, scalable production runtime.*

### APIs
Adopting an **"API-first"** approach has become the gold standard for enterprise architecture to deliver the benefits of the API economy approach to enterprise computing. 

This entails several critical capabilities:
1. API design and development time governance to help organizations prevent repeated redevelopment of the same functionality and also to create reusable functionality. 
2. Reuse of APIs, events and data products of the organization via marketplaces.
3. Runtime governance of APIs and events to ensure safe and secure usage, accountability and compensation.

Enterprise IT typically builds and operates this infrastructure using best of breed technologies for each component, often at heavy cost and delays. At the same time, this layer of technology does not offer any competitive advantage for most businesses. Instead, platformless delivers this infrastructure as “part of the woodwork” and allows developers to build assuming these capabilities.

### Cloud native 

Cloud-native practices stand as a pillar of the Platformless Environment. At its heart lies the Domain Driven Design (DDD) and modular [Cell-based Architecture (CBA)](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md), aligning business requirements with software solutions. Domains in this context are comprehensive, offering APIs, events, and data to ensure cohesive yet loosely coupled systems. With the microservices architecture, applications are split into optimal granularity, manageable services that operate independently, ensuring scalability and agility. Complementing this is the service mesh, which provides enhanced service-to-service communication, addressing challenges in interservice communication in microservices deployments. Security, vital in any setting, is managed through authentication (Authn) and authorization (Authz), ensuring proper access controls. Furthermore, with cloud-native architecture and middleware, there's a focus on flexibility, resilience, and scalability, utilizing the cloud's full potential. All these elements collectively set the stage for the Platformless Environment, where seamless integration, security, and scalability converge.

### DevOps
In the Platformless approach, DevOps emerges as the central pulse, streamlining and magnifying every process for peak efficiency. One of the foremost principles is self-service. By emphasizing developer autonomy, DevOps ensures that teams can deploy, manage, and access vital resources without any hindrance or reliance on centralized units. This approach not only hastens the developmental timeline but nurtures a profound culture of ownership and responsibility.

Next, we delve into version and release management. In the fluid world of contemporary software deployment, managing versions and guaranteeing seamless releases is paramount. Within the Platformless model, robust versioning tools are at play, documenting every change, keeping a meticulous track, and offering a safeguard by allowing rollbacks when necessary. Moreover, dedicated release management utilities ensure that software rollouts occur without a hitch, always keeping stakeholders in the loop.

Diving into security, the zero-trust model stands as the Platformless structure's backbone. Each interaction, be it internal or from an external source, is perceived with a lens of skepticism. This demands rigorous authentication and authorization checks for every single access request, safeguarding the sanctity and privacy of both resources and data.

Lastly, the essence of observability in the Platformless framework can't be understated. It goes beyond traditional monitoring, providing teams with an in-depth, detailed view of both applications and the underlying infrastructure. This capability allows for the early detection of inefficiencies, anomalies, and even preemptive identification of potential challenges. It’s a shift from merely gathering data to extracting actionable insights, ensuring the ecosystem is always tuned to its optimal state. 

Together, these intertwined DevOps principles shape the Platformless model into an environment where agility complements security, efficiency aligns with independence, and the mantra of continuous improvement resonates throughout.

## Platformless Facilitates Enterprise Software Engineering

Enterprise software engineering is more complex than building independent products because enterprises are complex organisms with competing interests that must somehow be hidden when a customer engages with the business. Further, as businesses become digital businesses, they need to produce not one piece of software but a large complex collection of software products that work together. The aim is to digitize the business and support both human users (as web/mobile/desktop apps), and non-human users (as network APIs), as well as programs that work with no external involvement (as jobs or automations). A large enterprise will often have thousands or even tens of thousands of such digital assets that need to work together.

The aim of platformless is to enable enterprises to build and deliver digital experiences without the platform becoming the challenge. To succeed, platformless must enable building systems that span business domains, APIs, events, automations, workflows and of course apps. It must support modularity, beautiful architecture, reuse and security. And of course it must have world-class delivery: fast deployment, continuous integration and rollout, incisive monitoring and intuitive management. 

<p align="center">
  <img src="/media/platformless-architecture-15.png" alt="Tech. mindshare"/>
</p>
<p align="center">
  <i>
   Figure 2: Modern distributed systems easily built and operating in a platformess environment
  </i>
</p>

## Conclusion

Software Delivery platforms and runtime platforms have had an amazing impact on the speed of delivery and scalability of enterprise applications and systems. But these were the forerunners for a simpler, more effective model. Platformless computing takes away the complexity of these systems while retaining and improving the experience for everyone involved in building, deploying and running enterprise applications. Most importantly, Platformless delivers even better applications to customers. 

## References

1. Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md
2. Compuware, Mike Burba. 2003. “Delivering the Holy Grail of Software Development.” Computerworld. October 22, 2003. https://www.computerworld.com/article/2572523/delivering-the-holy-grail-of-software-development.html.
3. Abeysinghe. A. 2023a. “Internal Developer Platform:  A Technical Reevaluation.” WSO2. October 2023. https://github.com/wso2/reference-architecture/blob/master/internal-developer-platform.md. 
