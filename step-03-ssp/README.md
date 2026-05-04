# Step 3: Partial FedRAMP System Security Plan (SSP)

---

**Project Title:** Partial FedRAMP System Security Plan (SSP) for ClearBridge Health Management System
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP SSP Template v3.1 | NIST SP 800-18
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** May 2024
**Status:** Complete (Partial SSP for Portfolio Demonstration)

---

## Purpose

The System Security Plan (SSP) is the primary document in a FedRAMP authorization package. It provides a comprehensive description of the system, its environment, its boundary, and how each of the 325+ FedRAMP Moderate controls is implemented. A complete SSP for a production system would exceed several hundred pages.

This document presents a partial SSP covering the most critical sections: system characterization, boundary description, interconnections, roles and responsibilities, and control implementation narratives for 10 representative controls. This is a realistic artifact for an entry-level ISSO who contributes to SSP development under the guidance of a senior GRC team.

---

## Section 1: System Identification

| Field | Detail |
|---|---|
| System Name | ClearBridge Health Management System (HMS) |
| System Abbreviation | CB-HMS |
| System Identifier | HHS-CB-HMS-2024-MOD |
| FedRAMP Unique ID | TBD (assigned upon authorization) |
| System Owner | Dr. Carolyn M. Fletcher, HHS Deputy Director, Benefits Technology |
| System Type | Major Application |
| Service Model | Software as a Service (SaaS) |
| Deployment Model | Federal Community Cloud (AWS GovCloud US-East) |
| Operational Status | Operational |
| FedRAMP Baseline | Moderate |
| System Description | ClearBridge HMS is a cloud-hosted health benefits management platform supporting approximately 45,000 federal beneficiaries across 12 regional HHS offices. It processes PHI, PII, federal benefit eligibility records, Treasury disbursement instructions, and CMS Medicare data. |

---

## Section 2: System Owner and Authorization Information

| Role | Name | Organization | Contact |
|---|---|---|---|
| System Owner | Dr. Carolyn M. Fletcher | HHS, Benefits Technology | cfletcher@hhs.gov (fictional) |
| ISSO | Ina Grace Kamara | ClearBridge Technologies | ikamara@clearbridge.com (fictional) |
| Authorizing Official | Robert T. Hargrove | HHS CISO | rhargrove@hhs.gov (fictional) |
| CSP Representative | Brian A. Holloway | ClearBridge Technologies | bholloway@clearbridge.com (fictional) |
| SAISO | Walter J. Drummond | HHS CISO Office | wdrummond@hhs.gov (fictional) |
| 3PAO Lead | Stephanie R. Goodwin | SecureAssess Partners, LLC | sgoodwin@secureassess.com (fictional) |
| Cloud Ops Lead | Kevin D. Ashworth | ClearBridge Technologies | kashworth@clearbridge.com (fictional) |
| Privacy Officer | Angela N. Weiss | HHS, Office of the General Counsel | aweiss@hhs.gov (fictional) |

---

## Section 3: System Security Categorization

Per FIPS 199 and NIST SP 800-60 Vol. II, ClearBridge HMS is categorized as follows:

**Final Security Category:**
SC ClearBridge-HMS = {(Confidentiality, MODERATE), (Integrity, MODERATE), (Availability, LOW)}

**Overall Impact Level: MODERATE**

Rationale: The system processes PHI, PII, and federal benefit eligibility records. A breach of confidentiality could harm tens of thousands of beneficiaries. Integrity failures could result in financial harm through misdirected payments. Availability failures are recoverable within the defined RTO (4 hours) and RPO (1 hour) without catastrophic impact.

---

## Section 4: System Boundary

The ClearBridge HMS authorization boundary encompasses all ClearBridge-managed components within AWS GovCloud (US-East). Components inside the boundary:

