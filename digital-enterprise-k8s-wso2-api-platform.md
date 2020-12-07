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
