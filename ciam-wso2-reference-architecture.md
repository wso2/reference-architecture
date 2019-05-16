<h1 align="center"> Customer Identity 
and Access Management
 </center></h1>
<h2 align="center"> A WSO2 Reference Architecture</center></h2>
<p align="center">
<i>
Version Q2-2019<br/>
</i>
</p>

**_Author_**
+ Dakshitha Ratnayake, Enterprise Architect - CTO Office
<dakshitha@wso2.com>


> *This paper will introduce Customer Identity and Access Management (CIAM), which is a subgenre of identity and access management. It enables organizations to scale and ensure secure, seamless digital experiences for their customers while collecting and managing customer identity data purposefully. Powerful CIAM solutions provide a variety of key features including customer registration, social logins, account verification, self-service account management, consent and preference management, single sign-on (SSO), multi-factor authentication (MFA) and adaptive authentication as well as other nice-to-have features. This paper will introduce a CIAM reference architecture to address minimal and full-scale CIAM needs with open source WSO2 products, which mainly focus on identity and access management, API management, integration, and streaming analytics.*

## 1.0 Introduction to Customer Identity and Access Management (CIAM)
### 1.1 Hyper-connected Customers and their Identity, Data,  and Experience Requirements

Today’s increasingly sophisticated customers now view digital interactions as the primary mechanism for connecting with brands and, therefore, expect significant online interactions to be delivered simply and seamlessly. Transforming the customer experience is at the heart of digital transformation and digital technologies are changing the game of customer interactions with new rules and possibilities that were unimaginable only a few years back. Most enterprises have a large number of customers who access mobile, IoT and other channels in addition to mere web apps, which may or may not reside inside the firewall. As consumers increasingly conduct high-value, sensitive transactions digitally, it is imperative for organizations to protect their businesses from threats to consumer-facing channels especially in the context of financial services, pharmaceutical, and other highly regulated industries.

Collecting, storing, and analyzing consumer data allows enterprises and government organizations to provide better digital experiences for their consumers. This creates additional sales opportunities and increases brand loyalty.  Companies that capitalize on customer insights have a competitive advantage over their contenders who do not. As the number of customers, applications, and services continues to grow, the data collected on customers is also increasing rapidly. At the same time, because consumer data is collected from various channels, this data is often found in disparate identity stores, creating inconsistent user experiences and hindering the ability to have a single unified view of these consumers. 

Moreover, the customers do expect some control around how firms collect, store, manage, and share their profile data. With the competition only a click away, a company’s misuse of customer data, whether deliberate or inadvertent, can significantly damage brand equity. 

### 1.2 CIAM for a Secure and Seamless Customer Experience
Customer Identity and Access Management (CIAM) addresses the above-mentioned requirements of the hyper-connected customer. CIAM is an emerging sub-genre of traditional IAM, which is of vital importance for a seamless digital customer experience. An effective CIAM system provides more than just access because it enables a relationship between the customer and the organization and facilitates data sharing on which cross-marketing capabilities and business intelligence activities depend.

#### 1.2.1 Benefits of CIAM
Enterprises should consider implementing a CIAM solution because it
- Helps provide a holistic view of the customer, which will enable companies to understand their customers’ actions across various access points.
- Provides a unified customer experience. It enables customer conversion and retention through consistent registration and authentication options at extreme scale and performance, thus allowing a secure and seamless customer experience. 
- Can deliver consolidated reports and analytics around users to drive various sales opportunities. These statistics typically include user demographics, social registration and login data, behavioral data, and revenue activity. 
- Adheres to privacy regulations and improves agility and scalability to support millions of customer identities. 
- Helps to build the bridge between marketing and line of business to deliver offerings that keep customers delighted while delivering actionable data to the business.

Traditional IAM solutions do not provide these benefits (as explained in section 1.2.2). 

#### 1.2.2 CIAM vs Traditional IAM
CIAM goes beyond traditional IAM, also known as Workforce IAM. Workforce IAM looks inward, where the focus is on business-to-employee (B2E) and business-to-business (B2B) interactions. Some enterprises have a mistaken impression that an IAM solution that’s purpose-built for employees is a natural fit for their customer interactions. It is important to note that CIAM transcends traditional IAM especially in analyzing customer behavior, collecting consent for user data usage, and integration into customer relationship management (CRM) systems, connected devices, and marketing automation systems. 

