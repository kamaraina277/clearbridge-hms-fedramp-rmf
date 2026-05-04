# Step 6: Continuous Monitoring (ConMon) Plan and Sample Monthly ConMon Report

---

**Project Title:** Continuous Monitoring Plan and Sample Monthly ConMon Report for ClearBridge HMS
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FedRAMP ConMon Guide v3.0 | NIST SP 800-137 | NIST SP 800-53 CA-7
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** August 2024
**Status:** Complete

---

## Purpose

Step 6 of the NIST Risk Management Framework is Monitoring. Once a system receives an ATO, it does not stay authorized permanently on its own. The organization must continuously monitor the system's security posture, report findings to the AO, and manage changes to the system that could affect its authorization. FedRAMP has specific continuous monitoring (ConMon) requirements that the CSP and ISSO must follow to maintain the ATO.

This document presents the ClearBridge HMS ConMon Plan, which governs how ongoing monitoring is conducted, and a sample Monthly ConMon Report for August 2024, the first full month of post-authorization monitoring.

---

## PART A: CONTINUOUS MONITORING PLAN

### Section 1: ConMon Governance

| Field | Detail |
|---|---|
| System | ClearBridge Health Management System (HMS) |
| System ID | HHS-CB-HMS-2024-MOD |
| ATO Date | July 22, 2024 |
| AO | Robert T. Hargrove, HHS CISO |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| ConMon Coordinator | Ina Grace Kamara, ISSO |
| Monthly Report Due Date | 15th of each month |
| ConMon Plan Approved | July 10, 2024 |
| ConMon Plan Review Frequency | Annually |

### Section 2: ConMon Activities and Frequencies

FedRAMP requires specific monitoring activities on defined schedules. The table below documents all required activities for ClearBridge HMS.

| Activity | Frequency | Tool / Method | Responsible Party | Deliverable |
|---|---|---|---|---|
| Operating System Vulnerability Scans | Monthly | Tenable Nessus (authenticated) | Cloud Ops: Kevin D. Ashworth | Nessus scan report |
| Web Application Vulnerability Scans | Monthly | Nessus Web App Scanning | Cloud Ops: Kevin D. Ashworth | Web app scan report |
| Database Vulnerability Scans | Monthly | Nessus Database plug-ins | Cloud Ops: Kevin D. Ashworth | Database scan report |
| SIEM Log Review | Weekly | Splunk (SIEM) | ISSO: Ina Grace Kamara | Weekly log review summary |
| POA&M Update | Monthly | POA&M tracker (Excel/FedRAMP template) | ISSO: Ina Grace Kamara | Updated POA&M |
| Hardware/Software Inventory Review | Monthly | ServiceNow CMDB + AWS Config | Cloud Ops: Kevin D. Ashworth | Updated asset inventory |
| Incident Reporting | As needed (within 1 hour) | ServiceNow Incident Module | ISSO: Ina Grace Kamara | US-CERT report |
| Significant Change Notification | As needed (within 30 days) | Change Advisory Board | ISSO + System Owner | Significant change notice |
| User Access Reviews | Quarterly | AWS IAM Access Analyzer + manual review | ISSO: Ina Grace Kamara | Access review report |
| Penetration Test | Annually | Accredited 3PAO | SecureAssess Partners, LLC | Pen test report |
| Security Assessment (full) | Annually (3-year reassessment) | Accredited 3PAO | SecureAssess Partners, LLC | Updated SAR |
| Privacy Impact Assessment Review | Annually | Privacy Officer review | Angela N. Weiss | Updated PIA |
| Contingency Plan Test | Annually | Tabletop exercise | Kevin D. Ashworth | Exercise report |
| Security Awareness Training | Annually | LMS (online training platform) | ISSO: Ina Grace Kamara | Training completion records |

### Section 3: Vulnerability Management Procedures

Vulnerabilities discovered through monthly scans are risk-rated using the CVSS v3.1 scoring system and addressed according to the following remediation SLA:

