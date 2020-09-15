<h1 align="center"> Reference Cloud Native Architecture for a Digital Enterprise </center></h1>
<p align="center">
<i>
Version Fall-2020<br/>
</i>
</p>

**_Original Authors_**

+ Lakmal Warusawithana | Senior Director - Technology Evangelism | WSO2, Inc | <lakmal@wso2.com>

> *This document describes a vendor/technology-neutral reference cloud native architecture (CNA) for a digital enterprise. The architecture defined in this paper can be mapped into different cloud-native platforms (Kubernetes and service mesh), different cloud providers (Microsoft Azure, Amazon AWS, and Google GCP), and infrastructure services to perform the implementation. These reference implementations will be covered in separate papers.*

## Introduction

In an era of digital transformation, **(digital) enterprises** are looking for fast innovation through effective collaboration to deliver more value to their customers with dramatically less effort. Digital enterprises enable companies of every sector to integrate, expose, and monetize their business capabilities by digitizing entire value chains.

As a result, APIs have become the norm to expose integrated business functionalities to deliver enhanced digital experience. Enterprises can start their digital transformation in greenfield or brownfield; in both cases, having a well defined **API-led integration architecture** is important. Apart from integration and API platforms, these architectures should be able to provide agility, flexibility, and scalability. This paper focuses on how to use cloud-native technologies along with an API-led integration platform to create an effective architecture, i.e., a **cloud-native architecture (CNA) for a digital enterprise**, to increase productivity by having automation, production or operation, and services. 

## Abstractions

| Icon | Name | Description |
|---------|---------|---------|
|![Component](/media/ra-microservice.png)| Microservices and serverless components |Core business logic, aggregation and service composition, transformation.|
|![Component](/media/ra-gateway.png)|Gateways|API gateways, ingress gateways, mesh gateways, micro integrators, exposed APIs, events and streams, policy enforcement points|
|![Component](/media/ra-data-service.png)|Legacy and data services|Databases, existing systems, registries and repositories, user stores, business processes|
|![SaaS EPR](/media/ra-saas-epr.png)|External endpoint|Access using APIs, events, and streams, cloud systems, and SaaS|
|![Front end Client](/media/ra-front-end-clients.png)|API Consumers|Mobile apps, reactive apps, API consumers|
|![Desktop Client](/media/ra-desktop-client-v3.png)|API Consumers|Mobile apps, reactive apps, API consumers|
|![Mobile Client](/media/ra-mobile-client-v3.png)|API Consumers|Mobile apps, reactive apps, API consumers|
|![Bot Client](/media/ra-bot-client-v3.png)|API Consumers|Bots, API consumers|
|![IOT Client](/media/ra-iot-client-v3.png)|API Consumers|IoT devices, apps, API consumers|
|![Key](/media/ra-key-v3.png)|Credentials|Credentials, keys, passwords|
|![Config](/media/ra-config-v3.png)|Configurations|Configurations|
|![Cert](/media/ra-cert-v3.png)|Certificats|Certificats|
|![Load Balancer](/media/ra-load-balancer-v3.png)|Load balancer|Load balancer|

## What is Cloud Native?

**“Cloud native”** is a two-fold term. It is a name for technologies that help to create, deploy, and operate applications in a scalable environment such as public, private, and hybrid clouds. It also refers to explaining characteristics of these applications, specifically made to address scalability. The capability of packaging and shipping application as a lightweight container is one of the main characteristics of cloud nativeness. 

Cloud native has its own foundation: the **Cloud Native Computing Foundation (CNCF)**, which was launched in 2015 by the Linux Foundation. The main goal of the CNCF is to build sustainable ecosystems and foster communities to support the growth and health of cloud-native open-source software.

## Cloud-Native Reference Architecture
![Cloud-native reference architecture by CNCF](/media/ra-cloud-nativearchitecture-cncf-v1.png) 

*Figure 1 - Cloud-native reference architecture by CNCF*

Figure 1 illustrates the cloud-native reference architecture presented by the CNCF. Each layer has its own specialized cloud-native software stacks and many of them are governed by the CNCF.  

### Infrastructure
The infrastructure layer represents the actual computing resources. These computing resources can be composed by using a set of bare metal machines networked together in a local data center. If the digital enterprise already runs a private cloud with the support of hypervisor-based virtualization technologies like VMware, OpenStack, and CloudStack, then the infrastructure layer can be composed by using a set of virtual machines connected and worked in the same virtual network. Alternatively, an enterprise can use virtual infrastructures, which is provided by public cloud providers such as Google, Microsoft, and Amazon. Or it can be a hybrid cloud by combining private cloud and public cloud computing resources.

### Provisioning
The provisioning layer covers the host management activities such as installation and setting up operating systems. It has a set of DevOps (maintenance) and management (software updates, security patches, etc) activities. Operating systems like CoreOS and RancherOS are specialized host operating systems to run containerized environments.

### Runtime
The runtime layer mainly consists of the container runtime. The **Container runtime interface** (CRI) allows to plug different implementations of container times. Docker is the widely used container runtime; alternatively,  CRI-O (Open Container Initiative compatible runtimes) or rkt container runtimes can be used. You can even plug a hypervisor-based container runtime like Frakti with support from CRI. 

The **Container network interface** (CNI) enables APIs to plug different container network runtime implementations. The CNI comes with inbuilt network plugins such as BRIDGE, VLAN, IPVLAN, DHCP, loopback, and etc. Also, it allows the plugin of the container network from third-party originations such as Weave, Calico, Cilium, Flannel, WMWare, and NSX. All of the network runtimes implement CNI specifications. 

![CNI](/media/ra-cni.png.png) 

*Figure 2 - Container network interface (CNI)*

Docker does not implement the CNI and it has its own implementation known as the container network model (CNM) and it only works with the Docker container runtime.

A **Container storage interface** (CSI) provides a common standard to connect container orchestration platforms to plugin to persistent storage. With the help of CSI, storage vendors can write a plugin to a single specification and this works on many orchestration platforms. Dynamic provisioning and decommissioning of volumes, attachment and detachment of volumes from a host node, and mounting and unmounting of a volume from a host node are the main capabilities that are provided by the CSI. 