The goal of workforce IAM is to reduce the risk and cost associated with onboarding and off-boarding new employees, partners and suppliers. By contrast, the purpose of CIAM is to help drive revenue growth by leveraging identity data to acquire and retain customers. If the CIAM processes are cumbersome, the experience is poor and the security is weak, customers will naturally reach out to competitors who offer these processes in ways more streamlined or easier to use. The same is not true of employees because employees are required to comply with and conform to their company’s systems and technologies. Very few employees leave their employer because business-to-employee (B2E) IAM processes are archaic or hard to use - employees are paid to use an organization’s systems. On the other hand, customers will walk away if the user experience is not smooth enough.

CIAM systems vary from employee IAM systems in the following foundational areas:

|  |  |  |
|--|--|--|
|   |Traditional IAM |Customer IAM|
|Business Objective| Reduce risk and improve efficiency|Attract and retain customers|
|User Profile|All required information of an employee is acquired when hiring|Customer information is acquired gradually over time (progressive profiling)|
|Control|Employee identities are centrally managed by the enterprise|The control of identity is shared between the enterprise and the customer (distributed)|
|Experience|Low priority (unless it detracts from efficiency)|High priority|
|Personalization|Low priority|High priority|
|Privacy and User Involvement|Organization-centric policies and procedures|Customer-centric policies and preferences|
|Scale|100s and 1000s|1000000s|
|Performance and Reliability|Generally not prioritized|Extremely important|
|

<p align="center">
<i>
Table  1 - Traditional IAM vs Customer IAM<br/>
</i>
</p>

## 2.0 CIAM Key Features 
![ciam key features](/media/media_ciam/ciam_key_features.png)

 
<p align="center">
<i>
Figure 1 - Key Features of CIAM
<br/>
</i>
</p>


























========================================




## References 
[1] Ballerina 
https://ballerina.io/

[2] WSO2 API Manager
https://wso2.com/api-management/

[3] WSO2 Enterprise Integrator
https://wso2.com/integration/

[4] WSO2 Identity Server
https://wso2.com/identity-and-access-management/

[5] Microservices 
https://thenewstack.io/category/microservices/

[6] Michelle Gienow - Microservices 101
]https://thenewstack.io/microservices-101/

[7] Chris Richardson - Pattern: Microservice Architecture
https://microservices.io/patterns/microservices.html

[8] Samir Behara - Monolith to Microservices Using the Strangler Pattern
https://dzone.com/articles/monolith-to-microservices-using-the-strangler-patt

[9] Martin Fowler - Strangler Application
https://www.martinfowler.com/bliki/StranglerApplication.html

[10] Istio Service Mesh 
https://developers.redhat.com/topics/service-mesh/

[11] Kasun Indrasiri - Service Mesh vs API Gateway
https://medium.com/microservices-in-practice/service-mesh-vs-api-gateway-a6d814b9bf56

[12] Kasun Indrasiri - Microservices Layered Architecture
https://medium.com/microservices-in-practice/microservices-layered-architecture-88a7fc38d3f1

[13] Asanka Abeysinghe and Paul Fremantle - Cell-based Reference Architecture: Version Q2-2018
https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md

[14] WSO2 Named a Leader | The Forrester Wave™: API Management Solutions, Q4 2018
https://wso2.com/resources/analyst-reports/the-forrester-wave-api-management-solutions-q4-2018/?utm_source=landiniam&utm_campaign=forrester_wave_apim_2018B7

[15] Anne Thomas and Aashish Gupta - Innovation Insight for Microservices
https://www.gartner.com/doc/3579057/innovation-insight-microservices

[16] Inter-process communication for Microservices
https://ballerina.io/learn/by-guide/inter-microservice-communication/

[17] Asanka Abeysinghe - Navigating the Ins and Outs of a Microservice Architecture (MSA)
https://www.infoq.com/articles/navigating-microservices-architecture





















