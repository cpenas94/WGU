# Cloud Data Security

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 3 – Data Classification](#chapter-3--data-classification)
- [Chapter 4 – Cloud Data Security](#chapter-4--cloud-data-security)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 3 – Data Classification

### Data Ownership and Roles

- **Data Ownership:** assign responsibilities according to who has possession and legal ownership of that data; roles are assigned to allocate this

- **Data Owner:**
  - org that collected/created the data
  - usually department head/business unit manager
  - cloud customer is usually the data owner (international treaties/frameworks refer to as the data controller)

- Data owners remain legally responsible for all data they own

- **Data Custodian:**
  - person or entity tasked with the daily maintenance/administration of the data
  - role of proper security controls and processes as directed by the data owner
  - sometimes a database admin

- **Data Processor:** any org or person who manipulates, stores, or moves the data on behalf of the data owner; cloud provider is a data processer (international law)

- Data processors do not necessarily all have direct relationships with data owners; processors can be third parties or further removed down the supply chain

### Lifecycle and Categorization

- **Data Lifecycle:**
  - understand it in order (Create &gt
  - Store &gt
  - Use &gt
  - Share &gt
  - Archive &gt
  - Destroy)

- **Create:**
  - data owner will be identified in this first phase
  - data security and management responsibilities require action
  - data owner will categorize the data

- Data Categorization:

- **Regulatory Compliance:** can categorize by specific datasets (GLBA, PCI, SOX, HIPAA, GDPR, other international, national, and local compliance)

- **Business Function:** different use of data (billing, marketing, operations)

- **Functional Unit:** department or office with its own category and data controls

- **By Project:** define datasets by projects associated with as means of creating discrete, compartmentalized projects

### Classification Mapping and Labels

- **Data Classification:** responsibility of the data owner; assigned by the org’s policy based on characteristics of dataset

- **Sensitivity:** used by the US military; assigned to the sensitivity of the data, based on negative impact an unauthorized disclosure would cause

- **Jurisdiction:** geophysical location of the source/storage point of the data might determine how the data is handled; PII gathered from citizens from EU is subject to the EU privacy laws

- **Criticality:** data deems critical to org survival classified in a manner distinct from trivial, basic operational data; BIA helps determine this

- **Data Mapping:** data between organizations (or departments) normalized and translated so it is meaningful to both parties; in classifications, mapping is necessary so data that is sensitive must be protected in one org must be recognized by the receiving org

- **Data Labeling:**
  - when data owner creates, categorizes, and classifies the data, it also must be labeled
  - should indicate who the data owner is (office or role, not name or identity)
  - should take any form to be enduring, understandable, and consistent
  - Ex: labels on hardcopy data might be printed headers/footers, labels on electronic files might be embedded in the filename/nomenclature
  - labels should be evident and communicate pertinent concepts without disclosing data they describe
  - labels may include:

- Date of creation; Date of scheduled destruction/disposal; Confidentiality level; Handling directions; Dissemination/distribution instructions; Access limitations; Source; Jurisdiction; Applicable regulation

### Discovery and Analytics

- **Data Discovery:** used to refer several kinds of tasks to determine and accurately inventory the data under its control; org is attempting to create an initial inventory of data it owns, org is involved in electronic discovery (e-discovery), and can modern the use of datamining tools to discover trends and relations in the data already in the org’s inventory

- **E-Discovery:** legal term for how electronic evidence is collected as part of an investigation/lawsuit

- **Label-Based Discovery:**
  - labels created will aid in any data discovery efforts
  - org can determine what data it controls and amounts of each kind
  - labels are useful when the discovery effort is undertaken in response to a mandate with specific purpose (court order/regulatory demand)
  - can easily collect and disclose all appropriate data if labeled

- **Metadata-Based Discovery:**
  - data about data, a listing of traits and characteristics about specific data elements/sets
  - can be useful for discovery purposes
  - data discovery uses metadata the same way as labels to scan field for particular terms for certain purposes

- **Content-Based Discovery:** discovery tools can be used to located and identify specific kinds of data by delving into the content of datasets (even without labels/metadata); basic term searches or sophisticated pattern-matching technologies

- **Data Analytics:**
  - technological options to provide additional findings and assigning types to data
  - modern tools create new data feeds from sets of data that already exist within the environment
  - modes used are real-time analytics, datamining, and agile business intelligence

- **Datamining:** an outgrowth of the possibilities offered by regular use of the cloud (big data); when org collects data streams and run queries across the feeds, the org can detect and analyze previously unknown trends and patterns that can be useful

- **Real-Time Analytics:** tools can provide datamining functionality concurrently with data creation and use; the tools rely on automation and require efficiency to perform properly

- **Agile Business Intelligence:** state-of-the-art datamining involves recursive, iterative tools and processes that can detect trends and identify more oblique patterns in historical and recent data

### Jurisdictional Requirements

- **United States:**
  - address privacy with industry-specific legislation (GLBA for banking/insurance, HIPAA for medical care, etc.) or with contractual obligations (PCI)
  - granular data breach notification laws exist that are enforced by states and localities (New York/California)
  - strong protections for intellectual property

- **Europe:** has massive, exhaustive, comprehensive personal privacy protections (EU General Data Protection Regulation); good intellectual property protection

- **Asia:**
  - data privacy protection levels differ by country
  - with its Act on the Protection of Personal Information, Japan and Singapore adheres to the EU model, China has a legal requirement the opposite of privacy (all IT traffic and communications in China must be accessible by the Chinese government)
  - disparate levels of intellectual property protection

- **South/Central America:**
  - most countries lack privacy protection frameworks
  - Argentina is an exception
  - their Personal Data Protection Act is in direct correlation with the EU legislation
  - has various intellectual property mechanisms

- **Australia/New Zealand:** has the Australian Privacy Act mapping directly to the EU statutes; provide strong intellectual property protections and strong privacy protections

### Information Rights Management

- **IRM (Information Rights Management):**
  - managing information in accordance with who has rights to it
  - can be DRM (digital/data rights management), ERM (enterprise)
  - uses a variety of tools to enforce intellectual property rights such as support-based licensing, local agent enforcement, and media-present checks

### Intellectual Property Protections

- **Intellectual Property Protections:** intangible; assets of the mind

- **Copyright:**
  - legal protection for expressions of ideas
  - in the US, granted to anyone who first creates an expression of an idea (literary works, films, music, software, and artistic works)
  - does not cover ideas, specific words, slogans, recipes, formulae
  - lasts for 70 years after the author’s death/120 years after the first publication of a work for hire
  - creator is the only entity legally allowed to do the following: perform the work publicly, profit from the work, make copies of the work, make derivative works from the original, import or export the work, broadcast the work, sell/assign the rights

- **Trademarks:**
  - intended to be applied to specific words and graphics
  - representations of an org – its brand
  - can be the name of an org, logo, phrase, color, sound, or combo of these

- **Patents:** legal mechanism for protecting intellectual property in the form of inventions, processes, materials, decorations, and plant life; lasts about 20 years from time of patent application

- **Trade Secrets:** has same aspects as patented material (processes, formulas, commercial methods, etc.); includes aggregations of information (list of clients/supplies)

### IRM Tools and Licensing

- **IRM Tool Traits:** material protected by IRM solutions need some form of labeling/metadata associated with the material for the IRM tool to function properly

- **Rudimentary Reference Checks:** content itself can check for proper usage/ownership; Ex: vintage games will pause in operation until player entered information acquired with the purchase of a licensed copy of the game (word/phrase from manual shipped with game)

- **Online Reference Checks:** Microsoft software packages (Windows OS/Office programs) requiring product key at installation; program will check against online database when connected to the Internet

- **Local Agent Checks:** user installs reference tool that checks the protected content against the user’s license; Ex: Steam when installing games purchased, agents check user’s system against online license database to ensure games are not pirated

- **Presence of Licensed Media:** disks for example, is required to be present when the content is being used; IRM engine is on the media, often installed with a cryptographic engine that identifies the unique disk and the licensed content and allowing usage based on that relationship

- **Support-Based Licensing:** predicted on the need of continual support for content (production software); vendor can prevent unlicensed versions from getting support (updates/patches)

### IRM in the Cloud Complications

- **Replication Restrictions:** IRM often prevent unauthorized duplication, the cloud may create, close, and replicate virtualized host instances; IRM might interfere with automatic resource allocation processes

- **Jurisdictional Conflicts:** cloud extends across boundaries and borders, often pose problems when intellectual property rights are restricted by locale.

- **Agent/Enterprise Conflicts:** IRM solutions that require local installation of software agents for enforcement purposes might not always function properly in the cloud environment, virtualization engines, or various platforms used in BYOD enterprise

- **Mapping IAM (Identity and Access Management) and IRM:** the extra layer of access control (ACLs) will cause a conflict between IRM IAM and enterprise/cloud IAM; more possible if these functions are outsourced to a third party (CASB)

- **API Conflicts:** IRM tool is often incorporated into the content, usage of material might not offer the same level of performance across different applications (content readers/media players)

### IRM Functions

- **Persistent Protection:** follow the content it protects regardless of location, if it’s duplicated or original file, or how it’s being utilized

- **Dynamic Policy Control:** should allow content creators and data owners to modify ACLs and permissions for the protected data under their control

- **Automatic Expiration:**
  - because of the nature of legal protections of intellectual property, a significant amount of digital content will not be protected in perpetuity
  - protection should cease when legal protections cease
  - licenses also expire, access and permissions for protected content should expire

- **Continuous Auditing:** allow for comprehensive monitoring of the content’s use and access history

- **Replication Restrictions:** purpose of IRM is to restrict illegal or unauthorized duplication of protected content; IRM solutions should enforce restrictions across the many forms of copying that exist (screen-scraping, printing, electronic duplication, email attachments)

- **Remote Rights Revocation:** owner of rights to intellectual property should have ability to revoke rights at any time; used because of litigation/infringement

### Data Control and Retention

- **Data Control:** protect data other than in the CREATE lifecycle phase; each aspect of data management (retention, audit, disposal) will need a specific policy addressing it

- Data Retention Policy

- **Retention Periods:**
  - length of time organization should keep data
  - data being archived for long-term storage, reduce data footprint, reduce duplicate data
  - not being used in production
  - expressed in number of years, set by regulation/legislation
  - can be mandated/modified by contractual agreements

- **Applicable Regulation:** can be mandated by statute/contract; policy should refer to all applicable regulatory guidance

- **Retention Formats:** contain description of how data is actually archived (type of media storage, handling specifications); Ex: some types of data are required to be encrypted while in storage, policy should include description of encryption engine, key storage and retrieval procedures, and reference to regulation(s).

- **Data Classification:** org can use classification level of data to determine how long specific datasets/types of data need to be retained

- **Archiving and Retrieval Procedures:** mandate the creation of a detailed description of the processes both for sending data into storage and recovery; usually attach to policy or mentioned by reference, usually kept separate

- **Monitoring, Maintenance, and Enforcement:** list in detail how often it will be reviewed, amended, by whom, consequences for failure to adhere to policy, and which entity is responsible for enforcement

- **Legal Hold:**
  - supersede org’s retention/destruction policies
  - when law enforcement/regulatory/private entity is commencing litigation against the org, they must suspend all relevant data destruction activities until fully resolved (only relevant data)
  - concept is dictated by the Federal Rules of Evidence (HIPAA)
  - considered temporary paramount retention period

### Audit and Disposal

- **Data Audit:**
  - org need to regularly review, inventory, and inspect usage and condition of data it owns
  - should have policy for conducting audits and include audit periods
  - scope
  - responsibilities (internal/external)
  - processes/procedures
  - applicable regulations
  - monitoring, maintenance, and enforcement
  - audit is predicated on logging (event
  - security
  - traffic)
  - data audit policy addresses activities that take place in all phases of the data lifecycle

- **Data Destruction/Disposal:**
  - because of the cloud environment, hardware destruction or overwriting storage area is nearly impossible
  - crypto-shredding will be the sole pragmatic option for data disposal in the cloud
  - must include in the policy the process for data disposal, regulations, clear directions of when data should be destroyed
  - addresses activities in the DESTROY phase of data lifecycle

- **Crypto-Shredding (Cryptographic Erasure):** encrypt the data with a strong encryption engine, take the keys generated and encrypt them with a different encryption engine, then destroying the resulting keys of the second round of encryption

## Chapter 4 – Cloud Data Security

### Security Across the Data Lifecycle

- **Data Lifecycle:**
  - Create &gt
  - Store &gt
  - Use &gt
  - Share &gt
  - Archive &gt
  - Destroy

- **Create:** defines classification levels

- **Data created remotely:**
  - data created by the user should be encrypted before uploading to the cloud
  - protects against MIIM attacks/insider threats at cloud data center
  - connection should be secure too (IPsec or TLS VPN solution)

- **Data created within the cloud:** should be encrypted upon creation; allows both read and process functions to be performed

- **Store:**
  - usually refer to near-term storage
  - this phase will happen when the data is created (occurs simultaneously)
  - encryption at rest/transit should happen before this phase begin

- **Use:**
  - platforms used to connect to data in the cloud needs to be secure (VPN, IRM, DLP)
  - for BYOD, a holistic approach should be used
  - data owners should restrict permissions
  - logging and audit trails are important when data are manipulated
  - on provider’s side, strong protections should be implemented, ensure virtualized data can’t be read/detected by other hosts on the same device

- **Share:**
  - craft sharing restrictions based on jurisdiction
  - limit/prevent data being sent to certain locations (export/import controls)
  - implement some form of egress monitoring
  - uses content delivery networks

### Export and Import Restrictions

- **ITAR (International Traffic in Arms Regulations:** US): State department prohibit defense-related exports (includes cryptography systems)

- **EAR (Export Administration Regulations:** US): Department of Commerce prohibits dual-use items (technologies used for both commercial/military purposes)

- **Cryptography (Various):** many countries restrict on importing cryptosystems/materials that has been encrypted

- **The Wassenaar Arrangement:** group of 41 members have agreed to mutually inform each other about conventional military shipments to nonmember countries; not a treaty, not legally binding, may require org to notify government to stay within compliance

- **Archive:**
  - phase for long-term storage
  - cryptography is the essential consideration
  - key management is important, if lost, can lead to exposure or total loss
  - weigh in the risk of physical security (location, format, staff, procedure

- **Destroy:** crypto shredding is the only feasible and thorough means available

### Cloud Storage Architectures

- **Volume Storage:**
  - customer is allocated storage space
  - represented as an attached drive to user’s VM
  - can take forms of file-based/block storage/raw disk storage
  - includes bit splitting and erasure coding, a means of implementing data protection solutions similar to RAID arrays
  - often associated with IaaS
  - user/admin can install/run programs

- **Threats:**
  - since it’s a drive space, all traditional data storage threats remain
  - malware, deletion of data, and physical disk failure
  - since data is stored in the cloud, MiiM exists

- **Block Storage:**
  - provides low latency and high-performance values
  - useful for structured storage
  - blank volume customer can put anything into
  - allow more flexibility and higher performance, requires greater amount of administration, installation of an OS or app to store, sort, and retrieve the data
  - better suited for a volume and purpose that includes data of multiple types and kinds (enterprise backup services)

- **File Storage (File-Level Storage/File-Based Storage):** data stored/displayed with a file structure in a traditional environment (files/folders) with same hierarchical and naming functions; popular with big data analytical tools/processes

- **Object-Based Storage:**
  - best used for large unstructured data when durability, unlimited storage, scalability, and metadata management are factors for overall performance
  - customers are given access to parts of the hierarchy
  - include actual production content, metadata describing the content/object, and unique address identifier for locating object across entire storage space
  - allow for significant level of description (marking, labels, classification, categorization)
  - enhances opportunities for indexing capabilities, data policy enforcement (IRM, DLP), and centralization of data management functions
  - stores presentations, documents, audio files
  - usually associated with IaaS

- **Threats:**
  - object storage doesn’t have a runtime environment
  - risk of malware is reduced but parasitical viruses can infect specific files
  - loss due to physical disk failure
  - ransomware attacks

- **Ephemeral Storage:**
  - temporary resource used for processing
  - referred to as instance store volumes
  - provided by devices directly connected to a host machine
  - analogous to RAM for cloud VM

- **Threats:** data will be lost if VM instance is shut down or physical drive fails

- **Long-Term Storage:**
  - durable data storage capacity
  - offered at low cost and large amounts
  - used for archiving/backups
  - not used for production environments or installing/running programs
  - can run queries and analyze data stored

- **Threats:**
  - insider threat
  - intermediary (MiiM attacks)
  - ransomware
  - vendor lock-in

- **SAN (Storage Area Network):** dedicated high-speed network that interconnects and deliver shared pools of storage devices on multiple servers

- **iSCSI:** makes it possible to set up a shared-storage network where multiple servers and clients can access central storage resources; creates a SAN

- **NAS (Network Attached Storage):** remote storage accessed; hosted by 3rd party service provider

- **Databases:**
  - provide some structure for stored data
  - arranged according to characteristics and elements in the data itself (trait required to file the data know, primary key)
  - usually backend storage in the data center, accessed by users utilizing online apps/APIs through a browser
  - PaaS and SaaS

- **CDN (Content Delivery Network):**
  - used for large amounts of data that require time-sensitive communication and low latency
  - a form of data caching, usually near geophysical locations of high use/demand, for copies of data commonly requested by users
  - Ex: online multimedia streaming services, improves bandwidth and delivery quality

- **Threats:**
  - intermediaries
  - insider threats
  - malware

### Encryption and Key Management

- **Key Management:**
  - how and where encryption keys are stored can affect the risk of data
  - keys must be secured at the same level of control (level of protection)
  - must have key recovery (usually multiple people with access to a portion of the key)
  - key distribution
  - key revocation
  - key escrow (copies of keys by trusted third party)
  - outsourcing key management

- **HSM (Hardware Security Module):**
  - device that safely store and manage encryption keys
  - used in servers, data transmission, and log files
  - far stronger than saving/storing in software

### Masking and Data Protection Methods

- **Key Protection Methods:** Masking, Obfuscation, Anonymization, and Tokenization

- **When to use it?:**
  - Test environments
  - enforcing least privilege
  - secure remote access

- How to perform these activities?:

- **Randomization:** replace part/all of the data with random characters

- **Hashing:** one-way cryptographic function to create a digest of the original data

- **Shuffling:** using different entries from within the same data set to represent the data

- **Masking:** hiding data with useless characters; XXX-XX-1234

- **DDM (Dynamic Data Masking):** replace sensitive data in transit leaving original at-rest data unaltered

- **SDM (Static Data Masking):** permanently replaces sensitive data by altering data at rest

- **Nulls:** deleting raw data from display before represented or displaying null sets

- **Obfuscation:** the application of any of the above techniques to make the data less meaningful, detailed, or readable to protect the data; can be done in static/dynamic matter

- **Anonymization (Deidentification):** can be difficult, sensitive data must be recognized and marked as sensitive when created, determining sensitivity might not be simple since data is input into open fields; mark creates metadata which can be valuable to attackers

- **Tokenization:**
  - practice of having two distinct databases: one with live, actual sensitive data
  - one with nonrepresentational tokens mapped to each piece of that data
  - user/program is authenticated by the token server
  - adds significant overhead but creates extra degree of security (relieve org dependence on encryption)
  - placing sensitive data with unique identification symbols
  - a way of hiding or concealing sensitive data by representing it with unique identification symbols/addresses, retains essential information w/o compromising security

### Monitoring and Data Loss Prevention

- **SIEM (security information and event management):**
  - goals implementation of SIEM are to centralize collection of log data
  - enhance analysis capabilities
  - dashboarding
  - automated response

- **Egress Monitoring (DLP):**
  - examining data as it leaves the production environment (DLP – data loss, leak prevention, and protection)
  - some major goals are, additional security
  - policy enforcement
  - enhanced monitoring
  - regulatory compliance
  - can be added to IRM tools to control intellectual property

## Additional Topics from the Source Notes

- **PKI:** framework of programs, procedures, communication protocols, and public key cryptography that enables a diverse group of individuals to communicate securely

- **FPE (Format-Preserving Encryption):** technique used to scramble contents of data using mathematical algorithm while keeping the structural arrangement of the data

- **PRE (Proxy Re-Encryption):** allows a proxy (3rd party) to convert a ciphertext encrypted under one key into an encryption of the same message under another key; place as little trust and reveal as little information to the proxy to allow it to perform its translations

## Review Questions

1. How do classification and labeling differ?
2. Why can ephemeral storage complicate investigations?
3. How does hashing differ from encryption?

<details>
<summary>Check your answers</summary>

1. Classification assigns a sensitivity or business category; labeling records that category and handling information.
2. Temporary storage may disappear when its instance is terminated, taking evidence with it.
3. Hashing produces a one-way digest; encryption is designed to be reversed with the appropriate key.

</details>

[Previous section](01-Cloud-Foundations.md) · [Study index](../README.md) · [Next section](03-Cloud-Infrastructure-and-Responsibilities.md)
