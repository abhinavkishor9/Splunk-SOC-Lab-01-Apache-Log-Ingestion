# Splunk-SOC-Lab-01-Apache-Log-Ingestion

## Overview

This lab demonstrates the process of importing Apache HTTP access logs into Splunk Enterprise and verifying successful data ingestion.

Data onboarding is the first step in every SIEM deployment and SOC workflow. Before security monitoring and threat hunting can begin, logs must be correctly indexed and searchable.

This lab focuses on validating the ingestion process and understanding how Splunk stores and searches log data.

---

# Lab Environment

- Windows 10/11 Host
- Splunk Enterprise
- Search & Reporting App
- Apache Access Log Dataset

---

# Scenario

You have joined the Security Operations Center (SOC) team of an organization.

The SOC team has received Apache web server access logs from a production web server. Your task is to onboard the logs into Splunk and verify that they have been indexed correctly for future investigations.

---

# Objectives

- Import Apache access logs into Splunk
- Verify successful data ingestion
- Validate searchable events
- Identify source and sourcetype
- Record ingestion statistics
- Prepare the dataset for future threat hunting

---

# Lab Environment

| Component | Value |
|------------|------------|
| SIEM | Splunk Enterprise |
| Dataset | Apache Access Logs |
| Search App | Search & Reporting |
| Index Used | main |
| Total Events | 4775 |

---

# MITRE ATT&CK Mapping

| Technique | Description |
|------------|------------|
| T1071.001 | Application Layer Protocol: Web Protocols |
| T1190 | Exploit Public-Facing Application |
| T1595 | Active Scanning |

> This lab focuses on data onboarding. MITRE mapping is included for future investigation labs.

---

# Severity

**Informational**

This lab does not investigate malicious activity. The objective is successful log ingestion and validation.

---

# Dataset

Apache HTTP Access Logs

Stored locally under:

```
D:\Datasets\Apache\
```

---

# Step 1: Launch Splunk

Open Splunk Enterprise:

```
http://localhost:8080
```

Login using your administrator credentials.

---

# Step 2: Upload Dataset

Navigate to:

```
Settings
→ Add Data
→ Upload
```

Select the Apache access log dataset and upload it.

---

# Step 3: Select Index

Import the dataset into the **main** index.

Complete the upload wizard.

---

# Step 4: Verify Events

Open:

```
Apps
→ Search & Reporting
```

Run:

```spl
index=main
```

Verify that Apache log events appear.

---

# Step 5: Count Events

Run:

```spl
index=main
| stats count
```

Expected Output:

```
count
4775
```

---

# Step 6: Verify Sourcetype

Run:

```spl
index=main
| stats count by sourcetype
```

Record the detected sourcetype.

---

# Step 7: Verify Source

Run:

```spl
index=main
| stats count by source
```

Record the imported source file.

---

# Step 8: Verify Host

Run:

```spl
index=main
| stats count by host
```

Record the host field value.

---

# Step 9: Verify Index

Run:

```spl
| eventcount summarize=false index=main
```

Confirm that Splunk reports the indexed events successfully.

---

# Detection Logic

Successful ingestion is confirmed when:

```spl
index=main
```

returns searchable Apache log events.

Verify total events:

```spl
index=main
| stats count
```

---

# Validation Performed

- Dataset uploaded successfully
- Events indexed successfully
- Events searchable
- Source verified
- Sourcetype verified
- Host verified
- Event count validated

---

# False Positives

Not Applicable.

This exercise focuses on data onboarding rather than attack detection.

---

# Indicators of Compromise (IOCs)

None.

No malicious activity is simulated in this lab.

---

# Recommended Investigation

Verify the following:

- Index assignment
- Sourcetype
- Source field
- Host field
- Timestamp parsing
- Total event count

---

# Recommended Containment

Not Applicable.

No security incident exists.


# Skills Demonstrated

- Splunk Enterprise
- SIEM Data Onboarding
- Index Management
- Search & Reporting
- SPL Fundamentals
- Event Validation
- Log Analysis
- Security Monitoring

---

# Lessons Learned

This lab improved understanding of:

- Splunk Architecture
- Data Onboarding
- Event Indexing
- Search & Reporting
- SPL Basics
- Source Verification
- Sourcetype Identification
- SIEM Fundamentals

---


✅ Data Searchable

✅ Ready for SOC Investigation Labs
