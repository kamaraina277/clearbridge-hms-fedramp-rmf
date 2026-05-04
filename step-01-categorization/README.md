# Step 1: FIPS 199 Security Categorization Workbook

---

**Project Title:** FIPS 199 Security Categorization Workbook for ClearBridge Health Management System
**System Reference:** ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD
**Framework / Standard:** FIPS 199, NIST SP 800-60 Volume II Rev 1
**Author:** Ina Grace Kamara, ISSO, ClearBridge Technologies
**Date:** May 2024
**Status:** Complete

---

## Purpose

Step 1 of the NIST Risk Management Framework requires the system owner and ISSO to formally categorize the information system based on the potential impact that a loss of confidentiality, integrity, or availability would have on organizational operations, assets, or individuals. This categorization drives control selection in Step 2 and all subsequent authorization activities.

For ClearBridge HMS, categorization was performed using FIPS 199 (Standards for Security Categorization of Federal Information and Information Systems) and NIST SP 800-60 Volume II Rev 1 (Guide for Mapping Types of Information and Information Systems to Security Categories). The categorization was reviewed and approved by AO Robert T. Hargrove and SAISO Walter J. Drummond before SSP development began.

---

## System Overview for Categorization

| Field | Detail |
|---|---|
| System Name | ClearBridge Health Management System (HMS) |
| System ID | HHS-CB-HMS-2024-MOD |
| ISSO | Ina Grace Kamara, ClearBridge Technologies |
| System Owner | Dr. Carolyn M. Fletcher, HHS Deputy Director, Benefits Technology |
| Authorizing Official | Robert T. Hargrove, HHS CISO |
| SAISO | Walter J. Drummond, HHS Sr. Agency Information Security Officer |
| Categorization Completed | April 3, 2024 |
| AO Approval Date | April 10, 2024 |

---

## FIPS 199 Categorization Methodology

FIPS 199 defines three security objectives: Confidentiality, Integrity, and Availability. Each objective is evaluated at three impact levels: Low, Moderate, or High. The overall system security category is expressed as:

SC system = {(Confidentiality, impact), (Integrity, impact), (Availability, impact)}

The system impact level is determined by identifying all information types processed, stored, or transmitted by the system, categorizing each using SP 800-60 Vol. II, and applying the high-water mark principle: the highest impact level across all information types for each security objective becomes the system-level value for that objective.

---

## Information Type Identification and Categorization

The following information types were identified through interviews with system owners, review of data flow diagrams, and analysis of system documentation.

| # | Information Type | SP 800-60 Identifier | Confidentiality | Integrity | Availability |
|---|---|---|---|---|---|
| 1 | Health and Human Services Benefit Eligibility Data | C.3.1.1 | Moderate | Moderate | Low |
| 2 | Protected Health Information (PHI) | C.3.1.2 | Moderate | Moderate | Low |
| 3 | Personally Identifiable Information (PII) | C.3.5.8 | Moderate | Moderate | Low |
| 4 | Benefit Payment Records | C.3.1.3 | Moderate | Moderate | Low |
| 5 | Audit and Accountability Logs | D.16.1 | Low | Moderate | Low |
| 6 | System Configuration Data | D.16.2 | Low | Moderate | Low |
| 7 | User Account and Access Records | D.17.1 | Moderate | Moderate | Low |
| 8 | Incident Response Records | D.16.3 | Low | Low | Low |
| 9 | Treasury Disbursement Instructions | C.3.2.1 | Moderate | High | Low |
| 10 | CMS Medicare Eligibility Records (incoming) | C.3.1.4 | Moderate | Moderate | Low |

---

## High-Water Mark Analysis

Applying the FIPS 199 high-water mark principle across all information types:

| Security Objective | Highest Impact Level Identified | Information Type Driving the Rating |
|---|---|---|
| Confidentiality | Moderate | PHI, PII, Benefit Eligibility Data, Payment Records |
| Integrity | High | Treasury Disbursement Instructions (C.3.2.1) |
| Availability | Low | All information types categorized as Low availability |

---

## Rationale for Integrity High Rating (Treasury Disbursement)

