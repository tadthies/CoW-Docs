---
description: >-
  This overview helps users understand how to manage device info and warranties
  efficiently via the Devices page.
---

# Devices

The **Devices** page lists every device COW tracks for your organisation, with its warranty status, and is where you sync, import and report on them.

## Actions

| Action                  | Description                                                                                                                                                                                                                                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Import CSV              | Imports devices from a CSV file, for when you use COW outside one of the supported [integrations](../integrations/ "mention"). See [csv-import.md](csv-import.md "mention") for more information. Unavailable once you reach your tier's device limit.                                                           |
| Sync Devices            | Opens the **Sync Devices** dialog. Select the **Integrations** to sync, or leave the field empty to sync every enabled integration, then click **Sync**. Integrations already syncing are skipped.                                                                                                              |
| Device Lifecycle Report | Opens a preview of the PDF lifecycle report. Under **Report Options**, choose the client in **Select Client**, a **Branding preset**, whether to **Classify devices by** **Warranty** or **Device Age**, the report **Currency**, and the **Average Replacement Cost**. Click **Download PDF** to save your copy. The logo, colours, cover and watermark come from the Branding tab in [settings.md](../settings.md "mention"). |

## Dashboard

| Card            | Description                                                                                       |
| --------------- | ------------------------------------------------------------------------------------------------- |
| Total Devices   | The number of devices in the table.                                                               |
| Percentage OK   | The percentage of devices whose status is `OK`.                                                   |
| Active Devices  | The number of devices whose status is `OK`.                                                       |
| Expired Devices | The number of devices whose status is anything other than `OK`, including devices not yet looked up. |

When 50 or fewer device slots remain on your tier, an **Approaching Device Limit** warning appears under the cards. Once you reach the limit, a **Device Limit Reached** alert appears instead, with a link to upgrade your subscription.

## Table Details

| Column                | Description                                                                                                                  |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Status                | The warranty status of the device, for example `OK`, or `No lookup performed` for a device not yet looked up.                |
| Device Name           | The name of the device.                                                                                                      |
| Device Manufacturer   | The manufacturer of the device.                                                                                              |
| Device Serial         | The serial number of the device.                                                                                             |
| Device Product Number | The manufacturer's product number for the device, where known.                                                               |
| Device Age (Days)     | The number of days since the warranty start date.                                                                            |
| Days Until Expiry     | The number of days before the warranty expires. A negative number means the warranty has already expired.                   |
| Client Name           | The client the device belongs to.                                                                                            |
| Warranty              | The type of warranty, `Unknown` until the device is looked up.                                                               |
| Last Lookup           | When the warranty was last checked, or `Never`.                                                                              |
| Start Date            | The start date of the warranty.                                                                                              |
| End Date              | The expiry date of the warranty.                                                                                             |
| Source                | Where the device came from, for example `ManualCSV` for a device imported from a CSV file.                                  |

## Table Features

| Feature | Description                                                                                                                                                              |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Refresh | Reloads the table and the dashboard cards.                                                                                                                               |
| Search  | Finds devices by any value in the table, such as a client name, serial number or manufacturer.                                                                          |
| Filters | **Show Column Filters** adds a filter box above each column, so you can filter on several columns at once. **Reset all filters** clears them.                            |
| Columns | Shows or hides individual columns. **Save as preferred columns** keeps your choice, **Reset to preferred columns** returns to it, and **Delete preferred columns** removes it. |
| Export  | **Export to CSV** or **Export to PDF** saves the table data, and **View API Response** shows the raw data behind it.                                                     |

## Table Actions

<table><thead><tr><th>Action</th><th>Description</th><th data-type="checkbox">Bulk Action Available</th></tr></thead><tbody><tr><td>View Device</td><td>Opens the device's <strong>Device Details</strong> page.</td><td>false</td></tr><tr><td>Get Warranty</td><td>Looks up the latest warranty details for the device, after a confirmation prompt. The lookup can take some time.</td><td>true</td></tr><tr><td>Delete Device</td><td>Removes the device from COW, after a confirmation prompt. Use this action with caution, as it cannot be undone.</td><td>true</td></tr></tbody></table>

## Device Details

**View Device** opens a page for a single device. **Back to Devices** returns to the table.

The header shows the manufacturer's logo, the device name, the manufacturer, and the warranty status. A device from a manufacturer without a logo shows `N/A` in place of one.

| Card               | Description                                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Device Information | **Device Name**, **Manufacturer**, **Serial Number**, **Product Number** and **Source**.                                                                                 |
| Client & Warranty  | **Client**, **Status**, **Warranty**, **Start Date**, **End Date**, **Device Age (Days)**, **Days Until Expiry** and **Last Lookup**.                                    |
| Payload            | The raw warranty data returned by the manufacturer, shown only when there is some. Its layout depends on the manufacturer, so it is not always easy to read.             |

Each value in the **Device Information** and **Client & Warranty** cards has a copy button beside it.
