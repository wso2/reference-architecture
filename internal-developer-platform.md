<h1 align="center"> Internal Developer Platform </h1>
<h3 align="center"> A Technical Reevaluation </h3>
<p align="center">
<i>
Version: 0.7 (Fall-2023)<br/>
</i>
</p>

**_Author_**

+ [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO - [WSO2, LLC](https://wso2.com/) | [@asankama](https://twitter.com/asankama)



> *In the ever-evolving field of software development and delivery, the term **"Internal Developer Platform"** (IDP) has often been confined to delivery and infrastructure automation. This narrow understanding overlooks crucial components, including application architecture, development, and production runtime. This article aims to correct this misinterpretation by offering a more comprehensive and nuanced definition. Through an in-depth analysis, this article will explore the multifaceted nature of internal developer platforms, breaking down the misconceptions and providing a well-rounded view that resonates with technical decision-makers and software application architects. By focusing on the real scope and potential of these platforms, we will shed light on what they truly encompass, extending beyond the conventional boundaries to reveal the complete landscape of modern software development practices.*

## What is a Platform?

Think of a platform like a bustling train station or an efficiently organized airport. These are not just transit points for the comings and goings of travelers. They are complex, multi-layered ecosystems that provide a wide array of services and functions. From shops, restaurants, and cafes to information kiosks, lounges, and even art installations, these hubs are miniature cities in themselves.

These elements don't exist in isolation; they interact and support each other. For instance, the information kiosk helps you find your way to the right terminal or track; the lounges offer a comfortable waiting area; the shops and eateries cater to your immediate needs, and digital displays keep you updated on schedules and delays. Each component serves a particular role, contributing to a seamless experience that accommodates a multitude of needs and preferences.

Moreover, these platforms are constantly evolving. New services are introduced, layouts are optimized, and feedback is actively collected to adapt to the changing requirements of the community they serve—travelers, employees, service providers, and more.

In essence, real-world platforms like these are supporting structures built to increase the effectiveness and productivity of a large and diverse community, mirroring Dave Gray's apt definition: 

> **"A platform is a supporting structure that increases the effectiveness of a community."** 

Whether it's about guiding, informing, feeding, or entertaining, each element within these platforms is fine-tuned to contribute to a harmonious, effective ecosystem.

![platform real world](/media/platform_new_40.png)

In technology terms, a platform serves as a foundation or a framework that enables the development, deployment, and scaling of applications. It provides a set of tools, services, and capabilities that can be leveraged for various phases of software or product lifecycle. A well-architected platform abstracts complexities, offers reusable components, and enables interoperability between disparate systems. More than just a piece of technology, it's an ecosystem that influences both operational efficiencies and strategic capabilities. Understanding what a platform is at its core sets the stage for grasping the more specialized roles that specific types of platforms, like Internal Developer Platforms, play in technology ecosystems.

![platform](/media/platform-20.1.png)

In the above diagram, the platform is represented as a foundation, serving as the base upon which all other activities and functions rest. Sitting atop the platform are interlinked squares labeled as 'Pods' or 'Domains.' These serve as compartments or subdivisions that group related functions and activities. Within each Pod or Domain, you'll find circles labeled as 'Components.' These components represent the individual workloads or tasks that the platform is designed to manage or execute. Just as in a train station, where different platforms serve specific train lines and each train has its specific compartments and cargo, this diagram illustrates how a technology platform organizes various workloads into logical groups (Pods/Domains), making it easier to manage, scale, and deploy them. The encapsulation within Pods or Domains provides an additional layer of organization, facilitating more efficient governance and operational management.

## Modern technology platform requirements 

In today's digital age, customer experiences are the driving force behind organizational differentiation. These experiences are increasingly delivered through software, blurring the lines between traditional industry categories. Whether you're in retail, healthcare, hospitality, or any other sector, your organization is, in essence, also a software company.

![application lcm](media/lcm-full-15.1.png)

A modern technology platform should, therefore, be capable of designing, creating, and delivering these unique digital experiences. This goes far beyond merely offering a set of APIs or an environment where code can be executed. A comprehensive platform addresses the end-to-end life cycle of application development, starting from business architecture and extending to application architecture, application development, and testing.

But the life cycle doesn't stop at deployment. A robust platform must also offer tools for running and operating these applications, ensuring they meet performance, security, and scalability requirements. Lastly, it must facilitate the gathering of feedback and insights, enabling continuous improvement and adaptation. This comprehensive approach ensures that the platform serves not merely as a set of disjointed tools but as a cohesive ecosystem enabling organizations to be agile, innovative, and customer-centric.

By encompassing the full spectrum of application development, from ideation to operation, modern platforms empower organizations to deliver differentiated experiences effectively and efficiently. Therefore, when evaluating technology platforms, the ability to support this complete life cycle should be a prime consideration.

In addition to covering the full stages of an application's lifecycle, the table below outlines key aspects that a modern technology platform should address. These are essential components that enable organizations to be agile, innovative, and customer-centric, shaping how they design, develop, deliver, and operate software.

| Digital infrastructure              | Architecture             |
|-----------------------------|------------------------------------------------------------|
| Containerization & Kubernetes, Serverless operation, Multi-environment, Multi-cloud, CI/CD, GitOps, Observability & alerting, Configuration management, Firewall/load balancing/geo routing/DNS, Multi-region deployment, API management, Developer self-service, Cost optimization, Insights - business and management | API-first development, Reuse and API marketplace, Domain-driven development, Microservice architecture, Version management, Release management, Authentication & authorization, Large language models and AI  |


### The enterprise abstraction for enhanced productivity and simpicity 

As technologists, we are in the business of building experiences, and every line of code we write contributes to shaping those experiences. In this sense, the software industry is akin to the movie industry, where creativity thrives and innovation takes center stage. Just as filmmakers use storytelling techniques, cinematography, and special effects to captivate audiences, software developers rely on powerful abstractions to unleash their creative potential and deliver remarkable experiences. 

In software development, abstractions offer simplicity and convenience. They enhance our creative efforts by providing intuitive interfaces, hiding the underlying complexities, and empowering us to work at higher levels of understanding and productivity. In this context, a platform serves as a critical abstraction layer that enterprises can leverage to achieve these benefits.

### Quadruple layers of enterprise abstractions
Hand in hand with software abstractions we must also embrace the power of enterprise abstractions to unlock the full potential of our creative endeavors in the software industry. These abstractions are specifically designed to tackle the unique challenges and complexities of the enterprise landscape, enabling us to develop scalable, secure, and efficient solutions that drive business success. By leveraging these enterprise abstractions, we can build robust architectures, streamline business processes, and transform the way organizations operate in the digital age.

To understand enterprise abstractions, it is useful to review "The Quadruple Layers: Levels of Enterprise Abstractions," which has emerged as a guiding principle. This powerful framework contains four key layers in which each layer represents a distinct level of abstraction — deployment, middleware, business, and domain — that contributes to the overall efficiency and effectiveness of enterprise systems.

![the quadruple layers](/media/enteprise-abstractions.png)

#### Deployment abstractions
Deployment abstractions encompass a wide range of practices and tools that facilitate efficient application hosting and deployment within an enterprise environment. These abstractions include continuous integration/continuous deployment (CI/CD), DevOps, GitOps, SecOps, observability, multi-cloud strategies, zero-trust security measures, scalability, and high availability. Collectively, these deployment abstractions form the foundation for efficient, secure, and scalable enterprise software deployments, empowering organizations to meet the demands of modern technology landscapes.

#### Middleware abstractions
Middleware abstractions serve as the intermediary layer that facilitates communication and data management between deployment and business abstractions. They play a key role in system integration, enabling seamless data flow and connectivity between disparate parts of an enterprise system. Middleware abstractions include elements like message brokers, API gateways, and data transformation tools.

#### Business abstractions
Business abstractions encompass a set of concepts and practices that focus on modeling and automating core business processes within an enterprise. These abstractions include services or microservices, functions, APIs, events, data, and more. They form the building blocks for designing and implementing agile, scalable, and modular enterprise solutions, allowing organizations to respond to changing market needs quickly and efficiently.

#### Domain abstractions
Domain abstractions, a subset of business abstractions, play a crucial role in tailoring software solutions to specific industry or domain requirements. These abstractions are grouped according to teams and capabilities, as guided by Conway's Law. By aligning software design with the boundaries of the business domain, domain-driven design (**DDD**) allows teams to develop a deep understanding of the problem space and create focused, autonomous teams. [**Cell-based Architecture**](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) can serve as an effective implementation strategy for these domain abstractions. This empowers teams to deliver tailored software solutions that address the unique needs and complexities of their industry or domain with speed, flexibility, and scalability.


![platform in enteprise](/media/ep-abstractions-20.png)

In the diagram above, we provide a granular view of the "Quadruple Layers: Levels of Enterprise Abstractions" within a typical enterprise context. The visualization showcases how each abstraction layer — Deployment, Middleware, Business, and Domain — interacts and aligns with various technologies, users, and components integral to an enterprise. This detailed breakdown serves to elucidate the complexity and interconnectivity across the layers, giving you a comprehensive insight into how these abstractions collectively form the backbone of enterprise software architecture.

#### Digital channels for enteprise abstractions 
With the establishment of the Quadruple Layers of Enterprise Abstractions, which now include Deployment, Middleware, Business, and Domain layers, organizations gain a comprehensive foundation for constructing robust and efficient applications across various digital channels. These channels encompass web, mobile, Internet of Things (IoT), and other emerging platforms.

Websites and web applications provide a digital interface accessible through browsers, enabling users to interact and consume services. Mobile applications offer a personalized and on-the-go experience, leveraging the capabilities of smartphones and tablets. The Internet of Things (IoT) adds connectivity to everyday objects, facilitating seamless interactions and data exchange. Emerging technologies like virtual reality (VR), augmented reality (AR), and mixed reality (MR) introduce new realms of immersive experiences.

By tapping into the power of these digital channels and the four underlying layers of enterprise abstractions, organizations can develop innovative, user-centric applications that meet a variety of needs and preferences. This adaptability enables them to remain competitive in a swiftly changing digital landscape.

The emergence of platform engineering—focused on designing and building toolchains and workflows for software development teams' self-service—underscores the growing importance of creating flexible, modular, and composable tech solutions. While the upside is clear, enterprises must weigh the financial and resource implications of such undertakings. Building and maintaining these complex platforms require careful assessment of costs, challenges, and the presence of viable alternatives.


## Rise of the internal developer platform (IDP)
Enterprise abstractions, also known as the platform that CIOs are building, are collectively referred to as the internal developer platform (IDP). The IDP serves as a centralized foundation for the organization's software development and delivery processes, and it provides a comprehensive set of tools, services, and abstractions that enable development teams to work efficiently and effectively. Notably, the IDP encompasses all three enterprise abstraction layers: deployment, business, and domain, providing a holistic framework for building, deploying, and managing applications. 

By leveraging the IDP, organizations can streamline their software development lifecycle, foster collaboration among teams, and accelerate the delivery of high-quality applications. The IDP empowers developers by offering self-service capabilities, automation, observability, and scalability so they can focus on innovation and deliver exceptional digital experiences. As CIOs recognize the need for these enterprise abstractions, the IDP emerges as a strategic investment that transforms the way organizations develop and deliver software solutions.

## Traditional IDP definition

The current definition of the IDP, as outlined by [internaldeveloperplatform.org](https://internaldeveloperplatform.org/what-is-an-internal-developer-platform/), can be summarized as follows:
The IDP is designed to provide a framework and set of tools to support software development within an organization. It encompasses several core components and capabilities, including application configuration management, infrastructure orchestration, environment management, deployment management, and role-based access control. These components collectively contribute to streamlining the software development process, enhancing collaboration, and accelerating the delivery of high-quality applications. 

| Core Capability               | Short Description                                           |
|-----------------------------|------------------------------------------------------------|
| Application Configuration Management | Manage application configuration in a dynamic, scalable, and reliable way.  |
| Infrastructure Orchestration | Orchestrate your infrastructure in a dynamic and intelligent way depending on the context.                  |
| Environment Management       | Enable developers to create new and fully provisioned environments whenever needed.                               |
| Deployment Management        | Implement a delivery pipeline for Continuous Delivery or even Continuous Deployment (CD).                            |
| Role-Based Access Control   | Manage who can do what in a scalable way.                  |

*source [internaldeveleporplatform.org](https://internaldeveloperplatform.org/core-components/)*


## The imperative to redefine the internal developer platform
With the complete application lifecycle and the four layers of enterprise abstractions already outlined, we're in a strong position to pinpoint the real-world demands on an enterprise platform. These foundational aspects serve as guideposts, directing us toward a more meaningful and relevant understanding of what a sophisticated, enterprise-grade platform should offer. They create a framework that can be used to evaluate, choose, or build a platform that stands up to the multifaceted challenges and requirements that modern enterprises face.

![lcm covered by current def](/media/lcm-current-15.png)

Current definitions of an Internal IDP largely confine themselves to a portion of the application lifecycle, primarily focusing on the delivery aspect. While delivery is undeniably crucial, it represents just one stage in a much more expansive lifecycle. This narrow focus leaves out important phases such as initial business and application architecture, development, testing, and ongoing operations. As a result, the existing IDP definitions fall short of addressing the comprehensive needs that modern enterprises have across the complete application lifecycle.

Additionally, it's crucial to point out that existing IDP definitions largely focus on the deployement layer, one of the four quadruple layers of enterprise abstractions we've previously detailed—deployment, middleware, business, and domain. Such a limited scope leaves out the complexity and essential functions of the other three layers. By doing so, it omits crucial elements like middleware services that facilitate communication and data management, as well as business and domain abstractions that align software capabilities with organizational objectives. Consequently, the conventional understanding of IDP provides a fragmented view, creating gaps that could lead to vulnerabilities and inefficiencies in a complex enterprise setting.

Given these shortcomings in the prevailing IDP definitions, there's a pressing need for a redefined IDP that aligns more closely with the full spectrum of enterprise needs. This redefinition should cover not only all stages of the application lifecycle but also adequately address all four layers of enterprise abstractions—deployment, middleware, business, and domain. A comprehensive IDP would thus offer a more holistic, enterprise-grade solution capable of tackling the complexities and challenges of modern organizations.

## A new definition of internal developer platform (IDP)

So, what is missing in the current definition of the IDP? To fully support the application development process, organizations need to consider the broader context of the business and application architecture, as well as the iterative feedback loops that facilitate continuous improvement and innovation.

By expanding the definition of the IDP to include the following ten areas in addition to the features covered by the existing definition, organizations can unlock the true potential of the IDP, enabling end-to-end collaboration, efficient development processes, and the delivery of exceptional software solutions.

Application architecture, development and testing tooling: The prevailing definition of an Internal Developer Platform (IDP) often falls short in encompassing key aspects like application architecture, development, and test tooling. These essential features, while overlooked in many conventional interpretations, are integral to a holistic understanding and implementation of a true IDP. A real IDP embraces these components, embedding them directly into developers' favorite IDEs, such as VSCode. This seamless integration not only fosters a cohesive development environment but also ensures that the entire software lifecycle, from initial design to testing and deployment, is streamlined and efficient. By recognizing and incorporating these crucial elements, and making them readily accessible within popular development environments, a real IDP transcends mere automation, shaping a platform that resonates with the complexity and demands of modern software development and delivery.

| New Capability               | Short Description                                           |
|-----------------------------|------------------------------------------------------------|
| **Foundational technology components for cloud native application development:** | APIs, integration, services, and identities are crucial foundational technology components for cloud native application development, and are therefore essential features for an IDP. These components enable developers to create, connect, deploy, and secure modern applications for cloud environments, resulting in faster and more efficient software development processes. Incorporating these components into an IDP allows development teams to build the digital core and deploy cloud native applications with greater speed, scalability, and security. |
| **API-first** | API management: API management is a critical feature for an IDP as it enables centralized management and control of APIs, ensuring their security, reliability, and scalability. With API management, developers can create, monitor, and manage APIs with ease, promoting collaboration and innovation among development teams. *API-driven:* An essential characteristic of a robust Internal Developer Platform (IDP) is its API-driven architecture. Both the architecture and development processes within the IDP must be governed by well-designed APIs, serving as the building blocks that ensure flexibility and coherence. Additionally, an IDP must expose clear system APIs, allowing seamless extensions of its capabilities. This API-centric approach not only aligns with modern software engineering practices but also enables organizations to tailor the platform to specific needs, facilitating integration, enhancing control, and promoting innovation. Moreover, the integration of a secured CLI can further extend the system API functionality, making it more developer-friendly and providing additional ease of use and customization. In essence, an API-driven IDP embodies a future-ready approach, turning the platform into a versatile tool that can adapt and evolve with the ever-changing technology landscape. |
| **Reusability, composability, and sharing:** | Using a marketplace to facilitate reusability, composability, and the sharing of software components is a must-have feature for an IDP. A marketplace enables development teams to discover and reuse existing components, promoting collaboration and innovation while reducing costs and time to market. |
| **Version management:** | Version management is another missing piece in the current IDP definition. It enables tracking, controlling, and managing different versions of applications, libraries, and dependencies. Proper version management ensures seamless transitions, rollback options, and compatibility maintenance. By incorporating strong version management capabilities, the IDP empowers developers to maintain control, collaborate effectively, and deliver high-quality software products that meet evolving needs. |
| **Communication policies and security controls:** | Communication policies and security controls are key requirements for an enterprise-grade IDP as they ensure the secure operation and protection of sensitive business information. By providing robust communication policies and security controls, an IDP can ensure that software development processes are secure and compliant, while also promoting collaboration and innovation among development teams internally and externally. |
| **Grouping of workloads for agile teams:** | The grouping of workloads for agile teams is a critical feature for an IDP as it aligns development teams with business capabilities, promotes collaboration, and facilitates the delivery of high-quality software. This approach is based on Conway's Law and is also aligned with the principles of DDD and cell-based architecture. |
| **Observability and business analytics:** | Observability and business analytics are critical features for an IDP, providing developers with insights into the behavior and impact of their applications, while also enabling businesses to make data-driven decisions. By incorporating these features, development teams can make more informed decisions and improve the quality and value of their software, while businesses can gain valuable insights into user engagement, revenue, and customer satisfaction. |
| **Full self-service:** | Full self-service is a must-have requirement for an enterprise-grade IDP, providing development teams with complete control over the application lifecycle. This promotes agility, innovation, and collaboration, reducing costs and increasing productivity. |
| **Compliance:** | An enterprise-grade IDP should comply with industry standards, such as System and Organization Controls 2 (SOC2), Federal Information Processing Standard 140-2 (FIPS 140-2), and Federal Risk and Authorization Management Program (FedRAMP), to ensure data security and privacy. Compliance with these regulations provides the assurance that cryptographic modules are secure and reliable, and the IDP meets the highest standards for data security and privacy. Additionally, compliance with other standards such as General Data Protection Regulation (GDPR), Health Insurance Portability and Accountability Act (HIPAA), and Payment Card Industry Data Security (PCI-DSS) is essential for an IDP to support the compliance requirements of enterprises. Overall, a key requirement of an ideal IDP for an enterprise is to provide assurance that the data and applications are secure and comply with industry and regulatory standards. |
| **SaaS:** | raditional interpretations of an Internal Developer Platform (IDP) often omit a crucial aspect: the necessity for the IDP itself to be a SaaS (Software as a Service) offering. In the newly framed definition of an IDP, being delivered as a SaaS offering isn't just an added feature; it's fundamental. This approach aligns with the agility, scalability, and accessibility that modern software development requires. By defining the IDP as a SaaS offering, organizations can leverage the benefits of cloud computing, enjoy seamless updates, and gain the ability to scale resources according to needs, all within a manageable subscription model. This vision of an IDP reflects a shift towards more flexible and adaptive platforms, capable of meeting the diverse and evolving needs of today's development teams and the organizations they support. |
| **Best practices:** | A notable gap in conventional definitions of an Internal Developer Platform (IDP) is the absence of inbuilt best practices for application architecture, development, testing, and deployment. These best practices are not mere supplementary features; they are integral to creating an IDP that truly serves the needs of modern development teams. An IDP that inherently incorporates these best practices ensures a consistent, efficient, and effective approach across all stages of the software lifecycle. It standardizes processes, reduces errors, and facilitates collaboration, allowing developers to focus on innovation rather than wrestling with inconsistencies. By defining an IDP that includes these inbuilt best practices, we move towards a platform that not only supports the technical aspects of development but also nurtures a culture of excellence, quality, and continuous improvement within the organization. |
| Core capabilities | application configuration management, infrastructure orchestration, environment management, deployment management, and role-based access control |


## Conclusion

The IDP represents a transformative approach to software development and operations, providing organizations with the means to streamline their processes and drive innovation. As a unified platform that spans the entire software development lifecycle, it empowers development teams to operate with agility while improving security, compliance, and cost-effectiveness. However, adopting an IDP requires careful consideration of an organization's unique needs and requirements.

To fully reap the benefits of an IDP, organizations should seek a platform that is fully self-service, enabling teams to rapidly access and provision the necessary resources. It needs to support agile teams by providing the flexibility to iterate and adapt to changing requirements. Emphasizing reusability and composability, the IDP should also enable teams to leverage existing components and build upon them. Additionally, the platform should provide observability and business analytics to facilitate data-driven decision-making and continuous improvement.

Compliance with industry and regulatory standards is crucial for ensuring that the IDP meets security and governance requirements. Considering the complexity and rapid evolution of technology, organizations can benefit from purchasing an off-the-shelf IDP from a reputable vendor. This approach reduces the burden of building and maintaining an IDP internally and allows organizations to focus their developers on creating unique business abstractions.

By adopting the new IDP paradigm, organizations position themselves to innovate with speed and agility, outpace the competition, and achieve their business goals. The IDP serves as a catalyst for delivering high-quality digital experiences, enabling organizations to simply **"JUST ADD DEVELOPERS"** and unleash their full potential in the digital landscape.

## References 

[1] Weerawarana, S., Dr. (2021, December 7). What Are the Right Abstractions for Cloud-Native Deployment? https://wso2.com/summits/. https://wso2.com/blogs/thesource/right-abstractions-cloud-native-deployment/

[2] How do Internal Developer Platforms (IDPs) relate to other concepts? (2023, February 9). Internal Developer Platform. https://internaldeveloperplatform.org/how-do-internal-developer-platforms-relate-to-other-concepts/

[3] Liebenberg, C. (n.d.). How to Design an Internal Developer Platform. https://blog.container-solutions.com/how-to-design-an-internal-developer-platform

[4] Fowler, M. (n.d.-b). bliki: Conway’s Law. martinfowler.com. https://martinfowler.com/bliki/ConwaysLaw.html

[5] Vernon, V. (2013). Implementing Domain-driven Design. Pearson Education https://www.pearson.com/en-us/subject-catalog/p/implementing-domain-driven-design/P200000009616/9780133039887

[6] Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md

[7] Gray, Dave, and Thomas Vander Wal. 2014. The Connected Company. O’Reilly Media https://www.oreilly.com/library/view/the-connected-company/9781449336622/

[8] Abeysinghe, A. 2023. “Why Building a Platform May Not Be Your Best Bet - Exploring Five Critical Reasons : @VMblog.” VMblog.Com. October 6, 2023. https://vmblog.com/archive/2023/10/06/why-building-a-platform-may-not-be-your-best-bet-exploring-five-critical-reasons.aspx.



[def]: /media/platform-real-world.png