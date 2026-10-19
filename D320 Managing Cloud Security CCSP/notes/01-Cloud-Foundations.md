# Cloud Foundations

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 1 – Architectural Concepts](#chapter-1--architectural-concepts)
- [Chapter 2 – Design Requirements](#chapter-2--design-requirements)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 1 – Architectural Concepts

### Business context and cloud characteristics

- **Existing State:**
  - evaluate and understand the business processes, assets, and requirements
  - after collecting sufficient data, a detailed analysis is necessary
  - a BIA (business impact analysis) takes place

- **BIA (Business Impact Analysis):**
  - an assessment of the priorities given to each asset and process within the organization
  - analysis considers the effect (impact) any hard or loss might mean to the organization overall
  - identify critical paths and single points of failure
  - determine costs of compliance (legislative and contractual requirements mandated)

- **Metered service:** the organization only pays for what it uses

- **Rapid Elasticity:** excess capacity available to be apportioned to cloud customers

- **Cloud bursting:**
  - organizations to use hosted cloud service to augment internal, private data center capabilities with managed services during times of increase demand
  - an org can rent the additional capacity as needed from an external cloud provider (crisis situation, heavy holiday shopping periods)
  - rapid scalability allows customer to dictate the volume of resource

- **Cloud service benefits:**
  - reduction in personnel cost (data management)
  - reduction in capital expenditure (metered service, rapid elasticity, cloud bursting)
  - reduction in operational costs
  - transferring some regulatory costs
  - reduction in costs for data archival/backup services

- **ROI (Return on Investment):**
  - term related to cost-benefit measures
  - used to describe a profitability ratio
  - calculated by dividing net profits by net assets

- **Elasticity:** customers can contract cloud providers to use virtualization to flexibly allocate only the needed usage of each resource to the organization, while holding costs while maintaining profitability; allow users to access their data from diverse platforms and locations, increasing portability, accessibility, and availability

- **Simplicity:** allow a user to seamlessly use the service without frequently interacting with the cloud service provider

- **Scalability:** increasing/reducing services can be easily, quickly, and cost-effectively accomplished

### Cloud Computing Service Models

- **IaaS (Infrastructure as a Service):**
  - most basic service
  - allows customer to install all software and OSs on hardware housed and connected by the cloud vendor
  - can be considered a warm site for BC/DR purposes
  - optimal for orgs wanting control over the security of their data and limited cloud vendor assistance (BC/DR or archiving)
  - least expensive option
  - customer retain IT staffing

- **When to use:**
  - website or application hosting
  - virtual data centers
  - data analysis

- **PaaS (Platform as a Service):**
  - includes services from IaaS and OSs (offers a selection for customers to use, Windows, Linux, Mac, etc.)
  - vendor is responsible for patching, administering, and updating the OS
  - customer can install any software
  - useful for customers involved in software development (they can test on multiple OS platforms)
  - includes cloud-based database engines and services “big data” style services (data warehousing and datamining)
  - provider offers access to back-end engine/functionality, while customer can create/install apps/APIs to access the backend

- **When to use:**
  - reduce development time
  - support for different programming languages
  - easy collaboration for remote/distributed teams
  - high development capabilities w/o additional staff

- **Data Storage Types used:** structured/unstructured

- **Unstructured Data Types:**
  - qualitative data
  - natural-language text
  - incorporate media (audio, video, images)
  - contains JSON, XML, binary objects (images encoded as text strings)
  - important for data analytic strategies
  - noSQL – Object Storage

- **Structured Data Types:**
  - quantitative data
  - organized and decipherable by machine learning algorithms
  - SQL (relational) can be used to quickly input, search, and manipulate data
  - used by machine learning algorithms

- **SaaS (Software as a Service):**
  - includes everything from IaaS and PaaS with the addition of software programs
  - vendor is responsible for administering, patching, and updating everything, also takes care of all infrastructure, compute, and storage needs as well as providing OSs and application
  - customer is only involved in uploading and processing data on a full production environment
  - application is a shared responsibility of all parties

- **When to use:** (Personal) email services (gmail), cloud storage services (Dropbox), cloud-based file management (Google Docs); (Business) gmail, collaboration tools (Trello), CRM (Salfesforce), ERP

### Cloud Deployment Models

- **Public Cloud:**
  - resources are owned and operated by a vendor and sold, leased, or rented to anyone
  - multitenant environments
  - multiple customers will share resources
  - EX: customer might be using a AM that resides on the same hardware that hosts another VM as their competitor, but they do not know the entities using the same resources
  - Rackspace, Microsoft’s Azure, and AWS (Amazon Web Services)

- **Private Cloud:**
  - resources dedicated to a single customer
  - might be owned and maintained by the entity that is the sole customer (org might own and operate a data center that serves as the cloud environment for the org’s users)
  - might be a set of resources (racks, blades, software packages) owned by the single customer but located and maintained at provider’s data center
  - provider might offer physical security, admin services, and utilities (power, Internet) for customers (referred to as co-lo (co-located) environment)

- **Community Cloud:**
  - features infrastructure and processing owned and operated by/for an affinity group
  - orgs come together to perform joint tasks and functions
  - gaming communities, ownership is spread throughout the various members of the community
  - can be provisioned by a third party (FedRAMP service – only used by US federal gov)

- **Hybrid Cloud:** contains elements of other models; org might want to retain some private cloud resources (remote user access) but lease some public cloud space (PaaS function for software development/testing)

### Roles and Responsibilities

- **Cloud Broker:** company that purchases hosting services from a provider and resells them to its own customers

- **CASB (Cloud Access Security Broker):** third-party entity offering independent IAM (identity and access management) services to CSPs and cloud customers; can be SSO, certificate management, and cryptographic key escrow

- **Regulators:**
  - ensure orgs are incompliance with regulatory framework for which they are responsible for
  - HIPAA, GLBA, PCI DSS, ISO, SOX, etc.
  - regulators include FTC, SEC, and auditors

### Definitions and Design Vocabulary

- **Cost-Benefit Analysis:** comparing potential positive impact (profit, efficiency, market share) of a business decision to potential negative impact (expense, detriment to production, risk) and weighing the two as equivalent or not (potential positive/negative)

- **FIPS 140-2:** NIST document that describes the process for accrediting and cryptosystems for use by the federal government; lists only approved cryptographic tools

- **NIST 800-53:** guidance document with primary goal of ensuring appropriate security requirements and controls are applied to all US federal government information in management systems

- **TCI (Trusted Cloud Initiative) Reference Model:** guide for cloud providers, allowing them to create a holistic architecture that customers can purchase (including physical/logical layout of network and processes necessary to utilize both)

- **Vendor Lock-In:**
  - situation where a customer is unable to leave, migrate, retrieve, or transfer data to an alternate provider due to technical/nontechnical constraints
  - use portability for a level of ease when transporting data, ensure contract states so, avoid proprietary formats (requires specific software to read data), check for regulatory constraints
  - detrimental contract terms or technical limitations

- **Vendor Lock-Out:** when a customer is unable to recover/access their own data due to provider going into bankruptcy or leaving the market

- **Blockchain:**
  - open means of conveying value using encryption technologies/algorithms (cryptocurrency)
  - transactional ledger where all participants can view every transaction, making it extremely difficult to negatively affect the integrity of past transactions
  - each record (block) is distributed among all participants in a distributed or cloud-based manner

- **Containers:**
  - logical segmentation of memory space in a device, creating two or more abstract areas that cannot interface directly
  - commonly used in BYOD environment
  - distinguish two distinct partitions (one for work functions/data and other for personal functions/data)

- **Quantum Computing:** emerging technology that allow IT systems to operate beyond binary math; instead of using the presence of electrons for calculations (electrons is either present/not present), quantum computing may use subatomic characteristics (electron spin, charm, etc.) to offer computing on exponentially larger scale

- **Homomorphic Encryption:** theoretical phenomenon that allow processing of encrypted material without needing to first decrypt it; can allow cloud customers to upload encrypted data and still utilize data without sharing keys with provider or having to accommodate decryption as part of the process

- **STRIDE Threat Model:** Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, and Elevation of Privilege

- **Apache cloud stack:** open source cloud computing software for creating, managing, and deploying infrastructure cloud services; uses existing hypervisor platforms

- **Business Requirement:** operational driver for decision-making and input for risk management

## Chapter 2 – Design Requirements

### Business Requirements and Risk

- **Business Requirements Analysis:**
  - inventory of all assets
  - valuation of each asset (BIA, data owners determine value
  - head of department)
  - determination of critical paths (made by senior management
  - SPOFs), processes, and assets
  - clear understanding of risk appetite (set by senior management)

- **SPOFs (Single Points of Failure) methods to reduce:**
  - adding redundancies
  - creating alternative processes
  - cross-training personnel
  - back up data
  - load sharing/balancing for IT assets

- **Quantitative Risk Assessment:** use specific numerical values such as 1,2, and 3; employ a set of methods, principles, or rules for assessing risk

- **Qualitative Risk Assessment:**
  - use nonnumerical categories that are relative in nature
  - high, medium, and low
  - employ a set of methods, principles, or rules for assessing risk

- **Risk:**
  - likelihood an impact will be realized
  - can be reduced, never eliminated
  - orgs can accept a level of risk that allows operations to continue in a successful manner
  - legal and defensible to accept risks higher than the norm/greater than your competitors (except risk to health and human safety, must be addressed to industry standard/regulatory scheme)

- There are four main ways to address risk

- **Avoidance:**
  - risk that exceeds the organization’s appetite
  - leaving business opportunity because risk is too high and cannot be compensated for with adequate control mechanisms
  - response to cost-benefit analysis
  - don’t conduct the risk at all
  - halts business functions

- **Acceptance:**
  - opposite of avoidance
  - falls within the org’s risk appetite
  - org continue operations without any additional efforts

- **Transference:** org pays someone else to accept the risk, at a lower cost (insurance); normally with low probability of occurring but a high impact if they do

- **Mitigation:** org take steps to decrease the likelihood/impact of the risk; form of controls/countermeasures, where security practitioners are involved

- **Residual Risk:** when risks are mitigated by applying countermeasures and controls the remaining leftover risk is residual risk; task of security program is to reduce until it falls within the acceptable level according to org’s risk appetite (senior management dictates the appetite)

### Responsibilities by Service Model

- **Security Considerations for Cloud:** the cloud customer is always legally liable for any loss of data, even if cloud provider demonstrates negligence or malice

- **IaaS Considerations:**
  - customer has the most responsibility and authority
  - provider is responsible for building, land, connectivity, power, and hardware assets
  - makes auditing difficult because they cannot set up network monitoring for policy and regulatory compliance, but customers can collect and review event logs from the software (OS too)

- **PaaS Consideration:** same as IaaS but provider controls the OSs; customer can still monitor and review software events because the programs running on the OS belongs to them

- **SaaS Consideration:** customer only supplies and process data; security controls are limited because provider supplies all needs of customer

- **To demonstrate due care:** ensure cloud provider performs strict background checks, continual monitoring of all personnel with access to data center, extreme physical security measures, encryption of data processed and stored, assignment of contractual liability to the provider, etc.

## Additional Topics from the Source Notes

- **NIST 800-145:** The NIST definition of Cloud Computing; a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.

- **NIST 800-146:** document reprises the NIST-established definition of cloud computing, describes cloud computing benefits and open issues, presents an overview of major classes of cloud technology, and provides guidelines and recommendations on how organizations should consider the relative opportunities and risks of cloud computing.

- **Eucalyptus:** computer software building AWS-compatible private/hybrid cloud computing environment; multitenancy

- **ISO/IEC 17788:** overview of cloud computing and a set of terms and definitions

- **NIST 500-292:** adoption of cloud computing into the Federal Government

## Review Questions

1. How do IaaS, PaaS, and SaaS change customer responsibilities?
2. How does cloud bursting help during a demand spike?
3. What remains after controls reduce risk?

<details>
<summary>Check your answers</summary>

1. IaaS includes customer management of the guest OS; PaaS manages the platform for customer applications; SaaS provides a managed application. Customer data and access responsibilities remain.
2. It adds external cloud capacity to supplement the normal environment.
3. Residual risk.

</details>

[Study index](../README.md) · [Next section](02-Cloud-Data-Security.md)
