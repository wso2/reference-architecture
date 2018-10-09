# Reference Architecture for Agility
+ Asanka Abeysinghe, Vice President - Architecture, CTO Office | asankaa@wso2.com
+ Paul Fremantle, CTO and Co-Founder | paul@wso2.com

>>>> This document describes a reference architecture for modern agile digital enterprises. This reference architecture offers a logical architecture based on a disaggregated cloud-based model that can be instantiated to create an effective and agile approach for digital enterprises, deployed in private, public or hybrid cloud environments. In this paper we present the architecture, the approach to applying this architecture, and existing approaches that fit into this architecture. The architecture defined in this paper can be mapped to current architectures as well as used to define new architectures. It is designed to help move from the “as-is” towards the “to-be”.

## Introduction

Enterprise architecture has one main aim-to bring structure and organization to evolving systems, thus enabling better maintainability, flexibility, and agility. Enterprise architects have the unending task of trying to bring order to chaos. Over the past five years, a rapid shift has taken place in the agility of software development and in particular DevOps. As a result, continuous integration and continuous deployment (CI/CD) approaches have dramatically accelerated the time needed for new deployments of software projects from months to weeks to days to hours. In many ways, enterprise architectures have struggled to adjust. This reference architecture aims to enable an agile enterprise by increasing the agility at the project level and take it to the enterprise level.
This architecture is based on experience working across hundreds of projects on building digital systems. It also offers a forward-looking view aimed at addressing emerging challenges. The aim of this architecture is to enhance agility at the enterprise level. We define agility as the ability of an organization to respond effectively and in good time to changes in the business environment, in customer requirements, or in enterprise strategy. Agility is not just about one-time changes. It's about ongoing, repeated adaptation to meet the challenges of the enterprise. In creating agility, we assert that four properties are key:

+ **Scalaility**, the ability to deal with changing workloads by utilizing available resources and effectively maintaining a service level. Modern cloud infrastructure allows components, such as containers, to be scaled effectively, provided they are designed in the correct manner

+ **Modularity**, is the idea that components of the architecture are versioned, replicable, and have well-defined interfaces. It is about exposing the right interfaces into a versioned system as well as hiding the details of the internal workings.

+ **Composability**, is about creating a recursive and uniform architecture where new components and capabilities add to the overall platform in a seamless way. For example, adding business logic in a web page makes it hard for other systems to build on top of that logic, whereas adding the same logic to an API allows web applications, mobile apps, and other server-based systems to access that logic.

+ **Governance**, is about building managed, monitored, resilient systems and ensuring that organizational policies are enforced.

The rest of the this paper is structured as follows:

+ **Section 1**: Introduces the overall abstractions used.

+ **Section 2**: Introduces to the units of an enterprise architecture.

+ **Section 3**: Defines the new reference architecture. This includes a mapping to a real-world example.

+ **Section 4**: Discusses structured agility and looks at how the reference architecture augments an iterative architecture.

+ **Section 5**: Looks at how the reference architecture supports enterprise features.

+ **Section 6**: Examines the overall picture by describing the agile business from the business architecture point of view.

## Section 1: Abstractions
