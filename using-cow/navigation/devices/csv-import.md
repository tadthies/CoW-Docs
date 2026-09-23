# CSV Import

A CSV import is the quickest way to try COW, and the way to add devices when you don't use one of the supported [integrations](../integrations/ "mention"). Click **Import CSV** on the [devices](./ "mention") page to open the **Import Devices** dialog.

## File Requirements

Only `DeviceSerial` is mandatory. The other columns are optional:

* `DeviceSerial`: The serial number of the device.
* `DeviceManufacturer`: The manufacturer of the device.
* `ClientName`: The client the device belongs to.
* `DeviceName`: The name of the device.
* `CompanyId`: Your own identifier for the client.
* `DeviceId`: Your own identifier for the device.

### Example CSV

Click **Download Example CSV** in the dialog for a file with every column header, or download the [example CSV file](data:text/csv;charset=utf-8,%EF%BB%BFDeviceSerial%2CDeviceManufacturer%2CClientName%2CDeviceName%2CCompanyId%2CDeviceId%0A) here.

## Importing

1. Drop your CSV file on the upload area, or click it to browse for the file. The rows appear in the **CSV Preview** table.
2. Remove any row you don't want with **Delete Row**.
3. Click **Import**.

Rows with an empty `DeviceSerial` and repeated serial numbers are removed from the preview, and a notice says how many. **Import** stays unavailable while any row is missing a serial number.

On import, COW skips serial numbers that are already in your manual CSV devices, and serial numbers it recognises as placeholders rather than real serials. The imported devices show a status of `No lookup performed` until their first warranty lookup finishes.

{% hint style="warning" %}
An import that would take you over your subscription's device limit is refused, and the message says how many devices you can still add. When you are at the limit, **Import CSV** is unavailable.
{% endhint %}
