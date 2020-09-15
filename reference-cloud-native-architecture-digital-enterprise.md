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
