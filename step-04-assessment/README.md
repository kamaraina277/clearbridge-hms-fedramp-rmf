# Step 4: Security Assessment Plan (SAP) and Security Assessment Report (SAR)

---

**Project Title:** Security Assessment Plan and Security Assessment Report for ClearBridge Health Management System
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP SAP Template v3.0 | FedRAMP SAR Template v3.0
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**3PAO:** Stephanie R. Goodwin, SecureAssess Partners, LLC
**Date:** May 2024
**Status:** Complete

---

## Purpose

Step 4 of the NIST Risk Management Framework requires an independent assessment of the security controls documented in the SSP. For FedRAMP, this assessment must be conducted by an accredited Third Party Assessment Organization (3PAO). The assessment produces two documents: the Security Assessment Plan (SAP), which describes the scope and methodology of the assessment before it begins, and the Security Assessment Report (SAR), which documents findings and results after the assessment is complete.

This document presents a realistic SAP and SAR for ClearBridge HMS. The 3PAO conducting the assessment is SecureAssess Partners, LLC, represented by Lead Assessor Stephanie R. Goodwin.

---

## PART A: SECURITY ASSESSMENT PLAN (SAP)

### SAP Section 1: Assessment Scope

The scope of this assessment covers all 325+ FedRAMP Moderate controls applicable to ClearBridge HMS within the defined authorization boundary. The assessment includes all components within the AWS GovCloud (US-East) VPC, including EC2 instances, RDS databases, S3 buckets, ALB, CloudTrail, CloudWatch, KMS, and Systems Manager.

Inherited controls (fully inherited from AWS GovCloud FedRAMP High P-ATO) are noted as inherited in the assessment and are not re-tested. The assessment covers shared and customer-responsible controls.

| Assessment Element | Details |
|---|---|
| Assessment Organization | SecureAssess Partners, LLC |
| Lead Assessor | Stephanie R. Goodwin |
| Assessment Type | Initial Assessment (Pre-Authorization) |
| Assessment Period | June 3-28, 2024 |
| System | ClearBridge HMS, HHS-CB-HMS-2024-MOD |
| Baseline | FedRAMP Moderate (325+ controls) |
| Controls Inherited (Not Tested) | 52 (fully inherited from AWS) |
| Controls Assessed | 273 (shared and customer-responsible) |

### SAP Section 2: Assessment Methods

Per NIST SP 800-53A Rev 5, the 3PAO uses three assessment methods: Examine, Interview, and Test.

| Method | Description | Application to ClearBridge HMS |
|---|---|---|
| Examine | Review of documentation, policies, procedures, and configuration artifacts | Review SSP, policies, system architecture diagrams, scan reports, access review records |
| Interview | Structured discussions with system personnel | Interviews with ISSO (Ina Grace Kamara), Cloud Ops Lead (Kevin Ashworth), System Owner (Dr. Fletcher) |
| Test | Technical testing of system components | Vulnerability scanning, configuration audits, penetration testing, log review |

### SAP Section 3: Assessment Tools

| Tool | Purpose |
|---|---|
| Tenable Nessus | Vulnerability scanning (OS and application layer) |
| Burp Suite Pro | Web application security testing |
| AWS Config | Configuration compliance auditing |
| AWS Security Hub | Automated security findings aggregation |
| Manual review | Policy review, interview documentation, configuration verification |
| Network packet capture | Limited traffic analysis for SC-8 (TLS configuration verification) |

### SAP Section 4: Assessment Schedule

| Activity | Dates | Lead |
|---|---|---|
| Kickoff meeting with ISSO and system owner | June 3, 2024 | Stephanie R. Goodwin |
| Document review (SSP, policies, diagrams) | June 3-7, 2024 | SecureAssess team |
| Personnel interviews | June 10-12, 2024 | Stephanie R. Goodwin |
| Technical testing (vulnerability scans, config review) | June 13-21, 2024 | SecureAssess technical team |
| Penetration testing | June 17-19, 2024 | SecureAssess red team |
| Draft SAR delivered to ClearBridge | June 25, 2024 | Stephanie R. Goodwin |
| ClearBridge review and factual corrections | June 26-27, 2024 | Ina Grace Kamara, ISSO |
| Final SAR delivered to HHS | June 28, 2024 | Stephanie R. Goodwin |

---

## PART B: SECURITY ASSESSMENT REPORT (SAR)

### SAR Section 1: Executive Summary

SecureAssess Partners, LLC completed the FedRAMP Moderate security assessment of ClearBridge HMS during June 3-28, 2024. The assessment covered 273 controls (excluding 52 fully inherited from AWS GovCloud). The assessment team identified 18 findings, of which 3 are High risk, 8 are Moderate risk, and 7 are Low risk. No Critical findings were identified.

