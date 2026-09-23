# Azure Table

Connect COW to an **Azure Table Storage** table containing your devices. It is the self-serve option for technical MSPs who want to push and pull data programmatically. You run the table in your own Azure tenant and populate it however you like (script, Rewst, Power Automate, PSA export). COW reads your devices, looks up warranties, and can write the results back into the same rows.

## Prerequisites

Your table must contain these columns. All of them are required, and the test fails if any are missing:

* `ClientName`: the end client each device belongs to.
* `DeviceSerial`: the device serial number (COW's lookup key).
* `DeviceManufacturer`: the manufacturer. If blank or `Unknown`, COW attempts to detect it from the serial.
* `DeviceName`: a friendly device name.
* `CompanyId`: your identifier for the client.
* `DeviceId`: your identifier for the device.

{% hint style="info" %}
**Optional**: `StartDate` / `EndDate` if you already hold warranty dates (COW reads them, and overwrites on write-back). Each row's Azure `PartitionKey`/`RowKey` are used to target write-back, so keep them stable.
{% endhint %}

## Import Steps

{% stepper %}
{% step %}
### Create a SAS link

Follow Microsoft's documentation to create a [shared access signature (SAS) token](https://learn.microsoft.com/en-us/azure/ai-services/translator/document-translation/how-to-guides/create-sas-tokens?tabs=Containers). Read-only sync needs **Read** (query) permission; add **Add** and **Update** as well if you plan to enable write-back. When you copy it from Azure, paste the **SAS token string** (the part after the `?`), not the full SAS URL.
{% endstep %}

{% step %}
### Enter SAS Details

Enter the **Storage Account Name**, **Table Name** and **SAS Token**. The storage account name is 3 to 24 lowercase letters and numbers. The table name is 3 to 63 letters and numbers, starting with a letter.
{% endstep %}

{% step %}
### Test the Connection

Click **Test** to confirm the token authenticates, the table is readable, and all required columns are present (your table needs at least one row for the column check). To see which rows would sync before you save, click **Test Report**. See [Test Report](README.md#test-report).
{% endstep %}

{% step %}
### Enable the Integration

Turn on **Enable Integration**. Optionally turn on **Write Back to Table** to save warranty results (`StartDate`, `EndDate`, `Warranty`, `Status`, `WarrantyJSON`) back onto your existing rows.
{% endstep %}

{% step %}
### Submit

Click **Submit** to save the integration. It then appears on the [sync.md](sync.md "mention") screen as **Queued** until its first sync starts. To queue a sync yourself, use **Sync** on that screen.
{% endstep %}
{% endstepper %}

To change the settings later, click the **Azure Table** card again. The **SAS Token** field is blank: leave it blank to keep the stored token, or enter a new one and click **Test** before you submit. To remove the integration, see [Delete an Integration](README.md#delete-an-integration).

## What COW writes back

With **Write Back to Table** on, for each device where a warranty is found COW updates that device's **existing row** (matched on its original `PartitionKey`/`RowKey`) with `StartDate`, `EndDate` (both `YYYY-MM-DD`), `Warranty` (description), `Status`, and `WarrantyJSON` (a compact JSON of all of it plus the lookup time). Unresolved devices are left untouched and retried next sync.

## Troubleshooting

* **Test fails "missing required columns"**: add the exact column names above.
* **Test fails "table is empty"**: the column check needs at least one row.
* **Test fails to authenticate**: make sure you pasted the SAS **token string** (the part after the `?`), not the full SAS URL.
* **Some devices never appear**: filtered for empty/placeholder `DeviceSerial`, blank `ClientName`, undetectable manufacturer, or your plan's device cap (upgrade to raise it). **Test Report** lists each row that would be left out, with the reason.
* **Warranties aren't writing back**: confirm write-back is on, the SAS has Add/Update, and rows still have the `PartitionKey`/`RowKey` COW first read them under.

{% hint style="warning" %}
Set the SAS token's expiry well into the future. Syncs stop the moment it expires, and you'll need to generate a new one.
{% endhint %}
