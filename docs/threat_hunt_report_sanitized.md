# 📄 Threat Hunt Report (Sanitized Version)

## 🛡️ Executive Summary

A threat hunt was conducted to identify potential unauthorized remote-access activity aligned with known adversary tradecraft involving tools such as AnyDesk. Analysis of SIEM and endpoint telemetry identified multiple instances of remote-access software execution across several users and endpoints over a 30-day period.

Execution was primarily observed from **user-writable directories** (e.g., Downloads, Temp, user profile paths), indicating non-standard usage outside of controlled enterprise deployment mechanisms.

While no definitive evidence of adversary compromise was identified, the findings revealed a **validated policy and control gap related to unauthorized software usage**.

---

## 🎯 Objective

* Identify unauthorized or suspicious remote-access software execution
* Validate whether activity aligns with enterprise-approved tools
* Distinguish between benign, non-standard, and potentially malicious behavior
* Improve detection visibility and control enforcement

---

## 🔍 Methodology

The investigation followed a structured threat hunting lifecycle:

* **Discovery:** Identified presence of AnyDesk execution in SIEM telemetry
* **Scoping:** Grouped activity by user and host to identify patterns
* **Deep Analysis:** Extracted process execution, command-line, and file path details
* **Validation:** Reviewed raw event telemetry to confirm execution accuracy
* **Aggregation:** Summarized activity across a 30-day window
* **Outlier Analysis:** Investigated anomalies (e.g., uninstall behavior)

---

## 🔎 Key Findings

* Remote-access software execution identified across **multiple users and endpoints**
* Activity originated primarily from:

  * Downloads directory
  * Temp directory
  * User profile paths
* Repeated execution patterns observed over time
* Command-line arguments (e.g., `--local-control`, `--local-service`) confirmed active usage
* Outlier activity identified and assessed as **benign uninstall behavior**

---

## ⚖️ Assessment

The reviewed telemetry does not confirm active adversary compromise. However, it does confirm:

* **Unauthorized or unmanaged remote-access software usage**
* Execution outside of standard enterprise controls
* Increased risk of misuse or potential adversary abuse

This is classified as a **policy and control gap**, not a confirmed incident.

---

## 🚨 Actions Taken

* Conducted threat hunt across SIEM and endpoint telemetry

* Validated findings using raw event analysis

* Correlated activity across users, hosts, and execution paths

* Developed detection logic:

  **Alert:** *AnyDesk Execution from User-Writable Paths*

* Documented findings and escalated for validation

---

## 🧠 Detection Logic

**Objective:** Identify unauthorized remote-access tool usage

**Detection Criteria:**

* Process: `AnyDesk.exe`
* Execution from:

  * `C:\Users\*\Downloads\`
  * `C:\Users\*\AppData\Temp\`
  * Other user-writable directories

**Outcome:**
Improved visibility into unmanaged remote-access activity and control deviations

---

## 💼 Business Impact

* Identified a **control gap in software usage enforcement**
* Improved visibility into unauthorized remote-access tools
* Enabled faster detection of policy violations
* Supported decision-making for security and compliance teams
* Strengthened detection engineering capabilities

---

## 🛠️ Tools & Technologies

* Splunk (SIEM)
* Endpoint Telemetry (EDR)
* MITRE ATT&CK Framework
* Threat Intelligence–driven analysis

---

## 📌 Recommendations

* Enforce application control policies for remote-access tools
* Restrict execution from user-writable directories
* Validate business justification for identified users
* Monitor for continued unauthorized software usage
* Expand detection coverage for remote-access behavior

---

## 🧾 Conclusion

This threat hunt successfully identified **unauthorized remote-access software usage** within the environment. While no confirmed adversary activity was detected, the findings highlight a clear **policy and control gap** that requires remediation and continued monitoring.

---

## 🔐 Data Handling Notice

All data has been **sanitized and anonymized**:

* Usernames replaced (e.g., `USER_01`)
* Hostnames replaced (e.g., `HOST_01`)
* Domains and identifiers redacted
* Hashes and internal references removed

This preserves detection logic while protecting sensitive information.

---

## 👤 Author

Albert Glenn
Cybersecurity Engineer | Threat Detection | Vulnerability Management

