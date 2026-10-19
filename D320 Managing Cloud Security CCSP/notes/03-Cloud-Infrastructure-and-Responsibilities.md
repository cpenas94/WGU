# Cloud Infrastructure and Responsibilities

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 5 – Security in the Cloud](#chapter-5--security-in-the-cloud)
- [Chapter 6 – Responsibilities in the Cloud](#chapter-6--responsibilities-in-the-cloud)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 5 – Security in the Cloud

### Deployment Risks and Portability

- **Private Cloud:** distributed computing environment with only one customer

- **Risks:**
  - personnel threats
  - natural disasters
  - external attacks
  - regulatory noncompliance
  - malware

- **Community Cloud:** resources are shared and dispersed among an affinity group

- **Risks:**
  - resiliency through shared ownership
  - shared costs
  - no need for centralized administration for performance and monitoring

- **Public Cloud:** offer services to any entity that wants to become a cloud customer

- Risks:

- **Vendor Lock-In:**
  - customer is unable to retrieve data
  - use portability for a level of ease when transporting data, ensure contract states so, avoid proprietary formats, check for regulatory constraints
  - detrimental contract terms or technical limitations

- **Data Portability:** used to avoid lock-in; the ease of moving data from cloud provider to another

- **Vendor Lock-Out:** provider goes out of business, bought out by another business, or ceases operation

### Hypervisors and Virtualization Risks

- Hypervisor:

- **Type 1:** also called bare-metal/hardware hypervisor; resides on host machine as bootable software

- **Type 2:** software hypervisor; runs on top of the OS that runs on a host device

- **Guest Escape / VM Escape:** allow a user to leave their own virtualized instance; user will be able to access other virtualized instances on the same host, view, copy, or modify data stored, access host itself affecting all instances on the machine

- **Host Escape:** user can leave the host machine, accessing other devices on the network

- **VMI (Virtual Machine Introspection):** agentless means of ensuring VM’s security baseline does not change by examining the physical address, network settings, and installed OS

### Virtual Networking

- **NFV (Network Functions Virtualization):** replacement of network appliance hardware with VMs; uses a hypervisor to run networking software and processes such as routing and load balancing

- **SDN (Software Defined Networking):** approach to networking that uses software-based controllers or APIs to communicate with underlying hardware infrastructure and direct traffic on a network; allow network admins to perform the following:

- Reroute traffic based on current customer demand

- Create logical subnets without having to change any actual physical connections

- Filter access to resources based on specific rules or settings

## Chapter 6 – Responsibilities in the Cloud

### SOC Reports and Assurance

- **SOC reports:** part of the SSAE reporting format by the AICPA; recognized as being acceptable for regulatory purposes, specifically designed for SOX

- **SOC 1:** reports for the auditing of financial reporting instruments of a corporation; there are 2 subclasses (Type 1 and Type 2)

- **SOC 2:** report audits of any controls on an org’s security, availability, processing integrity, confidentiality, and privacy

- **Type 1:** not useful for determining security and trust of an org; only reviews the design of controls, not how they are implemented / maintained / functioned

- **Type 2:** useful for getting true assessment of org’s security posture; extremely detail, usually not shared unless NDA is signed

- **SOC 3:**
  - reports designed to be shared with the public
  - “seal of approval”
  - has no data about the security controls, an assertion the audit was conducted and passed

## Additional Topics from the Source Notes

- **OSI Model:**
  - Physical
  - Data Link
  - Network
  - Transport
  - Session
  - Presentation
  - Application (Please Do Not Throw Sausage Pizza Away)

- **Management Plane:**
  - technology that allows an admin to remotely manage a fleet of servers
  - logical infrastructure design used to configure cloud resources
  - launching VMs or configuring virtual networks

- **Metastructure:** protocols and mechanisms that provide the interface between the infrastructure layer and other layers; the glue that ties technologies between management and configuration

- **Software-Defined Infrastructure:** technical computing infrastructure entirely under the control of software with no operator or human intervention

## Review Questions

1. How do Type 1 and Type 2 hypervisors differ?
2. How do SOC Type I and Type II reports differ?
3. What does the management plane do?

<details>
<summary>Check your answers</summary>

1. Type 1 runs directly on hardware; Type 2 runs on a host operating system.
2. Type I addresses control design at a point in time; Type II also addresses operating effectiveness over a period.
3. It provides interfaces for administering and configuring cloud resources.

</details>

[Previous section](02-Cloud-Data-Security.md) · [Study index](../README.md) · [Next section](04-Cloud-Application-Security.md)
