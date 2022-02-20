---
description: CureDAO data security policies and incident management
---

# 🔓 Data Security

### DATA SECURITY POLICY IN BRIEF

CureDAO focuses on security from the ground up. Our Data Center (managed by Amazon Web Services) is SAS 70 Type II certified, SSAE16 (SOC 2) Compliant, and features proximity security badge access and digital security video surveillance. Our server network can only be accessed via SSL VPN with public key authentication or via Two-factor Authentication over SSL. We run monthly Qualys Vulnerability Assessments on our production environment. Additionally, our network can only be accessed via multi-factor authentication, and all access to our web portal is secured over HTTPS using SSL 256-bit encryption. Additionally, all staff members with access to Client Data receive certification as a HIPAA Privacy Associate.

DEFINITION OF TERMS & SYSTEM USERS:

* Client — A customer of CureDAO.
* User — An individual with access to a CureDAO Application.
* Admin — A Client User with the capability of viewing and managing certain aspects of the Client's CureDAO Account.
* Member — A Client User whose account is provisioned through Client’s Web Portal. A Member cannot log in or otherwise access any CureDAO Application directly. All Member Data stored in our system is de-identified in compliance with the HIPAA “Safe Harbor” de-identification standard.
* Developer — A User that can create vendor applications in CureDAO for the purpose of integrating mobile health apps and/or devices.
* CureDAO Admin — A CureDAO employee with access to managing a Client’s account.

### DATA CENTER AND HARDWARE

All CureDAO application and database servers are physically managed by Amazon Web Services in secure data centers within the United States. Our security procedures utilize industry best practices from sources including The Center for Internet Security (CIS), Microsoft, Red Hat, and more. All data center facilities are certified SSAE 16 (SOC 2) Compliant and have 24/7 physical security of data centers and Network Operations Center monitoring.

### Physical Security

All servers are located in Data Centers managed by Amazon Web Services within the United States. Physical access is controlled both at the perimeter and at building ingress points by professional security staff utilizing video surveillance, intrusion detection systems, and other electronic means. CureDAO employees do not have access to physical server hardware.

### Data Access and Server Management Security

CureDAO has IPSec VPN connections to our hosting environment. Only select CureDAO employees are able to access the server network.

### Environmental Safeguards

All Amazon Web Services data centers are equipped with automatic fire detection and suppression (either wet-pipe, double-interlocked pre-action, or gaseous sprinkler systems), climate and temperature controls ,fully redundant uninterruptible Power Supplies (UPS), and generators to provide back-up power for each physical site.

### DATA STORAGE AND BACKUPS

All Member Data stored in our system is de-identified in compliance with the HIPAA “Safe Harbor” de-identification standard, and all data is encrypted at rest using 256-bit AES. CureDAO production database servers are replicated across multiple availability zones. Database backups use a fully disk-based solution (disk-to-disk) and full system backups are performed daily, weekly, and monthly. Daily backups are retained for a minimum of 7 days, weekly backups are retained for a minimum of 4 weeks, monthly backups are retained for 3 years. Backups are stored in multiple geographic availability zones within Amazon Web Services.

### Client Data Policies

Client Data includes data stored by Clients in CureDAO applications, information about a Client’s usage of the application, data instances in the CRM system that we have access to, or data that the Client has supplied to use for support or implementation. Here are the special considerations we take into account when managing Client Data:

1. Client Data is not to be disclosed outside of CureDAO, except to the Client who owns the data or to a Partner who has been contracted by the Client to manage or support their account. Client Data should only be shared using a secure sending method. Approved sending and sharing methods include Dropbox, Google Drive, emailing of encrypted files or use of a Client-provided secure transfer method.
2. Client Data should only be stored temporarily outside of the CureDAO Application if at all. If there is a need to archive Client Data (for example, data provided by a Client during implementation or training), the data should be stored on a central file server and deleted from any personal computers. This includes report exports, contact lists, and presentations that contain Client information, and Client agreements.
3. Client Data should only be accessed on a need-to-know basis. Specifically, a Client’s account should only be accessed to provide support, troubleshoot a problem with that account, or for supporting the system as a whole.
4. Client Data should never be changed except with the explicit permission of the Client, with the exception of repairing data quality issues.

### Destruction of Server Data

