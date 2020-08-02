<h3 align="center"> API-Centric Centralized Reference Architectures</center></h3>
<h1 align="center"> Layered and Segmented Architecture</center></h1>

<p align="center">
<i>
Version Summer-2020<br/>
</i>
</p>

**_Original Author_**

+ Asanka Abeysinghe | Chief Technology Evangelist | WSO2, Inc | <asankaa@wso2.com>

> *Enterprises depend on API-driven strategies to bring about digital transformation. The benefits include increased productivity, simplification, seamless connectivity, and rich experiences through digital channels. Connecting humans, things, applications, systems, and data is a fundamental requirement to become a digitally-driven organization, city, or country. APIs are the digital connectors that act as the glue for various digital assets. As a result, the business and technical architecture moved to API-centric from service-orientation. The primary focus of this paper is to look at the architecture approaches taken by the industry and represent these patterns as generic reference architectures. We identified two centralized reference architectures, i.e., layered and segmented, and we will discuss them in detail.*

## An API-Centric Architecture Approach

Digital transformation forced organizations to expose their capabilities in standard and easy-to-access ways. As a result, (managed) APIs became the norm to access business data and functionalities. Every architecture took an API-first approach and was augmented to support the same. Most enterprises followed the layered approach for a while and subsequently moved to segmented architecture with the rise of microservices. This paper focuses on these two centralized API-centric architecture patterns.  

## Abstractions

| Icon | Name | Description |
|---------|---------|---------|
|![Person](/media/ra-ls-component-10.png)| Component |In this architecture, any runtime is treated as a component. A component is an atomic unit. It can represent data, data abstraction, business logic, an end-user application, etc. |
|![Layer](/media/ra-ls-layer-20.png )| Layer| A layer is a grouping of a set of similar components and creates a clear boundary at design time and runtime. Layers are stacked on one another.|
|![DFlow](media/ra-ls-dflow-20.png)| Data flow| The data flow represents how information is exchanged between each layer. Data flows sequentially (without bypassing) based on how the layers are stacked.|
|![Segment](/media/ra-ls-segment-20.png )| Segment|The subgrouping of components within a layer or across a number of layers.|
|![API](/media/ra-ls-api-20.png )| API|An **A**pplication **P**rogramming **I**nterface. They can represent edge, domain, and utility APIs.|



## The Evolution of API-Centric Architecture 

![evolution of api architecture](/media/ra-ls-api-evo.png)

Single-tier Architecture: As we discussed earlier, application systems started as being centralized and single-purpose, with user interfaces, business logic, and data bundled together as a single layer. If you have built systems using Cobol and RPG (3G programming languages), you would have experienced how to generate user interfaces (forms) by pointing to a data set and building business logic directly interacting with the record sets and user interface. To run complex logic and data manipulation, business processes had to be scheduled in a queue and were executed sequentially (FIFO). 3G programming languages, ISAM databases, and mainframes were some of the technical elements in the single-tier era. 

Two-Tier Architecture: Following the advancements in data storage and data access mechanisms (database management systems xDBMS), data layers were separated from user interfaces and business logic.  As a result, two layers were introduced at the design, implementation, runtime, and administration. A new role was introduced to a database administrator (DBA). The user interface (UI) and the business logic was tightly coupled with the data but was logically and physically separated into two layers. Developers used programming languages such as Clipper, dBASEIII, and PowerBuilder to implement systems using two-tier architecture.  

Three-Tier Architecture: The introduction of various distributed computing technologies for information exchange and data access led to the three-tier architecture by separating the user interfaces, business logic, and data into individual tiers. Information exchange technologies (such as OLE, COM, COM+, DCOM, ActiveX, CORBA, and RMI/IIOP) and data access technologies (like OLE-DB, ODBC, DAO, and JDBC) introduced the power and linking capabilities of a three-tier architecture. Three-tier architecture became popular during this time, and data centers had application servers and database servers while user interfaces ran in the desktop computers of the users. Also, three types of developers operated in this model as backend developers (who develop business logic) and frontend developers (who develop user interfaces) and database administrators (DBAs). To strengthen this pattern, a number of frameworks came into the market, such as Enterprise Java Beans (EJB) and Microsoft.Net. 