- AWS VPC (dedicated, single-tenant): Contains all application and data components
- Amazon EC2 instances (application servers, web tier)
- Amazon RDS (PostgreSQL database cluster, multi-AZ)
- Amazon S3 (encrypted backup storage)
- AWS Application Load Balancer (public-facing HTTPS endpoint)
- AWS CloudTrail, CloudWatch, and Security Hub (logging and monitoring)
- AWS KMS (key management for encryption at rest)
- AWS Systems Manager (administrative access, no direct SSH)

Components outside the boundary (leveraged services):

- AWS infrastructure (physical data centers, hypervisor, networking): Covered by AWS FedRAMP High P-ATO
- HHS Central Identity Provider (IdP): Covered by HHS agency ATO
- CMS Medicare Data Gateway: Interconnection documented via ISA
- Treasury Disbursement API: Interconnection documented via MOU

---

## Section 5: System Interconnections

| External System | Owner | Connection Type | Data Exchanged | Agreement | Impact |
|---|---|---|---|---|---|
| HHS Central IdP | HHS CISO Office | SAML 2.0 (HTTPS) | Authentication tokens | ISA-HHS-001 | Moderate |
| CMS Medicare Data Gateway | CMS | SFTP (dedicated circuit) | Beneficiary eligibility data | ISA-CMS-001 (in progress) | Moderate |
| Treasury Disbursement API | Treasury BFS | REST API (HTTPS, mutual TLS) | Payment instructions | MOU-TREAS-001 (in progress) | Moderate |

All interconnections use encrypted channels (TLS 1.2 minimum). Data shared with CMS and Treasury is limited to the minimum necessary for benefit processing.

---

## Section 6: Applicable Laws and Regulations

| Law / Regulation | Applicability |
|---|---|
| FISMA 2014 | Federal information security program requirements |
| FedRAMP Authorization Act (2022) | Mandatory FedRAMP authorization for cloud services |
| Privacy Act of 1974 | Protection of PII held in federal systems of records |
| HIPAA Privacy Rule (45 CFR Part 164) | PHI handling requirements |
| HITECH Act | Breach notification and enhanced PHI protections |
| OMB Circular A-130 | Federal information management |
| NIST SP 800-53 Rev 5 | Security control requirements |
| NIST SP 800-37 Rev 2 | RMF application |

---

## Section 7: Control Implementation Narratives (Representative Sample)

### AC-2: Account Management

**Control Requirement:** The organization manages information system accounts, including establishing, activating, modifying, reviewing, disabling, and removing accounts.

**Implementation:** ClearBridge Technologies manages all ClearBridge HMS accounts. AWS IAM is used for infrastructure-level accounts. Application-level user accounts are provisioned through the HHS HR onboarding process. The ISSO receives a provisioning request form signed by the user's manager before creating any account. All accounts are reviewed quarterly by the ISSO and system owner. Accounts for departing employees are disabled within 4 hours of notification from HHS HR and removed within 30 days. Privileged accounts (admin roles) are reviewed monthly. Account activity is logged to AWS CloudTrail and the SIEM.

**Responsibility:** Shared (AWS manages IAM infrastructure; ClearBridge manages provisioning workflows and reviews)

---

### AU-2: Event Logging

**Control Requirement:** The organization identifies the types of events that the information system is capable of logging in support of the audit function, and coordinates the event logging function with other organizations requiring audit-related information.

**Implementation:** ClearBridge HMS logs the following event types: successful and failed login attempts, account provisioning and deprovisioning actions, privilege escalations, data access and export events, configuration changes, API calls to CMS and Treasury, and system start/stop events. AWS CloudTrail captures all API calls to AWS services. Amazon CloudWatch collects application-level logs. All logs are forwarded to the SIEM (Splunk) within 5 minutes of generation. Log integrity is protected through CloudTrail log file validation and S3 object lock on the log archive bucket.

**Responsibility:** Shared (AWS provides CloudTrail and CloudWatch infrastructure; ClearBridge configures application-level logging and SIEM integration)

---

### IA-2: Identification and Authentication (Organizational Users)

**Control Requirement:** The information system uniquely identifies and authenticates organizational users.