The system demonstrates a strong security posture in areas of identity and access management, encryption, network boundary protection, and audit logging. The primary gaps are in configuration management documentation, patch management timeliness for certain non-production instances, and the maturity of the continuous monitoring program.

All High-risk findings have been acknowledged by ClearBridge and are included in the POA&M with remediation timelines within 30 days of authorization.

| Finding Level | Count |
|---|---|
| Critical | 0 |
| High | 3 |
| Moderate | 8 |
| Low | 7 |
| Total | 18 |

### SAR Section 2: Control Assessment Results Summary

| Control Family | Controls Assessed | Satisfied | Other Than Satisfied |
|---|---|---|---|
| Access Control (AC) | 25 | 22 | 3 |
| Audit and Accountability (AU) | 16 | 15 | 1 |
| Configuration Management (CM) | 18 | 14 | 4 |
| Contingency Planning (CP) | 12 | 11 | 1 |
| Identification and Authentication (IA) | 12 | 12 | 0 |
| Incident Response (IR) | 10 | 9 | 1 |
| Risk Assessment (RA) | 9 | 8 | 1 |
| System and Communications (SC) | 44 | 42 | 2 |
| System and Information Integrity (SI) | 16 | 14 | 2 |
| Other Families | 111 | 108 | 3 |
| **Total** | **273** | **255** | **18** |

### SAR Section 3: Significant Findings

**Finding SAR-001: Patch Management Delay on Non-Production Instances (High)**
- Control: SI-2 (Flaw Remediation)
- Description: Two non-production EC2 instances had 14 unpatched High-severity vulnerabilities older than 60 days. These instances are used for development testing but share the authorization boundary.
- Risk: An attacker with access to the development environment could exploit these vulnerabilities to pivot to production systems.
- Recommendation: Apply patches immediately and update patch management procedures to include non-production instances within the same SLA as production.
- Status: Remediated before final SAR delivery (June 27, 2024)

**Finding SAR-002: Incomplete Configuration Baseline Documentation (High)**
- Control: CM-2 (Baseline Configuration)
- Description: The ClearBridge configuration baseline documentation does not cover 4 EC2 instance types added during a recent scale-out. The CMDB in ServiceNow was not updated.
- Risk: Untracked instances may have inconsistent configurations and could introduce unauthorized software or services.
- Recommendation: Update the configuration baseline document and CMDB to include all current instance types.
- Status: Open, included in POA&M (SAR-002), target completion July 15, 2024.

**Finding SAR-003: Penetration Test Identified Reflected XSS in Beneficiary Search Function (High)**
- Control: SI-10 (Information Input Validation)
- Description: The penetration test identified a reflected cross-site scripting (XSS) vulnerability in the beneficiary search input field. The field does not sanitize output before rendering.
- Risk: An attacker could craft a malicious URL that causes a victim's browser to execute arbitrary JavaScript in the context of the ClearBridge HMS session, potentially stealing session tokens.
- Recommendation: Implement output encoding and input validation for all search fields. Conduct a full code review of input handling.
- Status: Open, included in POA&M (SAR-003), target completion July 15, 2024.

### SAR Section 4: Assessment Team Attestation

SecureAssess Partners, LLC attests that the assessment was conducted in accordance with FedRAMP requirements and NIST SP 800-53A Rev 5. All findings are based on evidence collected during the assessment period. This SAR represents an accurate and independent assessment of the security posture of ClearBridge HMS.

Assessor: Stephanie R. Goodwin, SecureAssess Partners, LLC
Date: June 28, 2024

---

## Interview Defense Notes

- **What is the difference between a SAP and a SAR?** The SAP is the plan: it describes what the 3PAO will test, how they will test it, and the schedule. The SAR is the report: it documents what they actually found. The SAP comes before the assessment, the SAR comes after.
- **What are the three assessment methods in NIST SP 800-53A?** Examine (reviewing documents and artifacts), Interview (talking to system personnel), and Test (technical testing like scanning and pen testing). A rigorous assessment uses all three for each control.
- **What does "Other Than Satisfied" mean in a SAR?** It means the control has a finding: it is not fully implemented as required. OTS findings become POA&M items. The goal is to have zero OTS findings before authorization, or to accept the risk of open items in the POA&M.
- **What happens when a 3PAO finds a High finding?** It gets documented in the SAR with a risk rating, description, and recommendation. The CSP typically has to address High findings before authorization or include them in the POA&M with a 30-day remediation target. The AO decides whether to accept the risk or require remediation first.
- **Why does the ISSO review the draft SAR before it goes to the AO?** The ISSO reviews for factual accuracy, not to dispute findings. If a finding is based on outdated information or a misunderstanding of the configuration, the ISSO can provide corrections. This is called a factual correction period. The 3PAO retains the authority to determine whether to accept the correction.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*Assessment conducted by: Stephanie R. Goodwin, SecureAssess Partners, LLC*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
