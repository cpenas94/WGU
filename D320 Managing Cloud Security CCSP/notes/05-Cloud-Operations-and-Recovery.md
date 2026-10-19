# Cloud Operations and Recovery

[Back to study index](../README.md)

Reorganized from **Updated 25pg Doc - CCSP Notes.docx**, the uploaded study notes. Chapter content is retained as source notes; formatting and topic grouping have been changed. These are unofficial notes, not a fully fact-checked guide. Verify dated standards, legal summaries, and absolute claims against the current course materials.

## Contents

- [Chapter 8 – Operations Elements](#chapter-8--operations-elements)
- [Chapter 9 – Operations Management](#chapter-9--operations-management)
- [Additional Topics from the Source Notes](#additional-topics-from-the-source-notes)
- [Review Questions](#review-questions)

## Chapter 8 – Operations Elements

### Availability and Data Center Tiers

- Industry service standard for uptime is five nines (99.999%), less than 6 downtime minutes a year

- **Conditioning:** involves adjusting the voltage on the line; includes surge protectors

- **Uptime Institute (UI):** advisory org to publish standards related to data center redundancy in pursuit of continuous operations, matters related to IT services, and certifies data centers for compliance

- **Tier 1:**
  - simplistic with little to no redundancy and labeled Basic Site Infrastructure
  - lists minimum requirements for a data center
  - dedicated space for IT systems, UPS system for line conditioning and backup purposes, sufficient cooling systems to serve all critical equipment, power generator for extended electrical outages with at least 12 hours of fuel to run the generator
  - useful for orgs to use as a backup, private cloud, cheaper to operate, a hot/warm/cold site

- **Tier 2:** named Redundant Site Infrastructure Capacity Components; good for orgs looking to operate in the public cloud environment and maintaining low overhead

- **Tier 3:**
  - known as Concurrently Maintainable Site Infrastructure
  - has added benefit of multiple distribution paths
  - there are dual power supplied for all IT systems
  - critical operations can continue even if any single component is out of service

- **Tier 4:**
  - Fault-Tolerant Site Infrastructure is premium data center offering
  - redundancy in both IT and electrical components
  - facility will feature automatic response capabilities for infrastructure control systems

### Hardware and Cluster Storage

- **TPM (Trusted Platform Module):**
  - specialized chip on a computer designed to secure hardware with integrated cryptographic keys
  - helps prove user’s identity and authenticate devices
  - provide security against firmware and ransomware attacks

- **Tightly Couped Cluster Storage:**
  - all storage devices are directly connected to a shared physical backplane
  - confined to restrictive design parameters
  - enhance performance as it scales

- **Loosely Coupled Cluster:**
  - allow greater flexibility
  - each nose of the cluster is independent
  - logically connected and do not share same proximate physical framework

### Storage Resiliency

- **Resiliency:** two general ways for disk data protection in a cloud storage cluster: RAID and data dispersion

- **RAID (Redundant Array of Independent Disks):**
  - all data is stored across various disks known as striping
  - allows data to be recovered if one drive fails
  - in some schemes (0-10) parity bits are added to raw data to aid in recovery after a drive failure

- **Data Dispersion:**
  - data is sliced into chunks (shards) that are encrypted with parity bits (erasure coding in cloud data dispersion) and written to various drives in the cloud cluster
  - the parity bits/erasure coding allows recovery of partial data lost by recreating the lost data from remaining data plus parity bits/erasure code
  - can be seen equivalent to RAID array in a cloud environment
  - often referred to as bit splitting
  - uses parity bits, data chunks, and encryption

- **SSMS (Secret Sharing Made Short):** method of bit splitting using 3 phases: encryption, using information dispersal algorithm, and splitting encryption key using secret sharing algorithm; fragments are signed and distributed to different cloud storage services

## Chapter 9 – Operations Management

### Logging and Operating Conditions

- **OS Logging:** integral toolsets for monitoring performance and events; set OS logs to alert admins when usage approaches a level of capacity utilization, performance degradation, CPU usage, memory usage, disk space, disk I/O timing (slow writing/reading to/from disk)

- ASHRAE Recommended Range for data centers:

- **Temperature:** 64-81 degrees F

- **Humidity:** Dew point 42-59 degrees F; 60% relative humidity

### Maintenance and Service Management

- **Maintenance Mode:**
  - all operational instances are removed from the system/device before entering this mode
  - prevent all new logins
  - ensure logging is continued
  - begin enhanced logging

- **CI/CD (Continuous Integration/Continuous Delivery):** incorporates heavy use of automation to shorten software delivery pipeline; includes administrative and technical controls

- **ISO/IEC 20000-1, Information technology:** Service Management: defines a set of operational controls and standards orgs can use to manage IT services; used to manage ITSM using approaches of ITIL and ISACA COBIT framework

- **ITSM (IT Service Management):** goal is to identify user needs, design IT service to meet those needs, deploy it, then enter a cycle of continuous improvements

### Business Continuity and Disaster Recovery

- BC/DR (Business Continuity and Disaster Recovery):

- Business continuity efforts are concerned with maintaining critical operations

- Disaster Recovery efforts are focused on resumption of operations due to disaster

- **Event:** unscheduled impact to operating environment; impact lasts three days or less, disasters last longer, an event can become a disaster

- The most important planning and efforts is health and human safety; notification, evacuation, protection, and egress will need to be prioritized

### Recovery and Risk Metrics

- **MAD (Maximum Allowable Downtime):** how long an interruption will stop operations; referred to as MTD (maximum tolerable downtime)

- **MTTR (mean time to repair):** average amount of time it takes to repair a system/device that is down

- **RTO (Recovery Time Objective):** BC/DR goal for recovery of operation, measured in time; must be less than the MAD

- **RPO (Recovery Point Objective):**
  - BC/DR goal for limiting loss of data from unplanned event, measured in time
  - example – org resumes critical operations at alternate operating site with last full backup (if they backup every day, RPO will be 24 hours), RPO for org will be loss of no more than one day’s worth of data
  - tolerable/acceptable amount of data that might be lost due to an outage before severe consequences are experienced.

- RSL % (Recovery Service Level):

- **ALE (Annual Loss Expectancy):** amount an org should expect to lose annually based on any one type of incident; ARO x SLE = ALE

- **ARO (Annual Rate of Occurrence):** rate of occurrence of a specific event/incident

- **SLE (Single Loss Expectancy):** amount of expected damage/loss from any single specific security incident

### Power Continuity

- UPS should last long enough for graceful shutdown of affected system, can provide line conditioning, adjusting power to optimize for the devices it serves and smooth power fluctuations; battery backup should only be relied on to provide immediate and near-term power supply; longer power supply should be provided by generators (short-term contingency)

- **Generators:** supply close to immediate power when utility electricity is interrupted and have automatic transfer switches (not a viable replacement for an UPS); minimum of 12 hours of fuel for all generators

### Recovery Exercises

- Testing:

- **Tabletop Testing:**
  - essential participants work together at a scheduled time
  - InfoSec equivalent of role-playing games
  - least impact on production of testing alternatives

- **Dry Run:** whole org takes part in a scenario at a scheduled time; impacts productivity

- **Full Test:**
  - entire org takes part in an unscheduled, unannounced practice scenario, performing full BC/DR activities
  - includes system failover, facility evacuation, used for detecting shortcomings in the plan
  - greatest impact on productivity

## Additional Topics from the Source Notes

- **Joint Operating Agreements:** provide nearby relocation sites so disruption is limited to the org’s own facility/campus and can be addressed at a different location

- **Logging Levels:**
  - OFF &gt
  - FATAL &gt
  - ERROR &gt
  - WARN &gt
  - INFO &gt
  - DEBUG &gt
  - TRACE &gt
  - ALL

- **OFF:** used to turn off logging

- **FATAL:**
  - application is about to stop a serious problem/corruption
  - the situation is catastrophic
  - application is unable to connect to the data store

- **ERROR:**
  - inability to access a service/file
  - failure of something important in the application
  - when a severe issue is stopping functions within the application from operating efficiently, will continue to run but will need to be addressed

- **WARN:** detected an unexpected application problem

- **INFO:** normal behavior of applications

- **DEBUG:** diagnostic information in a detailed manner; fetch information to diagnose, troubleshoot, or test an application

- **TRACE:**
  - captures all details about behavior of application
  - used when you need to see events within application and what happened in 3rd party libraries
  - use to query parameters in the code or interpret algorithm’s steps

- **ALL:** shows all or customed logged defined

- **Chaos Engineering:** method of testing software that deliberately introduces failure and faulty scenarios to verify resilience

- **NIST 800-92:** log management

- **NIST 800-40:** enterprise patch management planning

- Backup Types:

- Full

- Copy

- **Differential:**
  - all data changed since last full backup
  - if a full back up was done on a Sunday, a differential backup will be done on Monday for only the files that changed since Sunday, Tuesday you back up only files that changed since Sunday (adding)
  - quicker than a full backup but storage space will be used until another full back up is done

- **Incremental:** backs up data that changed since last backup; time consuming to restore data

## Review Questions

1. How do RTO and RPO differ?
2. What do you need to restore the latest differential backup?
3. What does a tabletop exercise practice?

<details>
<summary>Check your answers</summary>

1. RTO is the target time to restore service; RPO is the acceptable data-loss window measured in time.
2. The full backup and the latest differential backup.
3. Participants discuss a scenario and their response responsibilities without a production failover.

</details>

[Previous section](04-Cloud-Application-Security.md) · [Study index](../README.md) · [Next section](06-Legal-Compliance-and-Risk.md)
