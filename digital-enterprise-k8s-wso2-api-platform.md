<h1 align="center"> Reference Implementation for a Cloud-Native Digital Enterprise </center></h1>
<p align="center">
<i>
Version Winter-2020<br/>
</i>
</p>

**_Original Author_**

+ Lakmal Warusawithana | Senior Director - Technology Evangelism | WSO2, Inc | <lakmal@wso2.com> | [@lakwarus](https://twitter.com/lakwarus)

> *This paper presents a reference implementation for a cloud-native digital enterprise architecture described in the [Reference Architecture for a Cloud-Native Digital Enterprise](https://github.com/wso2/reference-architecture/blob/master/reference-cloud-native-architecture-digital-enterprise.md). We will focus on an implementation using Kubernetes and WSO2’s API-led integration platform.*

## Introduction

The recent constraints on businesses have pushed organizations to accelerate their plans for moving operations to the digital world—often shrinking timelines from years to months. In the process, APIs have emerged as the products of the 21st century. As discussed in the [Reference Architecture for a Cloud-Native Digital Enterprise](https://github.com/wso2/reference-architecture/blob/master/reference-cloud-native-architecture-digital-enterprise.md), the combination of cloud-native technologies and an API-led integration platform significantly increases productivity by enabling agility, flexibility, and scalability through automation and services.

This paper discusses a reference implementation for a cloud-native digital enterprise using two industry-leading, open-source technology stacks: [Kubernetes](http://kubernetes.io) and [WSO2’s API-led integration platform](http://wso2.com). 

## Reference Implementation: A Cloud-Native Digital Enterprise 

<p align="center">
<img src="https://github.com/lakwarus/reference-architecture/raw/master/media/ra-reference-implementation-digital-enterprise.png">
<br> 
<i>Figure 1 - Cloud-Native Digital Enterprise</i>
</p>

In this reference implementation, Kubernetes provides the cloud-native platform capabilities, and WSO2’s API-led integration solution offers the required integration and API management capabilities for a digital enterprise.

Kubernetes can install on top of any private, public, or hybrid cloud infrastructure. WSO2’s API-led integration platform (WSO2 API Manager and WSO2 Enterprise Integrator) can be installed on top of Kubernetes with native support through the WSO2 Kubernetes API Operator. This native integration provides the necessary automation, scalability, and operations as well as giving API-led integration capabilities.

## Kubernetes

Kubernetes, an open-source cloud-native orchestration platform or a framework, provides a complete set of cloud-native abstractions and a toolkit to build a scalable, flexible solution that aligns with business growth. It is a mature open-source project that is governed by the Cloud Native Computing Foundation (CNCF). Kubernetes’ rich cloud-native abstractions help define the scalable architecture. Its toolkit helps to orchestrate containerized applications into a multi-host, multi-cloud distributed platform by providing the necessary infrastructure and automation. 

The Kubernetes architecture consists of a control-plane and a set of worker nodes. Typically, control-plane components deploy in master (control-plane) nodes, and work-loads deploy on worker nodes. The control-plane is responsible for storing information regarding nodes, monitoring the nodes, container workload scheduling, etc. If you are new to Kubernetes, I would recommend reading the Kubernetes Architecture appendix section.

Kubernetes’ rich cloud-native abstractions give the flexibility to create a wide variety of cloud-native platforms. *PODs, Services, Deployments, ConfigMaps, Labels,* and the *Horizontal POD Autoscaler* are some of the key cloud-native abstractions. The Kubernetes cloud-native abstractions section discusses details of the Kubernetes abstractions used in the API-led integration platform to build a cloud-native digital enterprise.

### Custom resources and custom controllers

A custom resource is an extension of the Kubernetes API; it does not ship with the default Kubernetes installation. A Kubernetes cluster admin can add/remove custom resources independently of the cluster itself. Once a custom resource installs, users can create and access its objects using kubectl, just as they do for built-in resources such as *PODs*.

Custom controllers help keep the current state of Kubernetes objects (defined in CR) in sync with the desired state. The controller interprets the structured data as a record of the user’s desired state and continually maintains it. So, custom resources provide a dedicated declarative API when you combine a custom resource with a custom controller.

Custom resources and custom controllers give flexibility and an immense power to architects to build cloud native platforms on top of Kubernetes.

## WSO2’s API-led integration platform

WSO2’s API-led integration platform is an open-source, market-leading enterprise solution that supports full API lifecycle management and integration. The platform was named a Leader in The Forrester Wave™: API Management Solutions, Q3 2020  [report](https://wso2.com/resources/analyst-reports/the-forrester-wave-api-management-solutions-q3-2020/).

WSO2’s offering comes with an API designer and publisher, a developer portal, a key manager, an API analytics server, an API gateway, an enterprise integrator, and a Kubernetes API operator.

### Full API lifecycle management

In an era of digital transformation, APIs are a strategic investment to any organization. They play a significant role as both technical enablers and  business drivers. WSO2 API Manager provides state-of-the-art web interfaces, e.g., WSO2 API Designer and Publisher, for API development and management. It is 100% compliant with the Open API Specification, helping API creators to develop, document, scale, and version APIs, while also facilitating more API management-related tasks such as publishing, monetizing, and promoting APIs.

<p align="center">
<img src="https://github.com/lakwarus/reference-architecture/raw/master/media/ra-api-publisher.png">
<br> 
<i>Figure 2 - WSO2 API Designer and Publisher</i>
</p>

In addition to the graphical interface, WSO2’s API-led platform has a command-line tool, i.e., apictl, which automates full API lifecycle management functionalities. 

### The communication hub for an API ecosystem

The API developer portal is a hub to discover and onboard developers with low friction experiences. WSO2’s developer API portal enables developers to find APIs, test them before subscription and consumption, calculate monetization with specific metrics, view feedback, and feature requests from consumers through forums, and more.

<p align="center">
<img src="https://github.com/lakwarus/reference-architecture/raw/master/media/ra-api-dev-portal.png">
<br> 
<i>Figure 3 - WSO2 API Developer Portal</i>
</p>

The developer portal’s web UI is a single page React application written on top of well-defined APIs. Organizations can customize the web UI to align with organization needs or build their own branded developer portal by consuming these developer APIs.

### Enabling QoS through traffic regulation

When productizing APIs, it is vital to have API traffic regulation capabilities to provide consumers with different service levels. WSO2 Traffic Manager helps to define throttling policies and enforce them in API gateways. WSO2 Traffic Manager comes with a dynamic throttling engine that processes throttling policies in real-time and enables rate-limiting of API requests to prevent APIs from being overwhelmed, allowing API owners to enforce a limit on the number of requests.

### Business intelligence

Obtaining meaningful business insights on how APIs are behaving is critical in every business. WSO2 API Analytics Server is capable of generating all kinds of business intelligence. In addition to statistical graphs, its real-time event processing engine can identify abnormalities and alert users about potential malicious attacks.  

### API security and anomaly detection

Security is paramount when exposing business capabilities via APIs. WSO2 Key Manager 
manages all clients, security, and access token-related operations. It supports OAuth 2.0, JWT, Basic Auth, Mutual SSL, and API-Key-based authentication mechanisms.

<p align="center">
<img src="https://github.com/lakwarus/reference-architecture/raw/master/media/ra-key-manager-v1.png">
<br> 
<i>Figure 4 - WSO2 API Key Manager</i>
</p>

Sometimes, traditional security measures, such as authentication and authorization, alone are not enough. Compromised security tokens can cause a data breach or malicious activities. You can use WSO2’s integrated artificial intelligence-based solutions to control these kinds of incidents. 

Malicious payloads could come with authorized and authenticated requests, and identifying and stopping them immediately at an early stage is critical. You can set rules to analyze the request payload (e.g., JSON or XML) and prevent them from passing through the gateway to the respective backends.

Anomalies can be identified by analyzing the access patterns to the APIs. Artificial intelligence and machine learning techniques help to identify these kinds of security threats. These advanced techniques help digital enterprises proactively monitor and prevent possible risks and malicious activities. 

### Composition, integration, and mediation

WSO2 Enterprise Integrator is capable of playing multiple roles in your enterprise architecture. It can be used as an Enterprise Service Bus (ESB), a streaming data processor, and a microservices integrator. WSO2 Micro Integrator supports both centralized (ESB style) and decentralized (microservices, cloud-native) architectural styles. WSO2 Streaming Integrator allows you to implement streaming ETL (extract, transform, and load), change data capture (CDC), and process large files and real-time APIs. 

WSO2 Micro Integrator provides a unique low code approach to microservices integration. Its rich, full connectors help integrate with a wide range of legacy systems. The offering’s easy-to-use code integration approach speeds creating composite integration microservices, while enabling users to reap the benefits of MSA.

<p align="center">
<img src="https://github.com/lakwarus/reference-architecture/raw/master/media/ra-facade-pattern-v1.png">
<br> 
<i>Figure 5 - Micro integration</i>
</p>
