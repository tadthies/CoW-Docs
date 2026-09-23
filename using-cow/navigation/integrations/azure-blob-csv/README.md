---
description: Instructions on connecting COW to a CSV file in Azure Blob Storage.
---

# Azure Blob CSV

## Introduction

Connect COW to a CSV file of your devices stored in **Azure Blob Storage**. You keep the file in your own Azure storage account and update it however you like, for example from a script or a PSA export. COW reads the devices from the file, looks up their warranties, and can write the results back into the same file.

{% hint style="warning" %}
The settings screen marks this integration as beta, and warns that it may be unreliable, especially for write-back. Use [azure-table.md](../azure-table.md "mention") instead where you can.
{% endhint %}

## Prerequisites

### The CSV file

The file must have a `.csv` extension, a header row, and at least one device row. The columns can be separated by commas, semicolons, tabs or pipes: COW detects which one the file uses.

The header row must contain all of these columns, even where a column is empty. The test fails if any are missing.

| Column             | What it holds                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------ |
| `ClientName`       | The end client each device belongs to. A row without one is not synced.                    |
| `DeviceSerial`     | The device serial number, which COW uses to look up the warranty.                          |
| `DeviceManufacturer` | The manufacturer. If it is blank or `Unknown`, COW tries to detect it from the serial number. |
| `DeviceName`       | A friendly name for the device.                                                            |
| `DeviceId`         | Your identifier for the device.                                                            |
| `CompanyId`        | Your identifier for the client.                                                            |
| `StartDate`        | The warranty start date.                                                                   |
| `EndDate`          | The warranty end date.                                                                     |
| `Warranty`         | The warranty description.                                                                  |
| `Status`           | The warranty status.                                                                       |

### The SAS URL

COW reaches the file through a shared access signature (SAS) URL: the full address of the file with the SAS token after the `?`. The URL must:

* start with `https://` and point to `*.blob.core.windows.net`
* end in the file name, with the `.csv` extension, before the `?`
* contain an expiry (`se`) at least 12 months from today
* contain a signature (`sig`)

The permissions the SAS needs are on [azure-blob-csv-permissions.md](azure-blob-csv-permissions.md "mention").

## Setup

{% stepper %}
{% step %}
### Create a SAS URL

Follow Microsoft's documentation to create a [shared access signature (SAS) token](https://learn.microsoft.com/en-us/azure/ai-services/translator/document-translation/how-to-guides/create-sas-tokens) for the CSV file, with the permissions on [azure-blob-csv-permissions.md](azure-blob-csv-permissions.md "mention"). Set the expiry at least 12 months ahead. Copy the full **Blob SAS URL**, not just the token.
{% endstep %}

{% step %}
### Enter the URL

On the **Integrations** page, click the **Azure Blob CSV** card, then paste the URL into **Azure Blob Storage URL**. The field shows an error straight away if the URL breaks one of the rules above.
{% endstep %}

{% step %}
### Test the connection

Click **Test**. COW downloads the file and checks the header row. A successful test shows how many rows it found. To see which rows would sync before you save, click **Test Report**. See [Test Report](../README.md#test-report).
{% endstep %}

{% step %}
### Enable the integration

Turn on **Enable Integration**. Turn on **Write Back to CSV** as well if you want COW to save warranty results into the file.
{% endstep %}

{% step %}
### Submit

Click **Submit** to save the integration. It then appears on the [sync.md](../sync.md "mention") screen as **Queued** until its first sync starts. To queue a sync yourself, use **Sync** on that screen.
{% endstep %}
{% endstepper %}

To remove the integration, see [Delete an Integration](../README.md#delete-an-integration).

## What COW writes back

With **Write Back to CSV** on, COW writes warranty results back into the file. It does this by uploading a complete new copy of the file, using the same column separator the file already has.

{% hint style="warning" %}
Because the whole file is replaced, changes made to the file while a sync is running can be overwritten. Update the file between syncs.
{% endhint %}

## Troubleshooting

* **The URL field shows an error**: the URL breaks one of the rules under [The SAS URL](#the-sas-url). A URL copied without the token, or with an expiry less than 12 months away, is rejected.
* **Test fails with "Missing headers"**: add the listed columns to the header row, spelt as in the table above.
* **Test fails on a file with only a header row**: add at least one device row.
* **Test fails to detect the delimiter**: the first five lines must split into the same number of columns. Check for a stray separator inside a value.
* **Some devices never appear**: rows with an empty or placeholder `DeviceSerial`, a duplicate serial, a blank `ClientName`, or a manufacturer COW cannot detect are left out. **Test Report** lists each of them with the reason.
* **Warranties are not written back**: confirm **Write Back to CSV** is on and the SAS has **Write** permission. **Test** only reads the file, so it passes without write permission.
* **Submit stays disabled when editing the integration**: the saved URL's expiry is now less than 12 months away. Create a new SAS URL, paste it in and click **Test**.