| CVSS Score | Risk Rating | Remediation Timeframe |
|---|---|---|
| 9.0 - 10.0 | Critical | 15 days |
| 7.0 - 8.9 | High | 30 days |
| 4.0 - 6.9 | Moderate | 90 days |
| 0.1 - 3.9 | Low | 180 days |

Vulnerabilities that cannot be remediated within the SLA must be entered into the POA&M with a documented justification, compensating controls, and an extended remediation timeline approved by the AO.

### Section 4: Significant Change Management

A significant change is any modification to the system that could affect the security posture documented in the SSP. Examples include: changes to the authorization boundary, deployment of new software components, changes to data types processed, changes to interconnections, and changes to encryption implementations.

When a significant change occurs:
1. The ISSO documents the change in the Change Advisory Board (CAB) system.
2. The ISSO notifies the AO within 30 days via the ConMon monthly report (or sooner for urgent changes).
3. If the change is substantial, the AO may require a partial or full re-assessment by the 3PAO.

### Section 5: POA&M Management

The POA&M is updated monthly and submitted with the ConMon report. All items are updated with current status, milestones achieved or missed, and revised target dates where applicable. Closed items must include closure evidence (e.g., scan results showing vulnerability remediated, policy document with approval date).

### Section 6: Incident Response Integration

Security incidents detected through monitoring are handled per the ClearBridge HMS Incident Response Plan (IRP v2.1). All incidents rated Moderate or higher are reported to the HHS CISO within 1 hour. US-CERT notification is submitted per NIST SP 800-61 Rev 2 timeframes. Incident details (excluding sensitive operational details) are reflected in the monthly ConMon report.

---

## PART B: SAMPLE MONTHLY CONMON REPORT (AUGUST 2024)

**Report Period:** August 1-31, 2024
**Prepared By:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Submitted To:** Robert T. Hargrove, AO, HHS CISO
**Submission Date:** September 12, 2024

---

### Executive Summary

This is the first monthly ConMon report following the ClearBridge HMS ATO granted July 22, 2024. During August 2024, all required monitoring activities were completed on schedule. Monthly vulnerability scans identified 3 new findings: 0 Critical, 1 High, 1 Moderate, and 1 Low. The High finding has been remediated and validated. Two High-risk POA&M items from the original SAR (POA-001 and POA-002) were closed with evidence. No security incidents meeting the reporting threshold were identified.

---

### Vulnerability Scan Summary

| Scan Type | Date Completed | New Findings | Critical | High | Moderate | Low |
|---|---|---|---|---|---|---|
| OS Vulnerability Scan (EC2) | August 8, 2024 | 2 | 0 | 1 | 0 | 1 |
| Web Application Scan | August 15, 2024 | 1 | 0 | 0 | 1 | 0 |
| Database Scan (RDS) | August 22, 2024 | 0 | 0 | 0 | 0 | 0 |
| **Total New Findings** | | **3** | **0** | **1** | **1** | **1** |

### New Vulnerability Details

| Vuln ID | Scan Type | CVE | Description | CVSS | Risk | Status | Target Close |
|---|---|---|---|---|---|---|---|
| VUL-2024-001 | OS Scan | CVE-2024-21338 | Windows kernel elevation of privilege on AMI baseline | 7.8 | High | Remediated August 16 | Closed |
| VUL-2024-002 | Web App Scan | CVE-2024-1234 | Outdated jQuery library version in admin portal | 5.3 | Moderate | In remediation | September 30, 2024 |
| VUL-2024-003 | OS Scan | N/A | Informational: Debug headers exposed in ALB response | 2.0 | Low | In remediation | October 31, 2024 |

---

### POA&M Status Update

