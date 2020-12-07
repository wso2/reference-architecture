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

Kubernetes’ rich cloud-native abstractions give the flexibility to create a wide variety of cloud-native platforms. PODs, Services, Deployments, ConfigMaps, Labels, and the Horizontal POD Autoscaler are some of the key cloud-native abstractions. The Kubernetes cloud-native abstractions section discusses details of the Kubernetes abstractions used in the API-led integration platform to build a cloud-native digital enterprise.

### Custom resources and custom controllers

A custom resource is an extension of the Kubernetes API; it does not ship with the default Kubernetes installation. A Kubernetes cluster admin can add/remove custom resources independently of the cluster itself. Once a custom resource installs, users can create and access its objects using kubectl, just as they do for built-in resources such as PODs.

Custom controllers help keep the current state of Kubernetes objects (defined in CR) in sync with the desired state. The controller interprets the structured data as a record of the user’s desired state and continually maintains it. So, custom resources provide a dedicated declarative API when you combine a custom resource with a custom controller.

Custom resources and custom controllers give flexibility and an immense power to architects to build cloud native platforms on top of Kubernetes.

