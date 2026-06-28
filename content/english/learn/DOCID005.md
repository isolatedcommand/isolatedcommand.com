---
title: "ABS Cloud Computing Implementation Guide 3.0 for the Financial Industry in Singapore: What have I learnt"
date: 2025-04-01T00:00:00+08:00
author: conanzhangtech
image : "https://abs.org.sg/images/default-album/abs-logo-text.png"
bg_image: "https://abs.org.sg/images/default-album/abs-logo-text.png"
description: "SERIES: What Have I Learnt"
categories: ["SERIES: What Have I Learnt"]
tags: ["Conan ZHANG"]
#tags: ["Conan ZHANG","Glendon ONG"]
draft: false
type: "post"
---




#### What is the guiding principle for cloud outsourcing arrangements?

In Section 1: Introduction (Objective), 
> The guiding principle for cloud outsourcing arrangements is that controls in the cloud must be at least as strong as those which the FIs would have implemented had the operations been performed in-house.

---

#### What are the three core actions or components that provide visibility over CSP concentration risk?

In Section 2: 1. Cloud Governance,
> • Maintain inventory of CSP exposures across various IaaS/PaaS/SaaS third party arrangements to provide a holistic view on dependency of a single CSP (including CSPs as sub-contractors of SaaS outsourcing.
>
> • Assess concentration risk at CSP level (including CSPs as sub-contractors of SaaS outsourcing). Such risk evaluation to be re-performed periodically or when proposed new cloud outsourcing relates to the same CSP.
>
> • Maintain inventory of CSP specific availability zone ("AZ") exposures for IaaS/PaaS workloads and SaaS to provide holistic business impact analysis for any potential AZ failure/ outage.

---

#### What legal and regulatory verification must an FI obtain regarding data host jurisdictions?

In Section 2: 2. Cloud Third-Party Arrangement Due Diligence (Cross-Border Data Transfers and Location of Data),
> FIs should at the outset obtain legal advice to ascertain that the CSP is operating in jurisdictions that generally uphold confidentiality clauses and agreement.
>
> An FI should enter into outsourcing arrangements only with CSPs operating in jurisdictions that generally uphold confidentiality clauses and agreements.
>
> An FI should not enter outsourcing or cloud third-party arrangements with CSP in jurisdictions where prompt access to information by the MAS or agents appointed by MAS to act on its behalf, may be impeded by legal or administrative restrictions at the CSP.

---

#### What four operational parameters outline the scope of a cloud contract exit plan?

In Section 2: 2. Cloud Third-Party Arrangement Due Diligence (Exit Plan),
> 1. Agreed procedure and tools used for deletion of data from CSP’s environment to render the data irrecoverable.
>
> 2. Costs associated with the exfiltration and return of an FI's data.
>
> 3. Removal of all FI’s data (e.g., customer data) and confirmation that all data has been rendered irrecoverable on termination of the outsourcing arrangement.
>
> 4. Transferability of outsourced services (e.g., to a third party or back to the FI) for ensuring service continuity.

---

#### How are cyber security responsibilities delineated between the CSP and the FI?

In Section 2: 2. Cloud Third-Party Arrangement Due Diligence (Shared Responsibility),
> Moving technology infrastructure into the cloud creates a shared responsibility model between the FI and the CSP for the operation and management of security controls. According to MAS’s Cloud Advisory, CSPs are responsible for “Security-of-the-Cloud”, FIs would be responsible for “Security-in-the-Cloud”.
>
> “Security-of-the-Cloud” refers to the security of the public cloud services under the CSPs’ responsibility. In an IaaS or PaaS arrangement, these would typically include the security of the underlying hardware, system software and the hypervisor. For SaaS, this would also include the underlying security of the application software.
>
> “Security-in-the-Cloud” refers to the security of the cloud workloads under the FIs’ responsibility. In an IaaS or PaaS arrangement, these should typically include securing IT systems components such as applications, operating system and orchestration tools. In a SaaS arrangement, it would generally include managing user account privileges and data access rights.

---

#### Under what operational standard must container images be frozen following validation?

In Section 3: B) Design and Secure the Cloud (2. Virtualisation, Containerisation and DevOps),
> 8. FI should consider ensuring container images are immutable post approval for production deployment.

---

#### What baseline technical validation level is mandated for cloud-based Hardware Security Modules?

In Section 3: B) Design and Secure the Cloud (5. Cryptographic Key Management),
> 5. At minimum, the cloud based HSM should meet the FIPS or Common Criteria for cryptographic products. Leverage on a FIPS 140-2 Level 2 validated HSMs at a minimum to secure their cryptographic keys, and access to the HSM should be secured with multi-factor authentication.

---

#### What operational restriction applies to the cloud infrastructure management account?

In Section 3: B) Design and Secure the Cloud (8. User Access Management and Authentication),
> 1. For each cloud deployment there will be a management account (previously known as master account). This account should only be used for emergency, and not for day-to-day operations.

---

#### What separation of duties standard applies to user access environments?

In Section 3: B) Design and Secure the Cloud (8. User Access Management and Authentication),
> 11. Where development, QA and production environments exist in the cloud, access should be strictly controlled. Developers and Testers should not have any write access to production environments. Production support should have limited read access in accordance with their responsibilities.

---

#### What monitoring requirement governs the cloud management console administrator credentials?

In Section 3: B) Design and Secure the Cloud (9. Privileged User Access Management),
> 8. As the administrator account to the CSP cloud management console cannot be locked out, FI should monitor for unauthorized access to the accounts or password guessing attempts to break into the account. FIs should consider changing the password periodically.

---

#### What structural requirement is expected when a fully managed SaaS incident must be reported under MAS Notice?

In Section 3: C) Run the Cloud (4. Incident and Problem Management),
> 11. While it is recognised that it is usually the FI's responsibility to identify a relevant incident under relevant MAS Notices related to Technology Risk Management, there are situations where systems or applications designated MAS Critical may be fully managed by the CSP, particularly SaaS or white-labelling.
>
> In these situations, a contractual requirement should be included to ensure notification to the FI as soon as possible after the detection of a relevant incident. The FI is then required to notify the MAS within 60 minutes of receiving the notification.

### Original Document: 

https://abs.org.sg/industry-guidelines/compliance-and-risk-management/cyber-security

> {{< pdfviewer
    src="https://abs.org.sg/docs/library/abs-cloud-computing-implementation-guide---july-2024.pdf"
    width="100%"
    height="1000"
 >}}
 >