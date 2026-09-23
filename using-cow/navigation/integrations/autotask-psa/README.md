---
description: Instructions on connecting and configuring Autotask.
---

# Autotask PSA

## Introduction

Integrating Autotask with COW allows you to seamlessly synchronise your device and warranty data, ensuring that your information is up-to-date and accurately managed. This guide will walk you through the steps required to set up and configure your Autotask integration.

## Prerequisites

Before you begin the integration process, ensure you have the following information ready:

* **Autotask API Username**: Enter your Autotask API username.
* **Autotask API Password**: Enter your API password securely.

### Setup

{% @storylane/embed subdomain="app" linkValue="vjyicbi0m66d" url="https://app.storylane.io/share/vjyicbi0m66d" %}

## Sync Options

After a successful **Test**, the screen opens the **Sync Options** tab and loads the lists below from Autotask. Click **Submit** to save them along with your credentials.

| Setting                  | Description                                                                                          |
| ------------------------ | ---------------------------------------------------------------------------------------------------- |
| Select Device Types      | The active configuration item categories to sync.                                                    |
| Enable write back to PSA | Lets COW write changes back to Autotask.                                                             |
| Sync all clients         | Syncs devices for every active company. Turn it off to choose companies in **Select Clients** instead. |

To change the settings later, click the card again. Password and key fields are blank: leave them blank to keep the stored values. If you change the connection details, click **Test** again before you submit. To preview which devices would sync, enter the password and key fields again, then click **Test Report**. See [Test Report](../README.md#test-report). To remove the integration, see [Delete an Integration](../README.md#delete-an-integration).

## Troubleshooting

* **Test fails with "credentials incomplete"**: enter both the **Autotask API Username** and **Autotask API Password**.
* **Test fails with "Connected, but could not retrieve a sample company, device type, and device"**: the API user signed in, but cannot read at least one active company, configuration item category and configuration item. Check its security level against [autotask-permissions.md](autotask-permissions.md "mention").
* **Sync Options shows an error instead of the lists**: check the credentials on the **Credentials** tab, then open **Sync Options** again to retry.
