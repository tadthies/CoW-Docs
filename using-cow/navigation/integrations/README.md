# Integrations

The **Integrations** page lists every system COW can read devices from. Each card shows whether that integration is set up for your organisation, and clicking a card opens its settings.

## Actions

| Action      | Description                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| Sync Status | Opens [sync.md](sync.md "mention"), where you can follow each integration's sync and queue a new one. |

## Integration Cards

Each card shows the integration's logo, a one-line description and its status. Click a card to open its settings screen.

| Integration        | Card description                                                                 | Setup guide                                                                       |
| ------------------ | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Halo PSA           | Sync device and warranty information from your HaloPSA system.                   | [halopsa](halopsa/ "mention")                                                     |
| ConnectWise Manage | Sync device and warranty information from your ConnectWise PSA system.           | [connectwise-psa](connectwise-psa/ "mention")                                     |
| Autotask PSA       | Sync device and warranty information from your Autotask PSA system.              | [autotask-psa](autotask-psa/ "mention")                                           |
| Azure Table        | Sync device and warranty information from an external Azure Table Storage table. | [azure-table.md](azure-table.md "mention")                                        |
| Azure Blob CSV     | Sync device and warranty information from a CSV file in Azure Blob Storage.      | [azure-blob-csv](azure-blob-csv/ "mention")                                       |

The status at the bottom of each card is one of:

| Status       | Description                                                                 |
| ------------ | --------------------------------------------------------------------------- |
| Unconfigured | The integration has never been saved. The dot is amber.                     |
| Disabled     | The integration is saved but **Enable Integration** is off. The dot is amber. |
| Enabled      | The integration is saved with **Enable Integration** on. The dot is green.  |

## Integration Settings

Clicking a card opens the settings screen for that integration. It shows the integration's logo, a short explanation, and a button for each vendor documentation link, which opens in a new tab. **Integrations** at the top returns to the previous page.

The settings are split into tabs:

* **Credentials**: the connection details and the **Enable Integration** switch. The fields for each integration are on its setup guide.
* **Sync Options**: Halo PSA, ConnectWise Manage and Autotask PSA only. It chooses which device types and clients are synced, and whether COW writes back to the PSA. The lists on this tab are loaded from your PSA when you open it.

The buttons at the bottom of the screen are:

| Action             | Description                                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Test               | Checks the connection details on the **Credentials** tab. Only shown on that tab. For a PSA, a successful test opens the **Sync Options** tab.                            |
| Test Report        | Previews which devices would sync with the settings on screen, and why the rest would be left out. See [Test Report](#test-report).                         |
| Submit             | Saves the settings. It stays disabled until **Test** succeeds, and again whenever you change the connection details of a saved integration.                             |
| Delete Integration | Only shown once the integration is saved. See [Delete an Integration](#delete-an-integration).                                                              |

When you save an integration with **Enable Integration** on, it appears on the [sync.md](sync.md "mention") screen as **Queued** until its first sync starts.

{% hint style="info" %}
When you reopen a saved integration, password and key fields are blank and show **Leave blank to keep the stored value**. **Test** and **Submit** use the stored value for a blank field, and you only need to test again if you change the connection details. **Test Report** does not use stored values, so enter the password or key fields again before you click it.
{% endhint %}

### Test Report

**Test Report** opens the **Integration Test Report** dialog. It reads the devices from the source with the settings currently on screen, including unsaved **Sync Options**, and shows what would happen to each one. Nothing is saved or synced. The screen marks the report as beta.

The report shows a **Report ID** and three summary cards. Click a card to filter the table below it.

| Card            | Description                                                              |
| --------------- | ------------------------------------------------------------------------ |
| Raw devices     | Every device row returned by the source.                                 |
| Filtered out    | Devices with a filter reason. These are not available for sync.          |
| Visible devices | Devices with no filter reason. These would sync with the current settings. |

**Why devices were filtered out** shows a count for each reason. Click a reason to show only those devices in the table.

| Reason                   | Description                                                                                                       |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| Device type not selected | The device type is not in your **Select Device Types** list.                                                      |
| Client not selected      | The device belongs to a client, or for ConnectWise Manage a company, that your **Sync Options** leave out.        |
| Empty serial number      | The device has no serial number.                                                                                  |
| Empty or excluded serial | ConnectWise Manage only. The serial number is missing, or is a placeholder.                                       |
| Excluded serial          | The serial number is a placeholder, such as `To Be Filled By O.E.M.`, `0123456789` or one character repeated.     |
| Invalid serial           | The serial number contains characters COW cannot store.                                                           |
| Duplicate serial         | An earlier device already has the same serial number, so this one is skipped.                                     |
| Unknown manufacturer     | The manufacturer is not in the source data and cannot be worked out from the serial number.                       |
| No client name           | The device could not be matched to a client or company name in the source.                                        |

The table lists each device with its **FilterReason**, **DeviceSerial**, **DeviceId**, **CompanyId**, **ClientName**, **DeviceName** and **DeviceManufacturer**. **FilterReason** is empty for a device that would sync.

### Delete an Integration

Click **Delete Integration**, then confirm. COW removes the integration's credentials and settings, its sync status, and the client list saved from its **Sync Options**, then returns you to the **Integrations** page. The card shows **Unconfigured** again.

{% hint style="danger" %}
Deleting an integration cannot be undone. To set it up again, you have to re-enter every credential.
{% endhint %}
