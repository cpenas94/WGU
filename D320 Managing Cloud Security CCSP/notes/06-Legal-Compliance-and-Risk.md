# Legal Compliance and Risk

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 10 – Legal and Compliance Part I](#chapter-10--legal-and-compliance-part-i)
- [Chapter 11 – Legal and Compliance Part II](#chapter-11--legal-and-compliance-part-ii)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 10 – Legal and Compliance Part I

### Legal Categories and Contracts

- **Criminal Law:**
  - all legal matters where the government is in conflict with person, group, or org that violates statutes (state and federal legislated by lawmakers)
  - includes federal court system
  - punishments can be monetary fines, imprisonment, death
  - enforcement is called prosecution

- **State Laws:** laws enacted by a state legislature; federal laws supersede this

- **Federal Laws:** laws that affect the entire country; issues of jurisdiction and prosecution are negotiated between law enforcement and course prior to prosecution

- **Civil Law:**
  - body of law, statutes, and so on that deals with personal and community-based law such as marriage/divorce
  - set of rules that govern private citizens and disputes
  - parties involved are strictly private entities
  - cases are called lawsuits/litigations
  - has restitution of monetary damages or perform actions but not imprisonment

- **Contracts:**
  - agreement between parties
  - in a breach of contract, a party within the agreement can sue to get court-ordered relief in money or other considerations (property or other agreements made before)
  - SLAs / PCI DSS contracts

- **Common Law:** existing set of rulings/decisions made by courts, informed by cultural mores and legislation; this creates precedents, each party will cite in course as means to sway the court

- **Administrative Law:** laws not created by legislatures but by executive decisions and function; federal agencies can create, monitor, and enforce their own administrative law

### US Laws and Federal Cloud Requirements

- US Laws:

- **ECPA (Electronic Communication Privacy Act):** laws restricting government from putting wiretaps on phone calls and electronic communication in the form of data

- **GLBA (Graham-Leach-Bliley Act):**
  - aka Financial Services Modernization Act of 1999
  - allow banks to merge with insurance companies and financial institutions
  - customer account information is kept secure and private
  - customers may opt out of any information-sharing arrangements from bank/insurer

- **SOX (Sarbanes-Oxley Act):**
  - transparency in publicly traded corporation’s financial activities
  - includes provisions for securing data and expressly names the traits of CIA
  - US legislation enacted to protect shareholders and the public from enterprise accounting errors and fraudulent practices

- **HIPAA (Health Insurance Portability and Accountability Act):** protect patient records and data; known as ePHI

- **FERPA (Family Educational Rights and Privacy Act):** prevent academic institutions from sharing student data with anyone other than parents or students (after age 18)

- **DMCA (Digital Millennium Copyright Act):** provisions to protect owned data; cracking of access controls on copyrighted media a crime and enables holders to require any site to remove content

- **CLOUD Act (Clarifying Lawful Overseas Use of Data):** allows US law enforcement and courts to compel American companies to disclose data stored in foreign data centers

- **FedRAMP:** not a law, but a US federal program that mandates standardized approach to security assessments, authorization, and continuous monitoring of cloud products/services; FedRAMP certification is required for cloud hosting services provided to a US government agency or contractor

### Personal Data and Privacy

- PII:

- **Direct Indicators:**
  - data elements that immediately reveal a specific individual
  - mobile phone number, IP address, SSN, birthday, home address, name
  - depends on jurisdiction

- **Indirect Indicators:**
  - characteristics/traits of an individual can reveal the identity of a person
  - not sensitive data but collect enough of it will reveal a person
  - location, birthplace, pets, industry, etc. Ex: a man born in Wisconsin, living in New Orleans, owns a dog, works in security

- **Anonymization:** removing identifiers; certain jurisdictions, laws, and standards require this for both indirect/direct identifiers

- **Federal PII law that complies with the EU Privacy Regulation:**
  - The EU, Australia, and New Zealand, Argentina, EFTA (Switzerland, Norway, Iceland, Lichtenstein), Israel, Japan, Canada
  - The USA does NOT
  - USA has an opt-out approach and EU has opt-in

- **GDPR (General Data Protection Regulation):**
  - the EU’s has the most significant and powerful privacy law in the world
  - describes handling of personal/private information of all EU citizens
  - codifies 7 principles:

- **Notice:** individual must be informed about PII being gathered or created

- **Choice:** individual can choose to disclose PII; need explicit agreement

- **Purpose:** individual must be told specific use of information

- **Access:** individual is allowed copies of PII

- **Integrity:** individual is allowed to correct information

- **Security:** entity holding PII is responsible for protecting PII and liable

- **Enforcement:** entities holding PII understand they are subject to enforcement actions by EU authorities

- **Privacy Shield:**
  - program for American companies to comply with GDPR within the EU
  - voluntarily agree to comply
  - administered by the DoC (Department of Commerce) a federal enforcement entity in the US
  - companies must agree to auditing and enforcement with fines assessed for violations

### Privacy Roles and International References

- **Data Subject:** individual whom PII refers; human being

- **Data Controller:**
  - entity collecting/creating PII
  - the cloud customer
  - responsible for any unauthorized disclosure of PII (with GDPR) regardless of fault

- **Data Processor:**
  - entity acting on behalf of data controller
  - performing any manipulation, storage, or transmission of PII
  - cloud service provider

- **Cloud Carrier:** intermediary who provides connectivity and transport of cloud services between cloud providers and cloud consumers

- Australian Privacy Act of 1988; Canada’s PIPEDA (Personal Information Protection and Electronic Documents Act); EFTA and Switzerland; APEC (Asia-Pacific Economic Cooperation) Privacy Framework

### Security Management Standards

- **ISMSs (Information Security Management Systems):**
  - holistic overview of the entire security program within an org
  - detailed in ISO 27001
  - provides a standardized international model for development and implementation of policies, procedures, and standards in a top-down approach in addressing and managing risk in an org

- **ISO/IEC 27017:** 2015: set of standards regarding the guidelines for information security controls applicable to the provision and use of cloud services and customers; standard for providing cloud services and how customer information/privacy should be controlled

- **ISO/IEC 27018:** 2019: focuses on code of practice and security techniques for processing PII in cloud services

- **Laws:** legal rules created by government entities/legislatures

- **Regulations:** rules created by governmental agencies

- **Standards:**
  - dictate reasonable level of performance
  - created by an org (internal) or industry bodies/trade groups (external)
  - following standards can reduce liability and compliance represents due care

### Electronic Discovery and Forensics

- **eDiscovery:** process of identifying and obtaining electronic evidence for prosecutorial or litigation purposes; ISO 27050 is the industry standard and guidance

- ISO Global Digital Forensic Standards:

- **ISO/IEC 27037:** 2012: guide for collecting, identifying, and preserving electronic evidence

- **ISO/IEC 27041:** 2015: guide for incident investigation

- **ISO/IEC 27042:** 2015: guide for digital evidence analysis

- **ISO/IEC 27043:** 2015: incident investigation principles and processes

- **ISO/IEC 27050-1:** 2016: overview and principles for eDiscovery

## Chapter 11 – Legal and Compliance Part II

### Risk Indicators and Controls

- **KRIs (Key Risk Indicators):**
  - metrics used by an org to inform management of impending negative impact to operations
  - involves algorithms and rating systems ascribed to factors selected by analysts and management for an early-warning system
  - forward-looking, helps an org understand risks/events already occurred and impacted the business

- **KPIs (Key Performance Indicators):**
  - backward-looking
  - metrics to gauge business critical initiatives, objectives, or goals
  - measurable benchmarks against defined goals

- **Risk Appetite/Tolerance:** how the org views risks; senior management dictates the amount of risk an org is willing to take

- **Risk Profiles:** comprehensive analysis of the possible risks to the org; include a survey of various operations the org is engaged in, public perception, pending legislation, stability of countries where org operates

- **Physical Controls:** physical access to assets that reduces the impact of a physical event; locks, fire suppression, fences, guards

- **Technical Controls:**
  - aka logical controls
  - controls that enhance the CIA triad
  - encryption, ACLs, audit trails, logs

- **Administrative Controls:** processes and activities that provide aspects of security; background checks, scheduled log reviews, mandatory vacations, robust/comprehensive security policies/procedures, designing business processes

### Risk Management Frameworks

- Risk Management Framework (RMF):

- **ISO 31000:** 2018: international standard focusing on design, implementing, and reviewing risk management processes and practices

- **NIST SP 800-37 (Guide for Implementing the RMF):** a methodology for handing all organizational risk in a holistic, comprehensive, and continual manner; relies on automated solutions

- **ENISA (EU Agency for Network and Information Security):**
  - EU counterpart to NIST
  - standard and model developed in EU
  - responsible for producing Cloud Computing: Benefits, Risks, and Recommendations for Information Security
  - identifies top eight security risks based on likelihood and impact

- COBIT

- **ISO/IEC 31010:** 2009: RM techniques

### Risk Scales and Assurance

- Risk Management Metrics:

- **5:**
  - Critical
  - 4 – High
  - 3 – Moderate
  - 2 – Low
  - 1 – Minimal

- **ISO/IEC 15408-1:** 2009 (Common Criteria Assurance Framework): provide assurances for security claims by vendors; assurance for security products customers purchase have been thoroughly tested by 3rd party testers and meets requirements

- **ISO 28000:** 2007: applies to security controls in supply chains

### Cloud Security Alliance Resources

- **CSA STAR (Security, Trust, and Assurance Registry):**
  - single consistent framework for evaluating cloud providers
  - registry of security controls provided
  - designed for users to assess cloud providers, security providers, and advisory and assessment service firms as part of their vendor management due diligence while choosing providers

- **CCM (Cloud Controls Matrix):**
  - list of security controls and principles appropriate for cloud environment, cross-referenced to other control frameworks (COBIT, ISO, NIST, FedRAMP, PIPEDA)
  - aids in selecting/implementing appropriate controls for regulatory frameworks
  - an inventory of cloud service security controls that are arranged into separate security domains

- **CAIQ (Consensus Assessments Initiative Questionnaire):** self-assessment by cloud providers, detailing evaluation of practice areas and control groups

### CSA STAR Program

- **CSA STAR Program:** Open Certification Framework:

- **Level One:** Self-Assessment: requires release and publication of due diligence assessment against CSA’s CAIQ/CCM

- **Level Two:** CSA STAR Attestation: requires release and publication of available results of assessment from 3rd party based on CSA CCM and ISO 27001:2013 or AICPA SOC 2

- **Level Three:** CSA STAR Continuous Monitoring: requires release and publication of results of continuous monitoring by certified 3rd party

## Additional Topics from the Source Notes

- **Information Commissioner:** responsible for enforcing UK’s GDPR and offering advice and assistance to both the council and individual groups whose information is being held

- **NIS Directive (EU2016/1148):** first piece of EU-wide cybersecurity legislation; must notify competent authorities or CSIRT

## Review Questions

1. How do physical, technical, and administrative controls differ?
2. How does risk acceptance differ from avoidance?
3. What is the purpose of a gap analysis?

<details>
<summary>Check your answers</summary>

1. Physical controls protect facilities and equipment; technical controls use technology; administrative controls use policies and processes.
2. Acceptance retains a known risk; avoidance stops or changes the activity that creates it.
3. To compare the current state with a required baseline and identify differences.

</details>

[Previous section](05-Cloud-Operations-and-Recovery.md) · [Study index](../README.md)
