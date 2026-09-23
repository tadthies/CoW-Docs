---
description: Instructions on connecting and configuring ConnectWise PSA.
---

# ConnectWise PSA

## Introduction

Integrating ConnectWise PSA with COW allows you to seamlessly synchronise your device and warranty data, ensuring that your information is up-to-date and accurately managed. This guide will walk you through the steps required to set up and configure your ConnectWise PSA integration.

### Prerequisites

Before you begin the integration process, ensure you have the following information ready:

* **CW Instance URL**: Enter the URL of your ConnectWise instance.
* **Company Id**: Provide your company identification for ConnectWise.
* **Public Key**: Enter the public key of your API member.
* **Private Key**: Enter the private key of your API member securely.

{% hint style="warning" %}
Be sure to follow the guidance in [connectwise-permissions.md](connectwise-permissions.md "mention") to properly configure your API member to work with COW.
{% endhint %}

### Setup

{% @storylane/embed subdomain="app" linkValue="o0opja2qvrze" url="https://app.storylane.io/share/o0opja2qvrze" %}

## Sync Options

After a successful **Test**, the screen opens the **Sync Options** tab and loads the lists below from ConnectWise Manage. Click **Submit** to save them along with your credentials.

| Setting                  | Description                                                                 |
| ------------------------ | --------------------------------------------------------------------------- |
| Select Device Types      | The active configuration types to sync.                                     |
| Enable write back to PSA | Lets COW write changes back to ConnectWise Manage.                          |
| Select Company Types     | Syncs devices only from companies of these types.                           |
| Select Company Statuses  | Syncs devices only from companies with these active statuses.               |

ConnectWise Manage has no client list: the company types and statuses decide which companies are synced.

To change the settings later, click the card again. Password and key fields are blank: leave them blank to keep the stored values. If you change the connection details, click **Test** again before you submit. To preview which devices would sync, enter the password and key fields again, then click **Test Report**. See [Test Report](../README.md#test-report). To remove the integration, see [Delete an Integration](../README.md#delete-an-integration).

## Troubleshooting

* **Test fails with "credentials incomplete"**: enter the **CW Instance URL**, **Company Id**, **Public Key** and **Private Key**.
* **Test fails with "Connected, but could not retrieve a sample of each required ConnectWise entity"**: the API member signed in, but cannot read at least one company, company type, company status, configuration type and configuration. Check its role against [connectwise-permissions.md](connectwise-permissions.md "mention").
* **Sync Options shows an error instead of the lists**: check the credentials on the **Credentials** tab, then open **Sync Options** again to retry.
