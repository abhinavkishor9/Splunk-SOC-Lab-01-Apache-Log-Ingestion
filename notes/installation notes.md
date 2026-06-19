# Splunk Installation Notes

## Overview

This document records the installation and initial configuration of Splunk Enterprise used for the Apache Log Ingestion Lab.

---

# Installation Environment

- Operating System: Windows 10/11
- SIEM Platform: Splunk Enterprise 10.x
- Installation Type: Local Installation

---

# Installation Directory

```
D:\Splunk\
```

---

# Splunk Web

Access URL:

```
http://localhost:8080
```

---

# Initial Configuration

The following configuration steps were completed:

- Installed Splunk Enterprise
- Started Splunk services
- Configured administrator credentials
- Verified Splunk Web access
- Opened Search & Reporting application

---

# Apache Dataset Location

The Apache access log dataset was stored under:

```
D:\Datasets\Apache\
```

Example:

```
apache_access.log
```

---

# Data Onboarding

Navigation:

```
Settings
→ Add Data
→ Upload
```

Dataset uploaded successfully.

---

# Index Used

```
main
```

---

# Event Count Verification

```spl
index=main
| stats count
```

Expected output:

```
4775
```

---

# Verification Queries

View events:

```spl
index=main
```

Verify source:

```spl
index=main
| stats count by source
```

Verify sourcetype:

```spl
index=main
| stats count by sourcetype
```

Verify host:

```spl
index=main
| stats count by host
```

---

# Notes

The original plan was to import the dataset into the **apache_lab** index.

However, the dataset was successfully imported into the **main** index.

Future labs will use dedicated indexes for better organization.