| POA&M ID | Description | Prior Status | Current Status | Evidence of Closure |
|---|---|---|---|---|
| POA-001 | Configuration baseline docs incomplete | Open (High) | Closed | Updated CMDB entries, signed baseline doc dated Aug 2, 2024 |
| POA-002 | Reflected XSS in beneficiary search | Open (High) | Closed | Patch deployed Aug 5; rescan confirmed resolved Aug 8 |
| POA-003 | Q1 2024 account review undocumented | Open (Moderate) | In Progress (80%) | Draft retroactive review document in final review |
| POA-004 | Vuln scan missing 2 API endpoints | Open (Moderate) | Closed | Scan targets updated; re-scan report attached |
| POA-005 | CP tabletop exercise not conducted | Open (Moderate) | Scheduled: Sep 18 | Exercise invitation sent to all stakeholders |
| POA-006 | Treasury MOU not fully executed | Open (Moderate) | In Progress | MOU sent to Treasury OGC Aug 1; awaiting signature |
| POA-007 | SCRM policy not approved | Open (Low) | Closed | Policy approved by AO August 12, 2024 |
| POA-008 | Audit log retention not verified | Open (Moderate) | Closed | All CloudWatch log groups confirmed; screenshot attached |
| POA-009 | 3 assets missing from CMDB | Open (Moderate) | Closed | AWS Config discovery run; all assets added to ServiceNow |
| POA-010 | IR tabletop exercise not conducted | Open (Moderate) | Scheduled: Sep 18 | Combined with CP exercise |
| POA-011 | Rules of behavior not signed by 3 users | Open (Low) | Closed | All 3 signatures collected Aug 7, 2024 |
| POA-012 | Session timeout not on 2 admin screens | Open (Moderate) | Closed | Fix deployed Aug 14; QA verified |
| POA-013 | Security awareness training overdue | Open (Low) | Closed | All 5 users completed training by Aug 10 |
| POA-014 | Access agreements missing for 2 contractors | Open (Low) | Closed | Signed agreements filed Aug 7, 2024 |

**POA&M Summary:** 10 of 14 items closed. 4 items remain open. No items are past target date.

---

### Significant Changes

No significant changes to the ClearBridge HMS authorization boundary, architecture, or data types occurred during August 2024.

---

### Incident Summary

No security incidents meeting the ConMon reporting threshold (Moderate or higher) were identified during August 2024.

One low-severity event was logged: an IAM user triggered 6 failed login attempts on August 19 due to an expired session token. The account was not locked (lockout threshold is 10 attempts per NIST recommendation). The user was notified and the token was refreshed. No further action required.

---

### Next Month Actions

| Action | Owner | Due Date |
|---|---|---|
| Complete September vulnerability scans (OS, web app, database) | Kevin D. Ashworth | September 8-22, 2024 |
| Conduct combined CP/IR tabletop exercise | Kevin D. Ashworth + ISSO | September 18, 2024 |
| Close POA-003 (Q1 account review documentation) | Ina Grace Kamara | September 15, 2024 |
| Follow up on Treasury MOU execution | Ina Grace Kamara | September 15, 2024 |
| Submit September ConMon report | Ina Grace Kamara | October 15, 2024 |

---

## Interview Defense Notes

- **What is the purpose of continuous monitoring in FedRAMP?** An ATO is not a permanent security guarantee. ConMon ensures the system's security posture stays consistent with what the AO authorized. Without ongoing monitoring, you would not know if new vulnerabilities emerged or configurations drifted.
- **What are the key FedRAMP ConMon deliverables?** Monthly: vulnerability scan results, updated POA&M, and a monthly ConMon report. Annually: penetration test results, full control assessment by the 3PAO, and updated SSP if changes occurred.
- **What is a significant change and why does it matter?** A significant change is anything that could affect the system's security posture as documented in the SSP. It matters because the AO authorized the system as it was described. If the system changes meaningfully, the AO needs to re-evaluate whether the authorization still applies.
- **What happens if a new Critical vulnerability is found during a monthly scan?** It must be remediated within 15 days per FedRAMP SLAs. If it cannot be remediated in time, it must go into the POA&M with compensating controls and an AO-approved extension. Failure to act can result in ATO suspension.
- **Why is the ISSO responsible for the monthly ConMon report?** The ISSO is the primary security liaison between the CSP and the agency. The ISSO coordinates the technical teams (cloud ops, developers) and translates security data into a report the AO can act on. It is a communication and accountability role, not just a technical one.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
