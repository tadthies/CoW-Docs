---
description: The SAS permissions the Azure Blob CSV integration needs, and why.
---

# Azure Blob CSV Permissions

The Azure Blob CSV integration reaches your CSV file through a SAS URL, so the SAS is the only access COW has. Scope it to the one file and grant only the permissions below.

| Area                | Permission | Why                                                                                   |
| ------------------- | ---------- | ------------------------------------------------------------------------------------- |
| The CSV file (blob) | Read       | To download the file during **Test**, **Test Report** and every sync.                  |
| The CSV file (blob) | Write      | To upload the updated file when **Write Back to CSV** is on. Not needed without write-back. |

The SAS must also:

* allow HTTPS, because the URL must start with `https://`
* expire at least 12 months from the day you save the integration, because the settings screen rejects an earlier expiry

{% hint style="warning" %}
**Test** only reads the file, so it succeeds with a read-only SAS. If you turn on **Write Back to CSV**, check that the SAS includes **Write** as well.
{% endhint %}

{% hint style="info" %}
When the SAS is close to expiring, create a new one and paste the new URL into the integration's settings. Once the saved URL's expiry is less than 12 months away, the URL field shows an error and **Submit** stays disabled until you replace it.
{% endhint %}
