# Step 2: Control Tailoring Log and Customer Responsibility Matrix (CRM)

---

**Project Title:** FedRAMP Moderate Control Tailoring Log and Customer Responsibility Matrix
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** NIST SP 800-53B, FedRAMP Moderate Baseline
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** May 2024
**Status:** Complete

---

## Purpose

Step 2 of the NIST Risk Management Framework requires the organization to select, tailor, and assign security controls appropriate for the system based on the security categorization established in Step 1. For ClearBridge HMS, this means working from the FedRAMP Moderate control baseline (325+ controls per NIST SP 800-53B) and documenting which controls are fully inherited from AWS, which are shared between AWS and ClearBridge, and which are the sole responsibility of ClearBridge.

The Customer Responsibility Matrix (CRM) is a required FedRAMP deliverable that maps each control to one of three responsibility categories: Inherited (fully handled by AWS), Shared (partially implemented by AWS, with ClearBridge implementing the remainder), or Customer Responsible (fully implemented by ClearBridge). This document also captures parameter values, organizational-defined parameters (ODPs), and control tailoring decisions made during this step.

---

## System Information

| Field | Detail |
|---|---|
| System Name | ClearBridge Health Management System (HMS) |
| System ID | HHS-CB-HMS-2024-MOD |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| System Owner | Dr. Carolyn M. Fletcher, HHS Deputy Director, Benefits Technology |
| FedRAMP Baseline | Moderate (NIST SP 800-53B) |
| Cloud Provider | AWS GovCloud (US-East) |
| AWS FedRAMP Package | AWS GovCloud FedRAMP High P-ATO |
| Step 2 Completion Date | April 25, 2024 |

---

## Control Responsibility Categories

| Category | Definition | Example for ClearBridge HMS |
|---|---|---|
| Inherited | AWS implements the control entirely. ClearBridge documents the inheritance. | PE-1 through PE-20 (Physical and Environmental Protection) |
| Shared | AWS implements part of the control at the infrastructure level. ClearBridge implements the application and configuration layer. | AU-2 (Event Logging): AWS provides CloudTrail; ClearBridge configures what events are logged at the application layer |
| Customer Responsible | ClearBridge must implement, operate, and provide evidence for this control entirely. | AC-1 (Access Control Policy and Procedures): ClearBridge writes and maintains its own access control policy |

---

## Representative Control Tailoring Log

The table below shows a representative sample of controls from each major family with tailoring decisions and responsibility assignments. The complete CRM spans all 325+ controls.

| Control ID | Control Name | Responsibility | Tailoring Decision | AWS Package Ref |
|---|---|---|---|---|
| AC-1 | Access Control Policy and Procedures | Customer | ClearBridge maintains policy reviewed annually | N/A |
| AC-2 | Account Management | Shared | AWS provides IAM infrastructure; ClearBridge owns provisioning, review, and termination workflows | AWS CRM AC-2 |
| AC-3 | Access Enforcement | Shared | AWS enforces at infrastructure level; ClearBridge configures IAM roles and application-level RBAC | AWS CRM AC-3 |
| AC-17 | Remote Access | Customer | ClearBridge policy prohibits direct remote access; all admin access via Systems Manager Session Manager | N/A |
| AU-2 | Event Logging | Shared | AWS provides CloudTrail and CloudWatch; ClearBridge defines application-level log events and retention | AWS CRM AU-2 |
| AU-3 | Content of Audit Records | Shared | AWS logs include timestamp, IP, and user ID; ClearBridge adds application transaction ID | AWS CRM AU-3 |
| AU-6 | Audit Record Review, Analysis, and Reporting | Customer | ClearBridge ISSO reviews SIEM alerts weekly; monthly report to AO | N/A |
| CA-2 | Control Assessments | Customer | Scheduled with 3PAO SecureAssess Partners, LLC | N/A |
| CA-7 | Continuous Monitoring | Customer | ClearBridge ConMon plan developed post-RAR (RAR-001 remediation) | N/A |
| CM-2 | Baseline Configuration | Shared | AWS provides AMI hardening; ClearBridge applies CIS Benchmarks at OS and application layer | AWS CRM CM-2 |
| CM-6 | Configuration Settings | Shared | AWS provides infrastructure defaults; ClearBridge applies and tracks application configuration | AWS CRM CM-6 |
| CP-4 | Contingency Plan Testing | Customer | ClearBridge conducts annual tabletop exercise | N/A |
| CP-9 | System Backup | Shared | AWS manages RDS automated backups; ClearBridge tests restores quarterly | AWS CRM CP-9 |
| IA-2 | Identification and Authentication (Organizational Users) | Shared | HHS Central IdP provides SAML federation; ClearBridge enforces MFA at application layer | AWS CRM IA-2 |
| IA-5 | Authenticator Management | Shared | HHS IdP manages credentials; ClearBridge enforces password complexity and rotation policies | N/A |
| IR-4 | Incident Handling | Customer | ClearBridge maintains Incident Response Plan; drills conducted semi-annually | N/A |
| IR-6 | Incident Reporting | Customer | ClearBridge reports incidents to HHS CISO within 1 hour of detection | N/A |
| MA-4 | Nonlocal Maintenance | Customer | All remote maintenance via AWS Systems Manager; no direct SSH permitted | N/A |
| MP-2 | Media Access | Inherited | No removable media in AWS GovCloud; inherited fully | AWS CRM MP-2 |
| PE-2 | Physical Access Authorizations | Inherited | AWS GovCloud physical access controls; fully inherited | AWS CRM PE-2 |
| PL-2 | System Security Plan | Customer | ClearBridge ISSO responsible for SSP development and maintenance | N/A |
| PS-3 | Personnel Screening | Customer | Background checks completed by ClearBridge HR for all staff with system access | N/A |
| RA-3 | Risk Assessment | Customer | ISSO conducts annual risk assessment; results documented in risk register | N/A |
| RA-5 | Vulnerability Monitoring and Scanning | Shared | AWS Inspector provides EC2 scanning; ClearBridge runs Nessus for application layer | AWS CRM RA-5 |
| SA-9 | External System Services | Customer | ClearBridge documents all external connections (HHS IdP, CMS, Treasury) with ISA/MOU | N/A |
| SC-5 | Denial of Service Protection | Inherited | AWS Shield Standard protects against volumetric DDoS; inherited from AWS | AWS CRM SC-5 |
| SC-7 | Boundary Protection | Shared | AWS VPC provides network boundary; ClearBridge configures security groups and NACLs | AWS CRM SC-7 |
| SC-8 | Transmission Confidentiality and Integrity | Shared | AWS manages TLS termination at ALB; ClearBridge enforces TLS 1.2+ and certificate management | AWS CRM SC-8 |
| SC-28 | Protection of Information at Rest | Shared | AWS KMS encrypts RDS and S3; ClearBridge manages key policy and rotation | AWS CRM SC-28 |
| SI-2 | Flaw Remediation | Customer | ClearBridge patches critical findings within 30 days, high within 60 days | N/A |
| SI-3 | Malicious Code Protection | Shared | AWS GuardDuty provides threat detection; ClearBridge deploys host-based endpoint protection | AWS CRM SI-3 |

