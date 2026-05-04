# Step 5: Authorization Package Index, POA&M Tracker, and ATO Decision Memo

---

**Project Title:** Authorization Package Index, Plan of Action and Milestones (POA&M), and ATO Decision Memo
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP Authorization Playbook | OMB Memo M-02-01
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** July 2024
**Status:** Complete

---

## Purpose

Step 5 of the NIST Risk Management Framework is the authorization step. The system owner and ISSO compile the complete authorization package, address outstanding findings, and submit the package to the Authorizing Official (AO) for a risk-based authorization decision. For FedRAMP, this step produces three key deliverables: the Authorization Package Index (a manifest of all documents in the package), the Plan of Action and Milestones (POA&M) (a tracker for all open security findings), and the ATO Decision Memo (the formal authorization document signed by the AO).

---

## PART A: AUTHORIZATION PACKAGE INDEX

| Field | Detail |
|---|---|
| System | ClearBridge Health Management System (HMS) |
| System ID | HHS-CB-HMS-2024-MOD |
| Authorization Type | Agency ATO |
| Sponsoring Agency | Department of Health and Human Services (HHS) |
| AO | Robert T. Hargrove, HHS CISO |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| Package Submission Date | July 15, 2024 |
| Package Version | 1.0 |

### Document Index

| # | Document | Owner | Version | Date | Status |
|---|---|---|---|---|---|
| 1 | FedRAMP Readiness Assessment Report (RAR) | SecureAssess Partners, LLC | 1.0 | March 8, 2024 | Final |
| 2 | FIPS 199 Security Categorization Workbook | Ina Grace Kamara, ISSO | 1.0 | April 10, 2024 | AO Approved |
| 3 | e-Authentication Risk Assessment | Ina Grace Kamara, ISSO | 1.0 | April 15, 2024 | Final |
| 4 | Privacy Impact Assessment (PIA) | Angela N. Weiss, Privacy Officer | 1.0 | May 1, 2024 | Final |
| 5 | System Security Plan (SSP) | Ina Grace Kamara, ISSO | 1.2 | June 30, 2024 | Final |
| 6 | SSP Attachments (Architecture Diagrams, Data Flow Diagrams) | Kevin D. Ashworth, Cloud Ops | 1.0 | June 15, 2024 | Final |
| 7 | Customer Responsibility Matrix (CRM) | Ina Grace Kamara, ISSO | 1.0 | April 25, 2024 | Final |
| 8 | AWS GovCloud Inheritance Package | AWS / ClearBridge | Reference | 2024 | Active |
| 9 | Security Assessment Plan (SAP) | SecureAssess Partners, LLC | 1.0 | June 3, 2024 | Final |
| 10 | Security Assessment Report (SAR) | SecureAssess Partners, LLC | 1.0 | June 28, 2024 | Final |
| 11 | SAR Appendix: Penetration Test Report | SecureAssess Partners, LLC | 1.0 | June 28, 2024 | Final |
| 12 | Plan of Action and Milestones (POA&M) | Ina Grace Kamara, ISSO | 1.0 | July 15, 2024 | Open (14 items) |
| 13 | Continuous Monitoring Plan | Ina Grace Kamara, ISSO | 1.0 | July 10, 2024 | Final |
| 14 | Incident Response Plan | Kevin D. Ashworth, Cloud Ops | 2.1 | May 15, 2024 | Final |
| 15 | Interconnection Security Agreements (ISA) | Ina Grace Kamara, ISSO | 1.0 | June 30, 2024 | Executed |
| 16 | Memoranda of Understanding (MOU) | Ina Grace Kamara, ISSO | 1.0 | June 30, 2024 | Executed |
| 17 | ATO Decision Memo | Robert T. Hargrove, AO | 1.0 | July 22, 2024 | Signed |

---

## PART B: PLAN OF ACTION AND MILESTONES (POA&M)

The POA&M documents all security findings not fully remediated before package submission. The AO reviews the POA&M to determine whether residual risk is acceptable.

| Metric | Value |
|---|---|
| Total POA&M Items | 15 |
| High Risk Items | 2 |
| Moderate Risk Items | 8 |
| Low Risk Items | 5 |
| Items Closed Before ATO | 1 (SAR-001: patched June 27, 2024) |
| Items Open at ATO | 14 |

### POA&M Tracker