Model View Controller (MVC): Web-based applications were enhanced in the dotcom era, and, as a result, a web-friendly MVC architecture pattern was introduced. The MVC approach held on to the three-tier architecture by changing the layer-to-layer data flow to a triangular flow. In principle, three-tier architecture does not recommend the UI layer directly accessing the data. The MVC pattern changed this by allowing the UI to interact with the data layer directly. This was further improved with the introduction of MVC-2.

N-Tier Architecture: Smart devices added another application type—mobile apps. As a result, three-tier architecture moved to n-tier, and this allowed architects to add many system layers based on application needs. For example, some systems introduced the client logic layer and made the web and mobile apps thin clients. Also, the n-tier approach moved data logic out of the core data storage and introduced a new data processing and manipulating layer. Data flow moved back to the layer-to-layer sequential flow. 

Service-Oriented Architecture (SOA): Web services standardized distributed system calls by introducing interface definitions (contracts) and message formats, which were initially XML based. In addition, web services simplified remote procedure calls and brought in the concept of business interfaces and business data. As a result, a new architecture layer was added to the n-tier architecture: the services layer. As the entire architecture was created based on services, it was named service-oriented architecture. Later on, services were categorized as data services, business services, composite services, etc., and each service category represented an architecture layer. SOA was further improved with the addition of many sub-architecture patterns, such as event-driven architecture (EDA) and web-oriented architecture (WOA). 

>***This paper mainly focuses on the layered and segmented architecture(s) defined after SOA.***

Microservice Architecture (MSA): The theory behind microservices proposed a decentralized and non-layered architecture. However, most enterprises that adopted MSA ended in a layered architecture once they started reusing existing systems and data as well as the added quality of services. 

One of the main motivations behind the [**Cell-Based Architecture**](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) **(CBA)** was to find the right reference architecture to enable MSA outside a layered approach. Cell-Based Architecture is an API-led decentralized reference architecture that is compliant with Microservice Architecture (MSA) and Cloud-Native Architecture (CNA). 


### Influence from Other Concepts

#### System of Systems (SoS)

The system of systems concept groups the functionality and the teams (people) associated with delivering the functionality. The system of record, system of operations, system of engagement, and system of intelligence are a few high-level classifications that derive into subsystems based on the size and the complexity of the overall system. 

#### Introduction of New Usage Patterns 

There were various usage patterns that were introduced from time to time-based on functionality enhancements. As an example, API management introduced an API gateway layer, identity and access management (IAM), and analytics moved to a centralized service layer. At the same time, infrastructure-related operations moved to an infrastructure as a service layer. These patterns influenced the shape of layered architecture.  

## Layered Architecture

For nearly two decades, reference architectures primarily focused on layers, where comparable functional capabilities were grouped into layers by following the SoS approach. Centralized data moved from one layer to another. Layered architecture not only created architecture and technology layers but it also created a culture, an organization structure, and a new way for how teams operate.
There are pros and cons to using this pattern. We position this as part of the emerging architecture pattern by considering enterprises that are moving from brownfield to greenfield and heavy usage of this pattern on the systems already built and providing a digital experience for consumers. 

Layered architecture is a natural progression based on how hardware and software systems have evolved, which started from tightly coupled, centralized, and single-purpose systems to distributed (centralized) multi-functional systems and modern decentralized any-functional systems. 

The movement of hardware and software, in addition to the hierarchical and centralized setup of the organization structure, was also an excellent fit for layered architecture. In such an organization, sub-teams are disconnected and operate as silos. Centralized, layered architecture helps these disconnected teams to connect by making the centralized system the source of truth. 

### An Overview of Layered Architecture

![Layered architecture](/media/ra-ls-layered-ov-25.png)

As noted at the beginning of this paper, in a layered architecture, components are the atomic units. Components that provide similar functional capabilities are grouped into layers. Layers are arranged as a stack.