In order to maintain system integrity, Client Data that has outlived its use is retained up to 60 days before it is destroyed. The data may remain in our backup files for up to 14 months, as it is our policy to maintain weekly backups for a minimum of 52 weeks before those backups are destroyed. De-identified activity data from Members may be stored in perpetuity for future analysis.

### Disposal of Computers and Other Data

Old computers and servers used to store or access client information receive a 7-pass erase that meets the U.S. Department of Defense 5220-22 M standard for erasing magnetic media; the devices are then recycled or resold to manufacturers. Paper information in the office is discarded using a document shredder or a commercial secure document shredding service.

### Incident Response

CureDAO security administrators will be immediately and automatically notified via email if implemented security protocols detect an incident. All other suspected intrusions, suspicious activity, or system unexplained erratic behavior discovered by administrators, users, or computer security personnel must be reported to a security administrator within 1 hour.

Once an incidence is reported, security administrators will immediately begin verifying that an incident occurred and the nature of the incident with the following goals:

1. Maintain or restore business continuity
2. Reduce the incident impact
3. Determine how the attack was performed or the incident happened
4. Develop a plan to improve security and prevent future attacks or incidents
5. Keep management informed of the situation and prosecute any illegal activity

#### Determining the Extent of an Incident

Security administrators will use forensic techniques including reviewing system logs, looking for gaps in logs, reviewing intrusion detection logs, interviewing witnesses and the incident victim to determine how the incident was caused. Only authorized personnel will perform interviews or examine the evidence, and the authorized personnel may vary by situation.

#### Notifying Clients of an Incident

Clients will be notified via email within one hour upon detection of any incident that compromises access to the service, comprises data, or otherwise affects users. Clients will receive a status update every 4 hours and upon incident resolution.

### APPLICATION SECURITY

All data transfer and access to CureDAO applications will occur only on Port 443 over an HTTPS encrypted connection with 256-bit SSL encryption.

### System Updates and Security Patches

As a hosted solution, we regularly improve our system and update security patches. No client resources are needed to perform these updates. Non-critical system updates will be installed at predetermined times (typically 2:00 a.m. Eastern on Thursdays). Critical application updates are performed ad hoc using rolling deployment to maximize system performance and minimize disruption. All updates and patches will be evaluated in a virtual production environment before implementation.

### Vulnerability and Security Testing

CureDAO performs Qualys Vulnerability Assessments and creates external security reports of our production environment once a month. Additional internal security testing is performed on the testing environment before code is checked into a master repository.

### User Login and Session Security

All Member logins and sessions are authenticated via a secure OAuth 2.0 access token.

#### Application Password Management

Admin passwords must have at least 8 characters with at least one number and one letter.

CureDAO Admin passwords must have at least 8 characters with at least one number and one letter and at minimum either one capital letter and/or one special character.

### DISASTER RECOVERY

CureDAO maintains real-time data stores mirrored across multiple geographic availability zones in Amazon Web Services within the United States. In a disaster situation, the full CureDAO platform will be recreated and available in a different availability zone within 1hr of the disaster declarations.

### HIPAA & PHI COMPLIANCE

In addition to the above HIPAA compliant policies for data storage and handling, the following procedures are in place to ensure HIPAA compliance:

1. All CureDAO employees receive annual HIPAA Business Associate training and certification
2. CureDAO web-based applications receive annual internal HIPAA audits

### PHI Handling Policy

All CureDAO staff members are made aware of relevant external regulations as part of their induction process, and all staff who may come into contact with PHI are trained in our PHI handling processes.

CureDAO anonymizes PHI upon receipt and destroys the original except in exceptional circumstances. Where anonymization is not possible (for example for technical reasons or where a product problem can only be recreated using PHI or if the Client specifies the data cannot be anonymized (e.g. if we are investigating a problem on a Client’s workstation), access to the data is restricted and the data is destroyed or returned to the Client as soon as it is no longer needed. Under no circumstances should identified data be added to the company dataset library.

CureDAO expects the professional integrity of our collaborators, clients, and partners providing PHI to us and will assume that they have obtained the data subject’s consent to use their data in this way.

Where a Business Associate Agreement or similar contract relating to PHI is in place, CureDAO staff members work under the terms of that agreement. Where no such agreement exists, the CureDAO PHI handling policy and process are followed.

CureDAO conducts periodic internal audits on compliance with this policy.
