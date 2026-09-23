---
description: Instructions on connecting and configuring Halo.
---

# HaloPSA

## Introduction

Integrating HaloPSA with COW allows you to seamlessly synchronise your device and warranty data, ensuring that your information is up-to-date and accurately managed. This guide will walk you through the steps required to set up and configure your HaloPSA integration.

### Prerequisites

Before you begin the integration process, ensure you have the following information ready:

* **HaloPSA URL**: Enter the URL of your HaloPSA instance.
* **HaloPSA Client ID**: Enter the client ID for authentication.
* **HaloPSA Secret**: Enter your API secret securely.

### Setup

{% @storylane/embed subdomain="app" linkValue="xmyh2w67fya7" url="https://app.storylane.io/share/xmyh2w67fya7" %}

## Sync Options

After a successful **Test**, the screen opens the **Sync Options** tab and loads the lists below from HaloPSA. Click **Submit** to save them along with your credentials.

| Setting                    | Description                                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Select Device Types        | The asset types to sync. Syncing asset types COW does not support can make syncs take longer.                 |
| Select Serial Number Field | The HaloPSA field that holds each asset's serial number: `Fields_Serial_Number`, `inventory_number`, `key_field`, `key_field2` or `key_field3`. |
| Enable write back to PSA   | Lets COW write changes back to HaloPSA.                                                                      |
| Sync all clients           | Syncs devices for every client. Turn it off to choose clients in **Select Clients** instead.                 |

{% hint style="warning" %}
`Fields_Serial_Number` reads the asset's **Serial Number** field, which can make syncs much slower and run into HaloPSA rate limits. Use one of the other fields where you can. With `Fields_Serial_Number`, **Test Report** also needs at least one device type selected.
{% endhint %}

To change the settings later, click the card again. Password and key fields are blank: leave them blank to keep the stored values. If you change the connection details, click **Test** again before you submit. To preview which devices would sync, enter the password and key fields again, then click **Test Report**. See [Test Report](../README.md#test-report). To remove the integration, see [Delete an Integration](../README.md#delete-an-integration).

## Troubleshooting

* **Test fails with "credentials incomplete"**: enter the **HaloPSA URL**, **HaloPSA Client ID** and **HaloPSA Secret**.
* **Test fails with "Connected, but could not retrieve a sample device, device type, and client"**: the API application signed in, but cannot read at least one asset, asset type and client. Check its permissions against [halo-psa-permissions.md](halo-psa-permissions.md "mention").
* **Sync Options shows an error instead of the lists**: check the credentials on the **Credentials** tab, then open **Sync Options** again to retry.
