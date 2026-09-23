# Lookup

The **Lookup** page checks the warranty of a single device by serial number, whether or not the device is one of your synced devices.

## Looking up a device

Enter the serial in **Serial Number** and click **Get Warranty**.

While you type, COW guesses the manufacturer from the length of the serial, and shows the guess when you hover over **Get Warranty**:

| Serial length       | Detected manufacturer   |
| ------------------- | ----------------------- |
| 7 characters        | Dell (Autodetect)       |
| 8 characters        | Lenovo (Autodetect)     |
| 9 characters        | Toshiba (Autodetect)    |
| 10 characters       | HP (Autodetect)         |
| 12 or 14 characters | Microsoft (Autodetect)  |

For a serial of any other length, the hover text says the manufacturer cannot be determined and **Get Warranty** stays unavailable.

## Results

The **Results** panel shows the outcome. When the serial is already in the COW warranty database, the result appears straight away under **Device found in warranty database!**:

| Field          | Description                                                                                          |
| -------------- | ---------------------------------------------------------------------------------------------------- |
| Serial Number  | The serial you looked up.                                                                            |
| Manufacturer   | The manufacturer of the device.                                                                      |
| Product Number | The manufacturer's product number for the device.                                                    |
| Status         | The warranty status.                                                                                 |
| Warranty Type  | The type of warranty.                                                                                |
| Start Date     | The start date of the warranty.                                                                      |
| Device Age     | The number of days since the warranty start date.                                                    |
| End Date       | The expiry date of the warranty.                                                                     |
| Days Remaining | The days left on the warranty, `Expires today`, or how many days ago it expired.                    |

When the manufacturer returns raw warranty data, it appears under **Raw Warranty Data**. Click the copy icon beside the heading to copy it.

## Serials not yet in COW

A serial COW has not seen before is queued for lookup. The button changes to **Processing...** and the panel shows **Processing warranty lookup...** while COW checks for the result every few seconds.

If no result arrives within about 25 seconds, the panel shows a message that the lookup is taking longer than expected. The device stays queued, so look up the same serial again later.
