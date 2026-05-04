# Step 0: FedRAMP Readiness Assessment Report (RAR)

---

**Project Title:** FedRAMP Readiness Assessment Report (RAR) for ClearBridge Health Management System
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP RAR Template v2.4
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** May 2024
**Status:** Complete

---

## Purpose

A FedRAMP Readiness Assessment Report (RAR) is produced during Step 0 of the NIST Risk Management Framework before any formal authorization work begins. Its purpose is to determine whether a cloud service provider is technically and operationally ready to pursue a FedRAMP authorization. The RAR is not a formal authorization document. It is an internal checkpoint that tells the agency and the CSP whether they have the foundational controls, documentation, and processes in place to survive a full 3PAO assessment.

For ClearBridge HMS, the RAR was initiated in February 2024 as a prerequisite to beginning the formal FedRAMP Moderate authorization package. SecureAssess Partners, LLC served as the 3PAO team conducting readiness interviews and technical reviews. The findings in this RAR informed the remediation roadmap that the ClearBridge team worked through between February and April 2024 before commencing formal SSP development.

---

## System Information

| Field | Detail |
|---|---|
| System Name | ClearBridge Health Management System (HMS) |
| System Identifier | HHS-CB-HMS-2024-MOD |
| Cloud Service Model | Software as a Service (SaaS) |
| Cloud Deployment Model | Federal Community Cloud |
| Cloud Provider | AWS GovCloud (US-East) |
| Sponsoring Agency | Department of Health and Human Services (HHS) |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| System Owner | Dr. Carolyn M. Fletcher, HHS Deputy Director, Benefits Technology |
| AO | Robert T. Hargrove, HHS CISO |
| 3PAO | Stephanie R. Goodwin, SecureAssess Partners, LLC |
| Assessment Date | February 12-23, 2024 |
| RAR Completion Date | March 8, 2024 |

---

## Readiness Criteria Assessment

| # | Capability | Assessment Result | Notes |
|---|---|---|---|
| 1 | System documentation (architecture diagrams, data flows) | Ready | AWS architecture diagrams current as of Jan 2024 |
| 2 | Boundary definition and data flow diagrams | Ready | Logical and physical boundaries clearly defined |
| 3 | Security authorization policies and procedures | Conditionally Ready | SSP narrative not yet initiated; policies drafted |
| 4 | Personnel security controls (PS family) | Ready | Background checks complete for all ClearBridge staff |
| 5 | Physical and environmental protection (PE family) | Ready | Inherited from AWS GovCloud FedRAMP High package |
| 6 | Incident response plan and procedures | Conditionally Ready | Plan exists but not formally tested in 12 months |
| 7 | Configuration management policy and baseline | Ready | CIS Benchmarks applied; CMDB maintained in ServiceNow |
| 8 | Vulnerability scanning (OS, web app, database) | Ready | Nessus scans run weekly; reports reviewed monthly |
| 9 | Patch management and remediation tracking | Conditionally Ready | High and critical patches remediated within SLA; medium backlog exists |
| 10 | Identity and access management (AC, IA families) | Ready | MFA enforced; AWS IAM roles in use; quarterly access reviews |
| 11 | Audit and accountability (AU family) | Ready | CloudTrail, CloudWatch, and SIEM logging active |
| 12 | Contingency planning (CP family) | Conditionally Ready | BCP documented; tabletop exercise not completed |
| 13 | Media protection (MP family) | Ready | All data encrypted at rest (AES-256); no removable media in use |
| 14 | Risk assessment (RA family) | Conditionally Ready | Informal risk register exists; formal NIST-aligned RA not complete |
| 15 | System and communications protection (SC family) | Ready | TLS 1.2+ enforced; VPC segmentation in place |
| 16 | Supply chain risk management | Conditionally Ready | Vendor inventory exists; formal SCRM policy not yet approved |
| 17 | Separation of duties | Ready | Admin, developer, and read-only roles separated in IAM |
| 18 | Least privilege enforcement | Ready | Roles scoped by function; no shared administrative credentials |
| 19 | Continuous monitoring plan | Not Ready | No formal ConMon plan in place at time of assessment |
| 20 | POA&M process and tracking | Conditionally Ready | Findings tracked in spreadsheet; no formalized process |
| 21 | Privacy controls and PIA | Conditionally Ready | PIA drafted; not yet reviewed by HHS Privacy Officer |
| 22 | Change management process | Ready | Change Advisory Board meets bi-weekly; records maintained |
| 23 | Third-party service provider management | Conditionally Ready | AWS and Microsoft 365 dependencies identified; ISA/MOU not complete |
| 24 | Penetration testing readiness | Conditionally Ready | No penetration test conducted; vulnerability scans active |

