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


# Introduction

Many of the major shifts in the enterprise application space have happened due to radical simplification:
+ From client-server to web: not needing to worry about delivery and deployment of specific clients (“client-less”)
+ From datacenter to cloud: not needing to worry about hardware (“data-centre-less”)
+ From app server to serverless: not needing to care about which application server and having to manage clusters

When we talk about “-less” to indicate a shift, e.g. in serverless, it doesn’t really mean that there is no server. It simply means that there is such a clear boundary between the user and the provider that the user no longer needs to know about the system behind the service. For example, serverless backends still need clustering, failover, deployment, system upgrades, etc. However, the user of serverless doesn’t see any of that - they simply write and deploy code.

Recently there has been the rise of enterprise software delivery platforms. Often these build on Kubernetes or other cluster management systems, together with DevOps pipelines, monitoring and management systems as well as many other aspects. These platforms are incredibly powerful and allow organizations to deploy applications at scale and speed. More importantly, they enable updates to be deployed, rolled out incrementally, and rolled back if necessary. 

Platforms allow massive agility in improving application function and performance — which are characteristics closely associated with business success.

However, the platform has become a challenge in itself. These platforms require large, highly-skilled platform engineering teams, and the skills are hard to find. Each platform requires many complex choices and linkages between multiple systems - DevOps pipelines, deployment management, monitoring & management systems, network substrates, and of course the actual cluster management. 

![focus shift](/media/mindshareV3.png)
*Figure 1: Enterprise IT needs to increase focus on apps and less on the platform.*

We need a new paradigm to remove the platform from our consciousness and allow us to code, build, and deploy enterprise applications with fast deployment, continuous integration and rollout, and world-class monitoring and management - but with no need to see and manage the platform itself. Of course that doesn’t mean the platform vanishes completely - but by building the right boundary we can hide it and therefore remove the complexity it brings. We call this “platformless” computing. 

Platformless has the potential to be as big a shift as the web or cloud. Web reinvented the concept of a client. Cloud reinvented the concept of server hardware. Platformless reinvents the concept of server-side development and deployment.
