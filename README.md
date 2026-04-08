# 🛡️ Threat Hunt Case Study: Unauthorized Remote Access Detection (Splunk + EDR)

## 📌 Overview

This project documents a **threat intelligence-driven hunt** focused on identifying unauthorized remote-access activity within an enterprise environment. The investigation was initiated based on adversary tradecraft indicating the use of remote-access tools (e.g., AnyDesk) for potential hands-on-keyboard activity.

The objective was to determine whether observed activity represented **benign usage, policy violations, or potential malicious behavior**, while improving detection visibility and operational awareness.

---

## 🎯 Objective

* Identify suspicious remote-access software execution
* Validate whether activity aligns with approved enterprise controls
* Distinguish benign vs non-standard vs potentially malicious behavior
* Develop detection logic to improve visibility into unmanaged tools

---

## 🔍 Investigation Workflow

This hunt followed a structured threat hunting lifecycle:

1. **Discovery** – Identify presence of AnyDesk execution
2. **Scoping** – Group activity by host and user
3. **Deep Analysis** – Extract process, command-line, and file path details
4. **Validation** – Review raw telemetry for accuracy
5. **Aggregation** – Summarize activity across users and endpoints
6. **Detection Development** – Identify patterns for alerting
7. **Outlier Analysis** – Separate normal vs suspicious behavior

---

## 📸 Investigation Walkthrough

### 1. Discovery – Identifying AnyDesk Execution

<img width="2317" height="1171" alt="image" src="https://github.com/user-attachments/assets/37de7ff0-b3d4-4f3b-8fab-2c4346016e3f" />


### 2. Host Scoping – Identifying Affected Systems

<img width="2950" height="1440" alt="image" src="https://github.com/user-attachments/assets/160f2475-3499-40c7-9f47-6bae70a90b7c" />

### 3. Multi-User Analysis – Identifying Spread Across Users

<img width="1433" height="736" alt="image" src="https://github.com/user-attachments/assets/a40563da-1649-40e9-bae0-90100824a8e4" />


### 4. Targeted Investigation – Deep Dive on Specific Host

<img width="2894" height="1472" alt="image" src="https://github.com/user-attachments/assets/bb6a0bb7-ea2e-40b3-ab68-6d100c36ca8c" />


### 5. Raw Event Validation – Confirming Execution Details

<img width="2944" height="1440" alt="image" src="https://github.com/user-attachments/assets/5d08f2b6-a945-4c42-8a6e-f030edef2076" />


### 6. Deep Analysis – Process + Command Line Breakdown

<img width="2942" height="1408" alt="image" src="https://github.com/user-attachments/assets/99566756-278e-4cc9-927c-e75bd2ce5644" />


---

## 🔍 Key Findings

* Identified unauthorized AnyDesk execution across **multiple users and endpoints**
* Observed execution from **user-writable directories** (Downloads, Temp), indicating control gaps
* Detected repeated execution patterns suggesting **non-standard remote-access usage**
* Validated activity using **raw telemetry, process execution logs, and command-line analysis**
* Differentiated between **benign usage and potential security risk**

---

## 🚨 Detection Logic Developed

**Alert Name:** `BT - AnyDesk From User-Writable Path`

### Detection Strategy:

* Monitor execution of `AnyDesk.exe`
* Flag executions from:

  * `C:\Users\*\Downloads\`
  * `C:\Users\*\AppData\Temp\`
  * Other user-writable directories

### Goal:

* Detect unauthorized or unmanaged remote-access tools
* Improve visibility into policy violations and potential attack vectors

---

## 💼 Business Impact

* Improved visibility into unauthorized remote-access software usage
* Enabled faster identification of **policy violations and control gaps**
* Supported security and compliance teams with validated findings
* Reduced risk of unauthorized remote access across enterprise endpoints
* Strengthened detection capabilities through repeatable logic

---
## 📄 Threat Hunt Report

A sanitized version of the full threat hunt report is available here:

➡️ [View Report](docs/threat_hunt_report_sanitized.md)


---

## 🛠️ Tools & Technologies

* **Splunk** (SIEM)
* **BeyondTrust** (EDR / Privileged Access Telemetry)
* **MITRE ATT&CK Framework**
* Threat Intelligence–driven analysis

---

## 📂 Repository Structure

```
.
├── README.md
├── queries/
│   ├── discovery_query.txt
│   ├── host_scoping_query.txt
│   ├── targeted_host_investigation.txt
│   ├── raw_event_validation.txt
│   ├── user_activity_summary.txt
│   ├── multi_user_summary.txt
│   ├── outlier_uninstall_analysis.txt
│   └── README.md
├── screenshots/
│   ├── Discover Query.png
│   ├── Host Scoping.png
│   ├── Multi-user-summary.png
│   ├── Single User.png
│   ├── Raw Event.png
│   └── Deep Analysis.png
```

---

## 🔐 Data Handling Note

All data in this project has been **sanitized and anonymized**:

* Hostnames replaced (e.g., `HOST_01`)
* Usernames replaced (e.g., `USER_01`)
* Domains and tenant identifiers redacted
* Hashes and internal identifiers masked

This ensures preservation of detection logic while protecting sensitive information.

---

## 🚀 Key Takeaway

This project demonstrates the ability to:

* Conduct **end-to-end threat hunts**
* Analyze **large-scale SIEM + EDR telemetry**
* Validate findings using **raw event data**
* Translate investigations into **detection engineering outputs**
* Communicate findings with **clear business impact**

---

## 👤 Author

Albert Glenn
Cybersecurity Engineer | Threat Detection | Vulnerability Management

---