**Summary:** Ready: 11 | Conditionally Ready: 12 | Not Ready: 1 (ConMon Plan)

**Overall RAR Determination: Conditionally Ready to Proceed**

---

## Open Findings and Remediation Plan

| Finding ID | Capability | Description | Priority | Remediation Owner | Target Completion |
|---|---|---|---|---|---|
| RAR-001 | Continuous Monitoring | No formal ConMon plan exists | High | Ina Grace Kamara, ISSO | April 15, 2024 |
| RAR-002 | Incident Response | IR plan not exercised in 12+ months | High | Kevin D. Ashworth, Cloud Ops | March 31, 2024 |
| RAR-003 | Contingency Planning | BCP tabletop exercise not conducted | Medium | Kevin D. Ashworth, Cloud Ops | April 30, 2024 |
| RAR-004 | Risk Assessment | Formal NIST-aligned RA not complete | High | Ina Grace Kamara, ISSO | April 15, 2024 |
| RAR-005 | POA&M Process | No formalized POA&M tracking process | Medium | Ina Grace Kamara, ISSO | April 30, 2024 |
| RAR-006 | Privacy (PIA) | PIA not reviewed by HHS Privacy Officer | Medium | Angela N. Weiss, Privacy Officer | April 30, 2024 |
| RAR-007 | SCRM Policy | Formal supply chain risk management policy not approved | Low | Brian A. Holloway, CSP Rep | May 15, 2024 |
| RAR-008 | Third-Party ISA/MOU | ISA with CMS and MOU with Treasury not formalized | Medium | Ina Grace Kamara, ISSO | May 15, 2024 |

---

## Inherited Controls from AWS GovCloud

| Control Family | Example Controls Inherited from AWS | Inheritance Type |
|---|---|---|
| Physical and Environmental (PE) | PE-1 through PE-20 | Full Inheritance |
| Media Protection (MP) | MP-2, MP-4, MP-5, MP-6 | Full Inheritance |
| System and Communications (SC) | SC-8 (transmission protection), SC-28 (protection at rest) | Partial Inheritance |
| Identification and Authentication (IA) | IA-3 (device identification) | Partial Inheritance |
| Audit and Accountability (AU) | AU-2 through AU-12 (CloudTrail logs) | Partial Inheritance |
| Contingency Planning (CP) | CP-6 (alternate storage), CP-7 (alternate processing) | Full Inheritance |

---

## System Interconnections Identified

| External System | Connection Type | Data Exchanged | Agreement Status |
|---|---|---|---|
| HHS Central Identity Provider (IdP) | SAML 2.0 federation | User authentication tokens | Active |
| CMS Medicare Data Gateway | SFTP (dedicated circuit) | Beneficiary eligibility data | ISA in progress (RAR-008) |
| Treasury Disbursement API | REST API (HTTPS) | Benefit payment instructions | MOU in progress (RAR-008) |

---

## Interview Defense Notes

- **What is the purpose of a FedRAMP RAR?** The RAR is a pre-authorization readiness check that tells the agency and CSP whether the system has foundational controls and documentation in place to undergo a full 3PAO assessment. It is not a formal authorization document.
- **Who conducts the RAR?** A 3PAO conducts it. For ClearBridge HMS, Stephanie R. Goodwin from SecureAssess Partners, LLC led the review. The ISSO (me) supports by gathering documentation and coordinating interviews.
- **What does Conditionally Ready mean?** It means gaps exist that must be remediated before or during the authorization process. The system is not rejected; a remediation plan is required.
- **What was the most critical finding in this RAR?** The absence of a formal Continuous Monitoring plan (RAR-001) was the only Not Ready finding. ConMon is a core FedRAMP requirement and must be in place before authorization is granted.
- **What is the difference between inherited controls and system-specific controls?** Inherited controls are implemented and owned by the cloud provider (AWS). ClearBridge must document the inheritance and verify it applies to their specific configuration. System-specific controls are ones ClearBridge must implement and evidence independently.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