The Treasury Disbursement Instructions information type (C.3.2.1) was initially categorized at Moderate Integrity. After review by the AO and the Privacy Officer, the team elevated it to High based on the following rationale: unauthorized modification of federal benefit payment instructions could result in direct financial harm to tens of thousands of beneficiaries, potential fraud or mispayment of federal funds, and significant reputational and legal consequences for HHS. This elevation was documented in a formal deviation memo reviewed by AO Robert T. Hargrove on April 10, 2024.

---

## Preliminary Security Category

Based on the high-water mark analysis:

**SC ClearBridge-HMS = {(Confidentiality, MODERATE), (Integrity, HIGH), (Availability, LOW)}**

---

## Agency Adjustment: Downgrade of Integrity to Moderate

Under FIPS 199 and FedRAMP guidance, the AO has the authority to adjust the preliminary categorization based on a risk-based determination. After consultation with the SAISO and the system owner, AO Robert T. Hargrove approved a downgrade of the Integrity impact from High to Moderate based on the following mitigating factors:

Treasury Disbursement API transactions are cryptographically signed using HMAC-SHA256 at the application layer. The API validates each transaction before processing and rejects any payload that fails signature verification. Transactions are logged in immutable CloudTrail records and reconciled against Treasury records daily. These compensating controls reduce the residual risk of an integrity failure to within the Moderate threshold.

**Final Approved Security Category:**

**SC ClearBridge-HMS = {(Confidentiality, MODERATE), (Integrity, MODERATE), (Availability, LOW)}**

**Overall System Impact Level: MODERATE**

This categorization determines that ClearBridge HMS will use the FedRAMP Moderate control baseline (325+ controls per NIST SP 800-53B).

---

## FIPS 200 Minimum Security Requirements

Based on the Moderate impact level, ClearBridge HMS is subject to the minimum security requirements defined in FIPS 200 for all 17 security control families: AC, AT, AU, CA, CM, CP, IA, IR, MA, MP, PE, PL, PS, RA, SA, SC, and SI.

---

## Approval and Sign-Off

| Role | Name | Organization | Date |
|---|---|---|---|
| ISSO | Ina Grace Kamara | ClearBridge Technologies | April 3, 2024 |
| System Owner | Dr. Carolyn M. Fletcher | HHS, Benefits Technology | April 7, 2024 |
| SAISO | Walter J. Drummond | HHS CISO Office | April 9, 2024 |
| Authorizing Official | Robert T. Hargrove | HHS CISO | April 10, 2024 |
| Privacy Officer | Angela N. Weiss | HHS Office of the General Counsel | April 8, 2024 |

---

## Related Documents

- Step 2: Control Tailoring Log and Customer Responsibility Matrix (../step-02-controls/README.md)
- Step 3: System Security Plan (../step-03-ssp/README.md)

---

## Interview Defense Notes

- **What is FIPS 199 and why does it matter?** FIPS 199 is a federal standard that defines how to categorize information systems based on the potential impact of a security failure. The categorization determines which control baseline applies, which in turn determines how much security work the system must do to get authorized.
- **What is the high-water mark principle?** It means you look at all the information types in the system and take the highest impact level for each security objective (C, I, A) across all of them. The highest one becomes the system-level value for that objective.
- **Why was ClearBridge HMS categorized as Moderate overall?** The high-water mark produced Moderate for Confidentiality and Availability was Low, but Integrity was initially High due to Treasury payment data. After review, the AO approved a downgrade to Moderate based on compensating controls, resulting in an overall Moderate system.
- **What is the difference between a preliminary and a final security category?** The preliminary category comes directly from the high-water mark analysis. The final category reflects any AO-approved adjustments based on risk analysis and compensating controls.
- **What does the security category determine?** It determines the FedRAMP baseline that applies. Moderate means 325+ controls from NIST SP 800-53B. High would mean 421+ controls. The category is the foundation for everything that follows in the RMF process.

---

*Prepared by: Ina Grace Kamara, ISSO, ClearBridge Technologies*
*System: ClearBridge Health Management System (HMS) | HHS-CB-HMS-2024-MOD*
*[GitHub Portfolio](https://github.com/kamaraina277)*
