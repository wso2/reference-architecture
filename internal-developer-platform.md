<h1 align="center"> Internal Developer Platform </h1>
<h3 align="center"> A Technical Reevaluation </h3>
<p align="center">
<i>
Version: 0.7 (Fall-2023)<br/>
</i>
</p>

**_Author_**

+ [Asanka Abeysinghe](https://www.linkedin.com/in/asankaabeysinghe/) | CTO - [WSO2, LLC](https://wso2.com/) | [@asankama](https://twitter.com/asankama)



> *In the ever-evolving field of software development and delivery, the term "Internal Developer Platform" has often been confined to delivery and infrastructure automation. This narrow understanding overlooks crucial components, including application architecture, development, and production runtime. This article aims to correct this misinterpretation by offering a more comprehensive and nuanced definition. Through an in-depth analysis, this article will explore the multifaceted nature of internal developer platforms, breaking down the misconceptions and providing a well-rounded view that resonates with technical decision-makers and software application architects. By focusing on the real scope and potential of these platforms, we will shed light on what they truly encompass, extending beyond the conventional boundaries to reveal the complete landscape of modern software development practices.*

## What is a Platform?

Think of a platform like a train station or an airport: a centralized location that facilitates the coming and going of various activities and transactions, enhancing the experience and productivity. In this context, Dave Gray's definition becomes particularly resonant: **"A platform is a supporting structure that increases the effectiveness of a community."**

![platform real world](/media/platform-real-world.png)

In technology terms, a platform serves as a foundation or a framework that enables the development, deployment, and scaling of applications. It provides a set of tools, services, and capabilities that can be leveraged for various phases of software or product lifecycle. A well-architected platform abstracts complexities, offers reusable components, and enables interoperability between disparate systems. More than just a piece of technology, it's an ecosystem that influences both operational efficiencies and strategic capabilities. Understanding what a platform is at its core sets the stage for grasping the more specialized roles that specific types of platforms, like Internal Developer Platforms, play in technology ecosystems.

![platform](/media/platform-20.1.png)

In the above diagram, the platform is represented as a foundation, serving as the base upon which all other activities and functions rest. Sitting atop the platform are interlinked squares labeled as 'Pods' or 'Domains.' These serve as compartments or subdivisions that group related functions and activities. Within each Pod or Domain, you'll find circles labeled as 'Components.' These components represent the individual workloads or tasks that the platform is designed to manage or execute. Just as in a train station, where different platforms serve specific train lines and each train has its specific compartments and cargo, this diagram illustrates how a technology platform organizes various workloads into logical groups (Pods/Domains), making it easier to manage, scale, and deploy them. The encapsulation within Pods or Domains provides an additional layer of organization, facilitating more efficient governance and operational management.

### Platform: the enterprise abstraction for enhanced productivity and simpicity 
In software development, abstractions offer simplicity and convenience. They enhance our creative efforts by providing intuitive interfaces, hiding the underlying complexities, and empowering us to work at higher levels of understanding and productivity. In this context, a platform serves as a critical abstraction layer that enterprises can leverage to achieve these benefits.

### Quadruple layers of enterprise abstractions
Hand in hand with software abstractions we must also embrace the power of enterprise abstractions to unlock the full potential of our creative endeavors in the software industry. These abstractions are specifically designed to tackle the unique challenges and complexities of the enterprise landscape, enabling us to develop scalable, secure, and efficient solutions that drive business success. By leveraging these enterprise abstractions, we can build robust architectures, streamline business processes, and transform the way organizations operate in the digital age.

To understand enterprise abstractions, it is useful to review "The Quadruple Layers: Levels of Enterprise Abstractions," which has emerged as a guiding principle. This powerful framework contains four key layers in which each layer represents a distinct level of abstraction — deployment, middleware, business, and domain — that contributes to the overall efficiency and effectiveness of enterprise systems.

![the quadruple layers](/media/enteprise-abstractions.png)

#### Deployment Abstractions
Deployment abstractions encompass a wide range of practices and tools that facilitate efficient application hosting and deployment within an enterprise environment. These abstractions include continuous integration/continuous deployment (CI/CD), DevOps, GitOps, SecOps, observability, multi-cloud strategies, zero-trust security measures, scalability, and high availability. Collectively, these deployment abstractions form the foundation for efficient, secure, and scalable enterprise software deployments, empowering organizations to meet the demands of modern technology landscapes.

#### Middleware Abstractions
Middleware abstractions serve as the intermediary layer that facilitates communication and data management between deployment and business abstractions. They play a key role in system integration, enabling seamless data flow and connectivity between disparate parts of an enterprise system. Middleware abstractions include elements like message brokers, API gateways, and data transformation tools.

#### Business Abstractions
Business abstractions encompass a set of concepts and practices that focus on modeling and automating core business processes within an enterprise. These abstractions include services or microservices, functions, APIs, events, data, and more. They form the building blocks for designing and implementing agile, scalable, and modular enterprise solutions, allowing organizations to respond to changing market needs quickly and efficiently.

#### Domain Abstractions
Domain abstractions, a subset of business abstractions, play a crucial role in tailoring software solutions to specific industry or domain requirements. These abstractions are grouped according to teams and capabilities, as guided by Conway's Law. By aligning software design with the boundaries of the business domain, domain-driven design (DDD) allows teams to develop a deep understanding of the problem space and create focused, autonomous teams. This empowers teams to deliver tailored software solutions that address the unique needs and complexities of their industry or domain with speed, flexibility, and scalability.


## RISE OF THE INTERNAL DEVELOPER PLATFORM


## REFERENCES 

[1] Weerawarana, S., Dr. (2021, December 7). What Are the Right Abstractions for Cloud-Native Deployment? https://wso2.com/summits/. https://wso2.com/blogs/thesource/right-abstractions-cloud-native-deployment/

[2] How do Internal Developer Platforms (IDPs) relate to other concepts? (2023, February 9). Internal Developer Platform. https://internaldeveloperplatform.org/how-do-internal-developer-platforms-relate-to-other-concepts/

[3] Liebenberg, C. (n.d.). How to Design an Internal Developer Platform. https://blog.container-solutions.com/how-to-design-an-internal-developer-platform

[4] Fowler, M. (n.d.-b). bliki: Conway’s Law. martinfowler.com. https://martinfowler.com/bliki/ConwaysLaw.html

[5] Vernon, V. (2013). Implementing Domain-driven Design. Pearson Education https://www.pearson.com/en-us/subject-catalog/p/implementing-domain-driven-design/P200000009616/9780133039887

[6] Abeysinghe, A., & Fremantle, P. (2018, June). Cell-based architecture: A decentralized reference architecture for cloud-native applications. https://github.com/wso2/. https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md

[7] Gray, Dave, and Thomas Vander Wal. 2014. The Connected Company. O’Reilly Media https://www.oreilly.com/library/view/the-connected-company/9781449336622/



[def]: /media/platform-real-world.png