| POA&M ID | Control | Description | Risk | Target Close | Status |
|---|---|---|---|---|---|
| POA-001 | CM-2 | Configuration baseline documentation missing for 4 EC2 instance types; ServiceNow CMDB not updated | High | July 31, 2024 | Open |
| POA-002 | SI-10 | Reflected XSS in beneficiary search input; output encoding not implemented | High | July 31, 2024 | Open |
| POA-003 | AC-2 | Quarterly account review for Q1 2024 not formally documented | Moderate | August 15, 2024 | Open |
| POA-004 | RA-5 | Application vuln scan did not cover 2 microservice API endpoints | Moderate | July 31, 2024 | Open |
| POA-005 | CP-4 | Contingency plan tabletop exercise not conducted in current period | Moderate | August 30, 2024 | Open |
| POA-006 | SA-9 | MOU with Treasury Disbursement API not fully executed | Moderate | August 30, 2024 | Open |
| POA-007 | SA-12 | SCRM policy not formally approved by AO | Low | August 15, 2024 | Open |
| POA-008 | AU-11 | Audit log retention not verified for all CloudWatch log groups | Moderate | August 1, 2024 | Open |
| POA-009 | CM-8 | 3 assets missing from ServiceNow CMDB inventory | Moderate | July 31, 2024 | Open |
| POA-010 | IR-3 | IR tabletop exercise not conducted in past 12 months | Moderate | August 30, 2024 | Open |
| POA-011 | PL-4 | Rules of behavior not signed by 3 remaining remote users | Low | July 31, 2024 | Open |
| POA-012 | SC-10 | Session timeout not enforced on 2 internal admin screens | Moderate | July 31, 2024 | Open |
| POA-013 | AT-2 | Security awareness training overdue for 5 users | Low | July 31, 2024 | Open |
| POA-014 | PS-6 | Signed access agreements missing for 2 contractors | Low | July 31, 2024 | Open |

---

## PART C: ATO DECISION MEMO

**AUTHORIZATION TO OPERATE**
**ClearBridge Health Management System (HMS)**
**HHS-CB-HMS-2024-MOD**

**Date:** July 22, 2024
**To:** Dr. Carolyn M. Fletcher, System Owner, HHS Benefits Technology
**From:** Robert T. Hargrove, Authorizing Official, HHS CISO
**Re:** Authorization to Operate Decision for ClearBridge Health Management System

### Authorization Decision

I have reviewed the FedRAMP Moderate authorization package for the ClearBridge Health Management System (HMS), system identifier HHS-CB-HMS-2024-MOD, submitted on July 15, 2024. The package was prepared by ISSO Ina Grace Kamara of ClearBridge Technologies and assessed by SecureAssess Partners, LLC (3PAO lead: Stephanie R. Goodwin).

Based on my review of the System Security Plan, Security Assessment Report, and Plan of Action and Milestones, I hereby grant an **Authorization to Operate (ATO)** for the ClearBridge Health Management System at the FedRAMP Moderate baseline.

### Risk Acceptance Statement

The authorization package documents 14 open POA&M items. Two items are rated High risk (POA-001, POA-002). I have reviewed these items and determined that the mitigating controls in place reduce residual risk to an acceptable level. Remediation timelines are acceptable. All High-risk items must be closed by July 31, 2024, and all remaining items by August 30, 2024.

This ATO is granted on the condition that ClearBridge Technologies maintains the system security posture and complies with all FedRAMP continuous monitoring requirements.

### Authorization Conditions

1. Monthly ConMon deliverables must be submitted to HHS CISO no later than the 15th of each following month.
2. All High-risk POA&M items must be closed within 30 days of authorization.
3. Significant changes to system boundary, architecture, or data types must be reported within 30 days.
4. The pending Treasury MOU (POA-006) must be completed within 60 days.
5. Annual security assessments must be conducted by an accredited 3PAO.

### Authorization Period

This ATO is effective July 22, 2024. It remains valid unless the system undergoes a significant change, falls out of continuous monitoring compliance, or the HHS CISO determines that the risk posture has materially changed.

**Signed:** Robert T. Hargrove, HHS Chief Information Security Officer, July 22, 2024

---

## Interview Defense Notes

- **What is a POA&M and why does the AO care about it?** A POA&M is a formal tracker of security weaknesses that have not been fully fixed. The AO uses it to understand what risks remain and decide if those risks are acceptable. A well-maintained POA&M with clear milestones and owners shows maturity.
- **Can a system get an ATO with open High findings?** Yes, but it requires explicit risk acceptance by the AO. The AO must document why the residual risk is acceptable given mitigating controls. Open Critical findings are generally not accepted.
- **What is an Authorization Package Index?** It is a manifest listing every document submitted to the AO as part of the authorization package, with version numbers and dates. It lets the AO confirm the package is complete.
- **What happens if ClearBridge misses a POA&M milestone?** It must be reported to the AO immediately. Depending on severity, the AO may extend the deadline, require an interim mitigating action, or in extreme cases suspend or revoke the ATO.
- **What is the difference between an ATO and a FedRAMP P-ATO?** An ATO is an Agency Authorization to Operate granted by the sponsoring agency's AO. A P-ATO (Provisional ATO) is granted by the FedRAMP Joint Authorization Board (JAB) and can be leveraged by any federal agency. ClearBridge HMS uses the Agency ATO path through HHS.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
