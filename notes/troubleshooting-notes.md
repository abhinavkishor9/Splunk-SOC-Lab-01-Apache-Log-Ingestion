# Splunk Troubleshooting Notes

## Overview

This document records issues encountered during the Apache Log Ingestion Lab and the steps taken to resolve them.

---

# Issue 1

## Problem

No events were returned for:

```spl
index=apache_lab
```

---

## Cause

The dataset was imported into the **main** index instead of **apache_lab**.

---

## Resolution

Check available indexes:

```spl
index=*
| stats count by index
```

Output:

```
main    4775
```

Use:

```spl
index=main
```

instead of:

```spl
index=apache_lab
```

---

# Issue 2

## Problem

The following query returned no results:

```spl
| eventcount summarize=false index=apache_lab
```

---

## Cause

The **apache_lab** index contained no events.

---

## Resolution

Verify available indexes:

```spl
index=*
| stats count by index
```

Confirm which index contains the imported data.

---

# Issue 3

## Problem

The dataset appeared to upload successfully, but searches returned no events.

---

## Resolution

Verify that the upload completed successfully.

Run:

```spl
index=*
```

or

```spl
index=*
| stats count by index
```

to identify where the data was stored.

---

# Useful SPL Queries

## View Events

```spl
index=main
```

---

## Count Events

```spl
index=main
| stats count
```

---

## Verify Source

```spl
index=main
| stats count by source
```

---

## Verify Sourcetype

```spl
index=main
| stats count by sourcetype
```

---

## Verify Host

```spl
index=main
| stats count by host
```

---

# Lessons Learned

- Always verify the destination index before importing data.
- Confirm successful ingestion using `stats count`.
- Verify the `source`, `host`, and `sourcetype` fields after onboarding.
- Ensure events are searchable before beginning investigations.
- Dedicated indexes simplify future SOC investigations and dashboard creation.
