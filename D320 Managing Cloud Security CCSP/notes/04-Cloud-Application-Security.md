# Cloud Application Security

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 7 – Cloud Application Security](#chapter-7--cloud-application-security)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 7 – Cloud Application Security

### Application Migration

- **Forklifting:** moving an entire application to the cloud without significant changes; often self-contained stand-alone applications

### Secure Software Development Lifecycle

- Cloud-Secure SDLC (Software Development Lifecycle):

- **Defining:**
  - during this phase, the focus is to identify the business requirements of the application (accounting, database, or customer relationship management)
  - describe aspects of the business needs
  - do not choose tools/technologies at this phase

- **Designing:** this phase begins to develop user stories (what user want to accomplish and how to do it), what the interface will look like, and will it require use/development of any APIs

- **Development:** phase where the code is written

- **Testing:**
  - activities of initial penetration testing and vulnerability scanning against the application
  - use techniques/tools for both DAST (Dynamic application security testing) and SAST (static)
  - at least two types of tests take place, functional and security testing

- **Functional testing:** ensures the software performs whatever tasks it was intended for, completely and accurately, in a manner resistant to loss/interruption

- **Security testing:** ensures whatever controls were included in the software are working effectively and accomplishing their purpose

- **Secure Operations:** phase begins when thorough testing is complete and environment is secure

- **Disposal:** when software reaches end of life or replaced by newer application, it must be securely disposed

### Quality Assurance and Application Frameworks

- **QA (Quality Assurance):** management/inspection to reduce possibility of introducing errors or harming the end product

- **ISO/IEC 27034-1 Standards for Secure Application Development:**
  - created an approach orgs can use for tracking security controls used in software
  - provides overview of application security that introduces definitive concepts, principles, and processes
  - describes two documents, ONF and ANFs

- **ONF (Organizational Normative Framework):** framework for all components of application security controls and best practices cataloged and leveraged by the org

- **ANF (Application Normative Framework):** subsets of ONF for each specific application; shares the applicable parts of the ONF needed to achieve an application’s required level of security and level of trust desired

- ANF-to-ONF relationship is one-to-one, every application has an ANF that maps back to the ONF; ONF-to-ANF relationship is one-to-many, ONF has many ANFs, but ANF has only one ONF

### Identity and Access Management

- **IAM (Identity and Access Management):** about the people, processes, and procedures used to create, manage, and destroy identities

- **Identity Management:** process where individuals are given access to system resources by associating user rights with a given identity

- **Provisioning:**
  - first phase of IM
  - each subject is issued a unique identity assertion (ex: user ID)
  - during the process, user is given a password to authenticate the identity assertion

- **Access Management:** part of the process that deals with controlling access to resources once they have been granted; identifies who a user is and what they are allowed to access, accomplished through authentication, authorization, policy management, federation, and identity repositories

- **Identity Repositories:** store of information or attributes of identities

- **Directory Services:**
  - how identities and attributes are managed
  - X.500 and LDAP
  - Microsoft AD
  - Novell eDirectory
  - Metadata replication and synchronization

### Federation and Identity Protocols

- **Federated Identity Management (Federation):**
  - used to manage identities across disparate orgs
  - a SSO for multiple orgs
  - two types of federation
  - web of trust and use of 3rd party identifier (CASB)

- **Web of Trust Model:** each member of the federation has to review and approve each other member for inclusion; doesn’t scale well, can be costly

- In a trusted third-party model of federation (CASB), each member organization outsources the review and approval task to a third party they all trust. This makes the third party the identifier (it issues and manages identities for all users in all organizations in the federation), and the various member organizations are the relying parties (the resource providers that share resources based on approval from the third party).

- **SAML (Security Assertion Markup Language):**
  - a federation standard
  - XML-based and consists of a framework for communication authentication, authorization or entitlement information, and attribute information across orgs
  - a means for users from outside orgs to be verified as authorized users

- **SAML 2.0:** standard used to pass security assertions across the internet (user IDs and authenticating credentials)

- **WS-Federation:** uses the term realms in explaining its capabilities to allow orgs to trust each other’s identity information across orgs

- **OAuth:** used in authorization with mobile apps; provides 3rd party applications limited access to HTTP services

- **OpenID Connect:** interoperable authentication protocol based on OAuth 2 specification; allows developers to authenticate users across websites and applications without having to manage us/pw

### Application Protection and Gateways

- **Stateful Packet Inspection:** allow firewalls to prevent inbound traffic from entering unless connection has been initiated from inside the network

- **WAFs (Web Application Firewall):**
  - deployed in addition to network firewall
  - protect specific web-based applications like PCI DSS
  - can protect against DoS/DDoS attacks
  - function at Layer 7 in OSI model

- **DAM (Database Activity Monitoring):**
  - protects the DB from unusual requests or activity
  - can be agent (host)/network-based
  - function at Layer 7 in OSI model

- **API Gateways:**
  - impose controls as an API proxy to not directly expose the API
  - implement access control
  - limit connections for bandwidth to be available for all applications (helps with internal DoS attack)
  - API logging
  - gathering metrics from access logs
  - additional API security filtering
  - function at Layer 7 in OSI model

- **XML Gateway:** works around how sensitive data and services are exposed to APIs; software/hardware based and can implement types of DLPs

- **XACML (eXtensible Access Control Markup Language):** attribute-based access control policy language or XML-based language, designed to express security policies and access requests to information; can be used for web services, digital rights management, enterprise security applications

### APIs and Development Tools

- **APIs (Application Programming Interface):** coding components that allow applications to communicate through web interface in a safe and secure manner; two types of APIs in cloud-based applications

- **RESTful APIs (Representational State Transfer):** relies on stateless, client-server, cacheable communications. It is a software architecture consisting of guidelines and best practices for creating scalable web service

- **Characteristics:**
  - low processing
  - uses simple URLs/URIs
  - not reliant on a single programming language
  - scalable
  - offers outputs in many formats (CVS, JSON)
  - efficient

- **Situations where REST works well:**
  - when bandwidth is limited
  - stateless operations are used
  - caching is needed

- **SCIM (System for Cross-domain Identity Management):** open standard designed to manage user identity information; provides a defined schema for representing users and groups, and a RESTful API to run CRUD operations on those user and group resources

- **SOAP (Simple Object Access Protocol):** protocol specification providing for the exchange of structured information or data in web services; works over other protocols like SMTP, FTP, and HTTP

- **Characteristics:**
  - standards-based
  - reliant on XML
  - highly intolerant of errors
  - slower
  - built-in error handling
  - more accurate

- **Situations where SOAP works well:**
  - asynchronous processing
  - format contracts
  - stateful operations

- **SDK (Software Developmental Kits):**
  - collection of software development tools in one installable package
  - facilitate creation of applications by having a compiler, debugger, and software framework
  - kit that facilitates usages of an API

### Encryption Threat Modeling and Testing

- **TLS (Transport Layer Security):** protocol to ensure privacy when communication between applications, servers, or client

- **SSL (Secure Socket Layer):** same use as TLS, replaced by TLS

- **Whole-Instance Encryption (Whole-Disk):** encrypt all system’s data at rest in one instance

- **STRIDE Model:** standardized way of describing threats by their attributes; Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of Privilege

- **CSRF (Cross-Site Request Forgery):** manipulates a logged-on user’s browser to send a forged HTTP request along with cookies to force the victim’s browser to generate a request that a vulnerable application thinks is a legitimate request from the user

- **White-Box Testing SAST (Static Application Security Testing):** reviewing the source code

- **Black-Box Testing DAST (Dynamic):**
  - testing the program as it functions in runtime
  - source code is not reviewed
  - team use inputs and results of application itself as it’s running

### Application Orchestration

- **Application Orchestration:** when two or more applications must interact in order to successfully complete a business process/transaction; two approaches we can take:

- Link elements of the applications directly, so out of one is input of another; can lead to additional problems; creating unnecessary dependencies, increasing difficulty of version control, testing

- Abstract the functions of the applications so input/output can be handled distinctly from the way the programs work; often with another code/software; preferable option; known as application orchestration

- **Authentication:** confirms the identity assertion belongs to the entity presenting it

## Additional Topics from the Source Notes

- **OWASP (Open Web Application Security Project):** an international nonprofit that focuses on identifying software vulnerabilities and educating developers in the practice of secure coding

- Broken Access Control; Cryptographic Failures; Injection; Insecure Design; Security Misconfiguration; Vulnerable and Outdated Components; Identification and Authentication Failures; Software and Data Integrity Failures; Security Logging and Monitoring Failures; Sever-Side Request Forgery (SSRF)

- **SSO:** allows a user to access multiple applications with a single set of credentials for authentication and authorization

- **Cross-Certification Model:** every participating org has to review and approve every other org; does not scale well

- **Functional requirements:** Those performance aspects of a device, process, or employee that are necessary for the business task to be accomplished. Example: A salesperson in the field must be able to connect to the organization’s network remotely.

- **Nonfunctional requirements:** Those aspects of a device, process, or employee that are not necessary for accomplishing a business task but are desired or expected. Example: The salesperson’s remote connection must be secure

- **DFD (Data Flow Diagrams):** useful in systems/software engineering to establish functional requirements before selection of technology takes place

- **Microsoft’s (SDL) Security Development Lifecycle:**
  - software development process based on the spiral model
  - help developers create applications/software while reducing security issues, resolving security vulnerabilities, and reducing development and maintenance costs
  - training, requirements, design, implementation, verification, release, response

## Review Questions

1. How do authentication and authorization differ?
2. What is the relationship between OAuth and OpenID Connect?
3. What distinguishes static and dynamic application testing?

<details>
<summary>Check your answers</summary>

1. Authentication verifies identity; authorization determines permitted actions.
2. OAuth supports delegated authorization; OpenID Connect adds an identity and authentication layer.
3. Static testing examines artifacts without executing the application; dynamic testing examines a running application.

</details>

[Previous section](03-Cloud-Infrastructure-and-Responsibilities.md) · [Study index](../README.md) · [Next section](05-Cloud-Operations-and-Recovery.md)