---

## Control Count Summary

| Responsibility Category | Control Count (Approximate) |
|---|---|
| Inherited from AWS | 52 controls |
| Shared (AWS + ClearBridge) | 138 controls |
| Customer Responsible (ClearBridge only) | 135 controls |
| Total FedRAMP Moderate Controls | 325+ controls |

---

## Organizational-Defined Parameters (ODPs)

Several NIST SP 800-53 controls include parameters that organizations must define. Key ODP assignments for ClearBridge HMS:

| Control | Parameter | ClearBridge Value |
|---|---|---|
| AC-2(j) | Account review frequency | Quarterly |
| AU-11 | Audit log retention period | 3 years |
| CA-7 | Continuous monitoring frequency | Monthly (vulnerability scans), weekly (log review) |
| CP-2 | Contingency plan review frequency | Annually |
| IA-5(1)(a) | Minimum password length | 15 characters |
| IA-5(1)(d) | Password change frequency | 90 days |
| IR-6 | Incident reporting time to AO | 1 hour |
| RA-3 | Risk assessment frequency | Annually |
| RA-5 | Vulnerability scanning frequency | Weekly (infrastructure), monthly (application) |
| SC-10 | Network disconnect timeout | 30 minutes |
| SI-2 | Patch remediation timeframes | Critical: 30 days, High: 60 days, Medium: 90 days |

---

## Interview Defense Notes

- **What is the purpose of Step 2 in the NIST RMF?** Step 2 is where you select the security controls for your system based on the security category determined in Step 1. You start with the appropriate baseline (Low, Moderate, or High) and then tailor it by adding, removing, or adjusting controls based on your specific environment and risk.
- **What is a Customer Responsibility Matrix (CRM)?** A CRM is a FedRAMP document that maps each control in the baseline to who is responsible for implementing it: the cloud provider (inherited), both the provider and the customer (shared), or the customer alone. It prevents gaps where both sides assume the other is handling something.
- **Why does ClearBridge have so many shared controls?** Because ClearBridge runs on AWS GovCloud, which has its own FedRAMP authorization. AWS handles physical, infrastructure, and some platform-layer controls. ClearBridge handles the application layer, configuration choices, and operational procedures. The split reflects that reality.
- **What are organizational-defined parameters (ODPs)?** ODPs are the blanks in NIST controls that each organization fills in based on its risk tolerance and operational needs. For example, NIST says you should review accounts periodically. The ODP is the specific frequency. ClearBridge set that to quarterly for AC-2.
- **How does control tailoring differ from selecting a baseline?** The baseline is the starting set of controls for your impact level. Tailoring means you adjust that set: you might add controls for system-specific risks, apply scoping guidance to remove controls that are not applicable, or parameterize controls with organization-specific values. The result is a tailored control set that fits ClearBridge HMS specifically.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