**Implementation:** ClearBridge HMS uses federated authentication through the HHS Central Identity Provider (IdP) via SAML 2.0. Users authenticate to the HHS IdP using their HHS Active Directory credentials plus a PIV card or software-based MFA token (Okta Verify). The HMS application validates the SAML assertion and creates a session. No local passwords are stored in ClearBridge HMS. Privileged access for ClearBridge system administrators uses IAM users with hardware MFA (YubiKey) enforced through an IAM policy condition.

**Responsibility:** Shared (HHS IdP manages credential validation; ClearBridge configures SAML integration and enforces MFA at application layer)

---

### IR-4: Incident Handling

**Control Requirement:** The organization implements an incident handling capability for security incidents.

**Implementation:** ClearBridge maintains a formal Incident Response Plan (IRP) approved by AO Robert T. Hargrove. The IRP follows the NIST SP 800-61 Rev 2 incident lifecycle: Preparation, Detection and Analysis, Containment, Eradication, Recovery, and Post-Incident Activity. The ISSO is the incident coordinator. All security incidents are reported to the HHS CISO within 1 hour of detection. US-CERT notification is submitted within the timeframes specified in NIST SP 800-61. Incident response drills are conducted semi-annually. All incidents are tracked in ServiceNow with a severity rating, timeline, actions taken, and lessons learned.

**Responsibility:** Customer (ClearBridge owns the IRP and all incident response activities; AWS provides detection signals through GuardDuty and CloudTrail)

---

### SC-7: Boundary Protection

**Control Requirement:** The information system monitors and controls communications at the external boundary and key internal boundaries.

**Implementation:** The ClearBridge HMS authorization boundary is enforced through AWS VPC architecture. The VPC contains three subnets: public (ALB only), private application (EC2 instances), and private data (RDS). Network ACLs and security groups enforce least-privilege traffic flow between subnets. The ALB is the only public-facing component and only accepts HTTPS on port 443. Direct SSH or RDP to any instance is prohibited. All administrative access uses AWS Systems Manager Session Manager, which does not require inbound ports. AWS WAF is deployed on the ALB to inspect and block common web attack patterns.

**Responsibility:** Shared (AWS provides VPC, Security Groups, and NACL infrastructure; ClearBridge configures rules and manages WAF policies)

---

## Section 8: System Environment of Operations

ClearBridge HMS operates in AWS GovCloud (US-East), a physically and logically separate AWS region designed for US government workloads that require compliance with ITAR, EAR, and other federal data handling requirements. The data center is FedRAMP High authorized and SOC 2 Type II certified. ClearBridge does not operate any on-premises components. All workloads, data, and management functions reside within the AWS GovCloud boundary. Physical access to the data center is managed entirely by AWS under its FedRAMP High package.

---

## Interview Defense Notes

- **What is an SSP and why is it the centerpiece of a FedRAMP package?** The SSP is the document that describes the system and documents how every required control is implemented. Reviewers and the AO rely on the SSP to understand the security posture of the system. Everything else in the authorization package supports or references the SSP.
- **What is the system boundary and why does it matter?** The boundary defines what is inside the authorization. Controls apply to everything inside the boundary. If a component is outside it, you need an interconnection agreement. Getting the boundary wrong means you might miss controls or overstate what you are responsible for.
- **What goes in a control implementation narrative?** A narrative explains what the control requires and how the organization actually implements it. A good narrative is specific: it names tools, processes, frequencies, and responsible parties. Vague statements like "we have a process" do not satisfy assessors.
- **What is the difference between an SSP and a POA&M?** The SSP documents how controls are implemented. The POA&M documents controls that are not yet fully implemented, with a plan and timeline to fix them. They work together: the SSP is the positive statement, the POA&M is the gap tracker.
- **Why is a "partial SSP" a legitimate portfolio artifact?** A full SSP for a Moderate system can be 300-500 pages. As a junior analyst, you would own specific sections or specific control families, not the entire document. A partial SSP demonstrating deep knowledge of key sections is more credible than a superficial treatment of all 325 controls.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