The number of layers is not fixed. However, at least three layers introduced by the three-tier architecture (presentation, logic, and data) exist in most layered architecture approaches. The complexity of the systems and the level of distribution (separation of concerns), introduced sub-layers to the basic three layers. 

Data flow in a sequential manner from one layer to another. As a result, two layers cannot bypass a layer in between. Different message exchange patterns (MEPs) can be used to exchange data between each layer. An architect can use one or a combination of different MEPs. For example, request-response and publish/subscribe (pub/sub) MEPs can be used to exchange data between layers.  
Developers working on and responsible for a layer experience the same behavior from the two layers surrounding it.


### Layered Architecture with SOA

![Layered SOA](/media/ra-ls-layered-soa-25.png)

The above diagram represents a common layered architecture used by architects that used SOA to implement systems. However, this is not an architecture diagram used at the beginning of SOA—rather it presents an architecture after the SOA concepts were well established in the industry. Initial SOA concepts were built using a triangular web services model and consisted of a service provider, service registry or discovery, and a service consumer. 

Architects extended the triangular model by following one of the fundamental concepts of SOA "decoupling" and grouped the decoupled functional capabilities into layers. Organizations modeled their teams and reporting structures to fit into the layered architecture and each layer became an individual team or even a business unit. 

### Improved Layered Architecture with SOA: August-2011 

![Layered SOA2](/media/ra-ls-layered-soa-2-orig.png)

>*In fall 2015, I was involved in defining the future state architecture for a leading European automobile company. The company’s chief architect visited our office in California, and we started the project by taking the standard SOA-based layered architecture defined in the previous section. After a full working day and many whiteboard diagrams, we realized that single-dimensional layers could not represent the full architecture landscape we wanted. We started day two by extending the layered architecture to one that was multi-dimensional by bringing in application lifecycle stages and quality of services into separate dimensions. This allowed us to group cross-cutting concerns into different blocks within the layers and address a broader scope of capabilities.*

The system of systems concept influenced this architecture as the foundation. Also, concepts such as Gartner's pace layered architecture and the functionality richness expected by the enterprise architecture considered heavily while defining this pattern.  
We used this pattern to build many systems in medium to large enterprises, and still, many architects refer to this as a logical pattern. 
Let's go through each layer in detail. 

Source System of Record (SSoR): This is the layer that physically stores data. Different types of data storage can represent this layer. In reality, enterprises use heterogeneous data storage added with the time based on the internally and externally built systems introduced. This storage can vary from SQL, NoSQL, file system, to cloud storage, or a combination of these.

System of Record (SoR): This layer is responsible for managing and maintaining data stored in the SSoR layer. Typically a core system application represents this layer by encapsulating the SSoR. 

Data Virtualization: This layer allows access to the SoR or multiple SoRs by building business objects. Data manipulation tools and technologies, such as master data management (MDM) and extract, transform, load (ETL), reside in this layer. Object-relational mapping (ORM), data services introduced by SOA, data APIs, and new data lakes implemented using data caches can be new additions. 

Service-Oriented Architecture (SOA): The SOA layer contains the business logic and processes that expose the business capabilities as services. Traditional web service standards or RESTful service standards use this layer to define the interfaces on accessing the services. 

Application Programming Interfaces (APIs): Data and business functionalities are exposed in secure and standard ways via (managed) APIs. The application developer only sees the APIs as the way to perform create/read/update/delete (CRUD) operations and execute business processes. APIs encapsulate the complexity of the underlying systems and data and provide a pure abstraction. 

System of Engagement: This is the layer that human interaction happens through various applications, such as web and mobile applications. As we identified before, applications are built by consuming (managed) APIs. There can be a system-to-system interaction, and device interaction through IoT (Internet of Things) can represent this layer, in addition to human-centric applications. Even robotics is a candidate to represent this layer. 

As explained previously, the difference between this layered architecture compared to the standard layered diagrams is the multi-dimensional aspect of it. So let's look at the horizontal view of the same. 

