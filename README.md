# ClearBridge HMS: FedRAMP Moderate ATO Portfolio
### NIST Risk Management Framework (RMF) Steps 0 through 6

![Framework](https://img.shields.io/badge/Framework-FedRAMP%20Moderate-blue)
![Standard](https://img.shields.io/badge/Standard-NIST%20SP%20800--53B-darkblue)
![System](https://img.shields.io/badge/System-ClearBridge%20HMS-green)
![Status](https://img.shields.io/badge/Status-Portfolio%20Complete-brightgreen)
![Cert](https://img.shields.io/badge/Cert-CompTIA%20Security%2B%20(In%20Progress)-orange)

---

## About This Repository

This repository contains a complete, simulated FedRAMP Moderate authorization package for the **ClearBridge Health Management System (HMS)**, a fictional cloud-hosted federal health benefits platform operated by a fictional HHS sub-agency. The work presented here documents all seven steps of the NIST Risk Management Framework (RMF) from initial readiness assessment through ongoing continuous monitoring.

Every document in this portfolio was produced at the entry level, reflecting the kind of work a Junior GRC Analyst would own, contribute to, or support during an actual FedRAMP engagement. The system details are consistent and realistic throughout.

---

## System Overview

| Field | Detail |
|---|---|
| System Name | ClearBridge Health Management System (HMS) |
| System ID | HHS-CB-HMS-2024-MOD |
| System Owner | Dr. Carolyn M. Fletcher, HHS Deputy Director, Benefits Technology |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| Authorizing Official | Robert T. Hargrove, HHS CISO |
| Cloud Platform | AWS GovCloud (US-East) |
| FedRAMP Baseline | Moderate (325+ controls, NIST SP 800-53B) |
| FIPS 199 Categorization | MODERATE: SC = {(C, Mod), (I, Mod), (A, Low)} |
| Auth Path | Agency ATO, HHS Office of the CISO |
| CSP Representative | Brian A. Holloway, VP Engineering, ClearBridge Technologies |
| 3PAO Lead | Stephanie R. Goodwin, SecureAssess Partners, LLC |
| SAISO | Walter J. Drummond, HHS Sr. Agency Information Security Officer |
| Cloud Ops Lead | Kevin D. Ashworth, ClearBridge Technologies |
| Privacy Officer | Angela N. Weiss, HHS Office of the General Counsel |
| User Base | ~45,000 federal beneficiaries, 300 agency staff, 12 regional offices |
| Data Types | PHI, PII, federal benefit eligibility records, audit logs |

---

## Repository Structure

```
clearbridge-hms-fedramp-rmf/
|
|-- step-00-readiness/
|   |-- README.md   (FedRAMP Readiness Assessment Report)
|
|-- step-01-categorization/
|   |-- README.md   (FIPS 199 Security Categorization Workbook)
|
|-- step-02-controls/
|   |-- README.md   (Control Tailoring Log and Customer Responsibility Matrix)
|
|-- step-03-ssp/
|   |-- README.md   (Partial FedRAMP System Security Plan)
|
|-- step-04-assessment/
|   |-- README.md   (Security Assessment Plan and Security Assessment Report)
|
|-- step-05-authorization/
|   |-- README.md   (Authorization Package Index, POA&M Tracker, ATO Decision Memo)
|
|-- step-06-conmon/
|   |-- README.md   (Continuous Monitoring Plan and Sample Monthly ConMon Report)
|
|-- README.md       (This file)
```

---

## Project Deliverables

| Step | Project File | Framework Reference | Status |
|---|---|---|---|
| Step 0 | FedRAMP Readiness Assessment Report (RAR) | FedRAMP RAR Template v2.4 | Complete |
| Step 1 | FIPS 199 Security Categorization Workbook | FIPS 199, NIST SP 800-60 Vol. II | Complete |
| Step 2 | Control Tailoring Log and Customer Responsibility Matrix | NIST SP 800-53B, FedRAMP Mod Baseline | Complete |
| Step 3 | Partial FedRAMP System Security Plan (SSP) | FedRAMP SSP Template v3.1 | Complete |
| Step 4 | Security Assessment Plan (SAP) and Security Assessment Report (SAR) | FedRAMP SAP/SAR Templates | Complete |
| Step 5 | Authorization Package Index, POA&M Tracker, ATO Decision Memo | FedRAMP Authorization Playbook | Complete |
| Step 6 | Continuous Monitoring Plan and Sample Monthly ConMon Report | FedRAMP ConMon Guide v3.0 | Complete |

---

## Framework Coverage

| Requirement Area | Standard / Guidance | Coverage in This Repo |
|---|---|---|
| Risk Management Framework | NIST SP 800-37 Rev 2 | Steps 0 through 6 documented |
| Security Control Baseline | NIST SP 800-53 Rev 5, SP 800-53B | Moderate baseline, 325+ controls |
| Security Categorization | FIPS 199, NIST SP 800-60 Vol. II | FIPS 199 workbook with rationale |
| Privacy Overlay | NIST SP 800-53B Privacy Controls | Privacy controls addressed in SSP |
| FedRAMP Authorization | FedRAMP Authorization Playbook | Full package from RAR to ATO |
| Continuous Monitoring | FedRAMP ConMon Guide v3.0 | ConMon plan and sample report |
| Vulnerability Management | NIST SP 800-40 Rev 4 | Addressed in ConMon plan |
| Plan of Action and Milestones | OMB Memo M-02-01, FedRAMP POA&M Template | POA&M tracker in Step 5 |

---

## Laws, Regulations, and Standards

| Instrument | Relevance |
|---|---|
| Federal Information Security Modernization Act (FISMA) 2014 | Statutory basis for federal information security programs |
| FedRAMP Authorization Act (2022) | Mandates FedRAMP use for cloud services across federal agencies |
| FIPS 199 | Security categorization of federal information and information systems |
| FIPS 200 | Minimum security requirements for federal information and systems |
| NIST SP 800-37 Rev 2 | Risk Management Framework for Information Systems and Organizations |
| NIST SP 800-53 Rev 5 | Security and Privacy Controls for Information Systems and Organizations |
| NIST SP 800-53B | Control baselines (Low, Moderate, High) |
| NIST SP 800-60 Vol. II | Guide for mapping types of information to security categories |
| NIST SP 800-30 Rev 1 | Guide for conducting risk assessments |
| OMB Circular A-130 | Managing federal information as a strategic resource |
| HIPAA Privacy and Security Rules (45 CFR Parts 160 and 164) | PHI protection requirements applicable to federal health data |

---

## Key Personnel

| Role | Name | Organization |
|---|---|---|
| ISSO | Ina Grace Kamara | ClearBridge Technologies |
| Authorizing Official (AO) | Robert T. Hargrove | HHS CISO |
| System Owner | Dr. Carolyn M. Fletcher | HHS, Benefits Technology |
| CSP Representative | Brian A. Holloway | ClearBridge Technologies |
| 3PAO Lead | Stephanie R. Goodwin | SecureAssess Partners, LLC |
| SAISO | Walter J. Drummond | HHS Sr. Agency Information Security Officer |
| Cloud Ops Lead | Kevin D. Ashworth | ClearBridge Technologies |
| Privacy Officer | Angela N. Weiss | HHS Office of the General Counsel |

---

## Competencies Demonstrated

This repository demonstrates the following entry-level GRC competencies:

- **FedRAMP Process Knowledge:** Understanding of the full ATO lifecycle from readiness through authorization and ongoing monitoring
- **NIST RMF Application:** Practical application of all seven RMF steps for a real-world cloud system scenario
- **Security Categorization:** Applying FIPS 199 and SP 800-60 methodology to classify information types and system impact levels
- **Control Selection and Tailoring:** Identifying applicable controls from the Moderate baseline and documenting customer vs. CSP responsibilities
- **SSP Documentation:** Structuring a System Security Plan with system boundary, architecture, and control implementation narratives
- **Assessment Planning:** Writing a Security Assessment Plan with objectives, scope, and test methods
- **POA&M Management:** Tracking open findings with milestones, resource owners, and risk ratings
- **Continuous Monitoring:** Developing a ConMon plan with scanning cadence, reporting requirements, and escalation procedures

---

## Related Repositories

| Repository | Description |
|---|---|
| [clearbridge-hms-iso27001](https://github.com/kamaraina277/clearbridge-hms-iso27001) | ISO 27001:2022 and ISO 27005 compliance program for ClearBridge HMS |
| [clearbridge-hms-security-plus](https://github.com/kamaraina277/clearbridge-hms-security-plus) | CompTIA Security+ SY0-701 domain projects mapped to ClearBridge HMS |

---

## Portfolio Overview

| Repository | Framework | Projects | Status |
|---|---|---|---|
| clearbridge-hms-fedramp-rmf | FedRAMP Moderate / NIST RMF | 7 | Complete |
| clearbridge-hms-iso27001 | ISO 27001:2022 / ISO 27005 | 6 | Complete |
| clearbridge-hms-security-plus | CompTIA Security+ SY0-701 | 6 | Complete |

---

## About the Author

**Ina Grace Kamara**
Junior GRC Analyst, Quarantyne Technologies | Cybersecurity Analyst | GRC and Compliance
CompTIA Security+ SY0-701 (In Progress) | NIST RMF Foundational Training
Maryland

This portfolio was built to demonstrate practical federal GRC skills and is intended to support entry-level positions in cybersecurity compliance, FedRAMP program management, and information security governance.

[GitHub Portfolio](https://github.com/kamaraina277)
