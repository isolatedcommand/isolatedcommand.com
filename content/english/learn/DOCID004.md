---
title: "ABS Vulnerability Risk Management for the Financial Industry in Singapore: What have I learnt"
date: 2025-04-01T00:00:00+08:00
author: conanzhangtech
image : "https://abs.org.sg/images/default-album/abs-logo-text.png"
bg_image: "https://abs.org.sg/images/default-album/abs-logo-text.png"
description: "Lessons from the ABS Vulnerability Risk Management guidance for the Singapore financial industry."
categories: ["SERIES: What Have I Learnt"]
tags: ["Conan ZHANG"]
#tags: ["Conan ZHANG","Glendon ONG"]
draft: false
type: "post"
---


#### Why do traditional vulnerability management approaches become resource-prohibitive?

In 1.1,
> Traditionally, each vulnerability needs to be risk-assessed by human who understand severity of the affected assets and prioritised for remediation according to its risk profile.
>
> This approach demands huge number of resources to assess and address these vulnerabilities and consequently, prevents focus on the vulnerabilities that truly matter.

---

#### What are the baseline asset parameters required to establish an attack surface inventory?

In 2.2,
> a. Impact and value of the asset: Importance of the asset to the FI such as core banking systems.
>
> b. Sensitivity of data: The level of sensitivity of the data processed by and/or store in the asset in view of legal, compliance, and business impact, for example, personally identifiable information (PII).
>
> c. Location and exposure level: Whether the asset is internet-facing, intranet, or operates in an air-gapped environment. The reachability to the asset serves as a key factor for prioritisation.
>
> d. Regulatory requirements: Compliance obligations of the assets, such as those designated as Critical Information Infrastructure (CII) system.
>
> e. Uptime and availability considerations: Factors related to the asset's availability and the impact of patching on its uptime.

---

#### Under what criteria may an asset component be excluded from remediation trackers?

In 3.1,
> For vulnerability that is validated as false positive by the FI or principal vendor who provides Commercial-Off-The-Shelf product, it should be excluded from remediation.
>
> As the state of false positive vulnerability may change due to the design or implementation changes over time, it should be tracked and reviewed periodically to determine if false positive remains relevant.

---

#### How should threat intelligence be aggregated into the vulnerability evaluation process?

In 3.3,
> Threat intelligence provides important context to prioritise remediation efforts. FI should subscribe to threat intelligence feeds that provide information on widely and actively exploited vulnerabilities, as well as availability of Proof-of-Concept (POC) exploit codes.
>
> The effectiveness of the exploitation may also depend on the threat actor’s capabilities. Threat actors can be classified based on motivation and skill level, ranging from nation-state actors to script kiddies.
>
> FI should profile and assess the threat actor groups targeting its industry and their common attack tactics regularly. FI may test POC exploit codes internally to aid in the assessment.

---

#### What specific parameters dictate high-priority patching vs routine schedules?

In 3.4,
> High-priority patching is required to address vulnerabilities where there is no effective control, whereby routine patching is required for vulnerabilities that have been mitigated by layered defenses.
>
> Criticality of asset | Critical exposure vulnerability
>
> Internet facing system -> High-priority patching
>
> Critical system -> High-priority patching
>
> Other system -> Routine patching

---

#### What four risk response modes can an institution deploy against a vulnerability?

In 3.6,
> a. Accept the risk of the vulnerability by relying on existing layered defences to prevent exploitation of the vulnerability.
>
> b. Mitigate the risk by eliminating the vulnerability such as applying software patching, software upgrade, enhancing security configuration to reduce attack surface and likelihood of exploitation.
>
> c. Transfer the risk by softening the impact when the exploitation occurs such as cyber insurance and allow third party to manage the vulnerability (such as Software-As-A-Service).
>
> d. Avoid the risk through eliminating the attack surface such as removal of the vulnerable software, removal of the affected components, removal of libraries and disabling the vulnerable services.

---

#### What are the operational guardrails required for managing an emergent zero-day incident?

In 4.2,
> This procedure should include a detailed task force description, outlining the roles and responsibilities of personnel from different teams involved.
>
> It is crucial to have well-defined processes for notification, authorisation for zero-day risk mitigation or remediation plans, proposed action plans, testing, deployment, and post-deployment actions.
>
> Communication within the FI should be escalated appropriately and, on a need-to-know basis.

---

#### What technical criteria must validate an automated patch deployment payload?

In 4.3,
> It is crucial that the distribution and transportation of patches are carried out securely, with proper signature and hash value verifications.

---

#### What deployment policies define an infrastructure remediation standard?

In 4.5,
> a. Immediate Deployment Policy: FI should prioritise patching as soon as a patch becomes available. This approach is especially relevant for zero-day vulnerabilities but can also be applied to highly mature products.
>
> b. Time Based Policy: FI should adopt a patching policy that involves regular intervals, such as leveraging Microsoft's "Patch Tuesday" and initiating patching activities after the release of monthly patches.
>
> c. Patch Based Policy – Patch when predefined number of outstanding critical patches are outstanding. FI can adopt this to trigger patching where downtime is a concern and want to bundle patches within stipulated timeframes.
>
> d. Controlled Deployment Policy – When the cumulative security risk surpasses a specific level or set of metrics, a patch should be implemented.
>
> e. Hybrid Policy – Different combinations of the approaches can be implemented for various information systems within the FI.

---

#### How must an institution enforce consequence management when patching deadlines are breached?

In 4.10,
> Effective risk management should consider limit the risk exposure by limiting additional changes to the environment until the vulnerability is remediated to an acceptable threshold.
>
> An example is to prohibit introduction of new system when the vulnerabilities are not remediated in accordance with the required policy.


### Original Document: 

https://abs.org.sg/industry-guidelines/compliance-and-risk-management/cyber-security

> {{< pdfviewer
    src="https://abs.org.sg/docs/library/abs-vulnerability-risk-management-paper.pdf"
    width="100%"
    height="1000"
 >}}
 >