System of Automation: Infrastructure, infrastructure as a service (IaaS), and virtualization of hardware, such as the physical location of different runtimes, runs in this layer. Besides, a supportive process of application lifecycle management, such as continuous integration (CI), continuous deployment (CD), infrastructure as a code, and various DevOps automation, represents this layer. This layer runs across the vertical layers we looked in the previous sections. 

Application lifecycle stages (develop/publish/consume and run): Tools and actions bound with development sandbox environments are represented in the development layer. Once the application advances from the development by successfully passing the relevant quality tests, it gets promoted to the publishing stage. Publishing can proceed to a relevant listing (store or registry) as well as to an application composite repository. In some cases, it can be just a branch or a tag in the source control system, which contains a separate build pipeline. Application usage outside development and testing can be found in the consume and run layer. The production-ready versions of applications are represented here. In addition to the applications, the dependent runtimes in each vertical layer are presented from bottom to top (data to screen). 

Quality of Services (QoS): We identified three primary quality of services in this architecture, which can engage at the runtime separated from the core application and business logic. Securing, governing, and monitoring the applications and business logic are added as separate horizontal layers. 

The layered architecture described above does not look interesting for current greenfield projects that follow concepts such as microservices and cloud-native. The reality is that a majority of enterprises cannot take a 100% greenfield approach; it is a mix of brownfield and greenfield. Therefore, a multi-dimensional layered architecture is still used as a reference architecture to build large distributed systems. The next section explains a way to enhance this approach to address greenfield architecture requirements. 

### Layered Architecture with Microservice Architecture (MSA): February-2014

The term microservices was coined by Dr. Peter Rogers in 2005; however, it was adopted as an architecture pattern that could be applied to build production-ready systems in 2011. Best practices and guidelines provided by technology evangelists like Martin Fowler and organizations that adopted the principles, such as Netflix and Uber, made it famous in the architecture community. 

However, architects found it difficult to apply all the theories associated with microservice architecture during that period. Development teams started writing microservices when they revamped existing services or when introducing new services. At the same time, greenfield projects started adopting microservices. But those microservices had to fit into the overall application architecture due to various reasons, such as fetching data, integrating with business processes, and even producing data to various end-user applications residing in the system of the engagement layer. As a result, microservices became another layer in layered architecture. The following diagram explains how microservices fit into the layered architecture during the early stage. 

![Layered MSA](/media/ra-ls-layered-msa.png)

Primarily the business logic and integration logic focused on service composition (orchestration and choreography) moved to microservices. The centralized nature of the runtime, dependency with multiple application architecture layers, and hypervisor-based and bare-metal infrastructure did not support the flexibility and depth required for MSA. Container-based infrastructures were there at that time, such as Linux Containers (LXC) and Warden, but they were not mature enough to run production systems. 

To break the limitations identified above, application and DevOps architects came up with a workaround. This is the birth of segmented architecture. 

## Segmented Architecture

### An Overview of Segmented Architecture

Organizations started moving to a podular architecture with small agile teams adapting to agile methodologies. Different terms were used to define these teams. Pods, two-pizza teams, and scrum teams are a few examples of this, and we call them [**self-organized teams**](https://github.com/wso2/reference-methodology/blob/master/reference-methodology.md#self-organized-teams). From a technical perspective, microservice architecture, virtualization, and containers helped these autonomous teams to operate successfully. Some teams started bypassing corporate IT and moved to their hosting options, such as public clouds. We call it 'Shadow IT.' To avoid Shadow IT, responsive IT concepts were introduced by corporate IT teams, and segmented architecture is a result of that.  

The fundamental concept behind layered architecture did not change in segmented architecture. However, segmented architecture introduced more freedom for application development teams than layered architecture by creating isolation and ownership of runtimes by partitioning using segments. 

Segments were created based on how each enterprise was organized; in some cases, it was based on the business units, a set of functionality delivered to larger application systems,  or center of excellence (CoE) teams. The team owns the segment and has access to the segment in different environments associated with the lifecycle of the application, such as development, testing, staging, and production. 



