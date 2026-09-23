---
description: Follow each integration's sync, queue a new one, and read the sync logs.
---

# Sync Status

The **Sync Status** page shows where each integration's sync has got to, and lists the log entries recorded while syncing. Open it with **Sync Status** on the [integrations](./ "mention") page. **← Back to Integrations** returns you there.

## Actions

| Action  | Description                                                                                                                                                                                  |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Refresh | Reloads the sync status cards.                                                                                                                                                               |
| Sync    | Opens **Trigger Sync**. Pick one or more integrations under **Integrations**, then click **Sync** to queue a sync for each. An integration with **Enable Integration** off, or one already queued or syncing, is skipped. |

## Dashboard

There is one card for each integration that has a sync status. A saved integration with **Enable Integration** on gets its card when you save it. With no cards, the page shows **No sync states found, please configure an integration first.** and a **Go to Integrations** button.

| Card detail | Description                                                                                                                  |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Name        | The integration's short name: `Halo`, `CWM`, `AT`, `AzureTable` or `BlobCSV`.                                                |
| Status      | Where the sync is. See the status table below.                                                                               |
| Progress    | How far through the sync is, as a percentage. Shown while a sync is in progress.                                            |
| Stage       | The step the sync is on, for example `Waiting in queue`.                                                                     |
| Devices     | Devices processed so far out of the total found. Shown once the total is known.                                              |
| Last Sync   | How long ago the status last changed, for example `2h 10m ago`, or `Never`.                                                  |
| Failures    | How many syncs in a row have failed. Shown only after a failure.                                                             |

The status chip on each card shows one of these:

| Status      | Description                                                                                       |
| ----------- | ------------------------------------------------------------------------------------------------- |
| Queued      | The sync is waiting to start. A newly saved integration shows this until its first sync starts.   |
| In Progress | The sync is running.                                                                              |
| Completed   | The last sync finished.                                                                           |
| Failed      | The last sync failed. Check the **Sync Logs** table for the reason.                               |
| Disabled    | The integration has failed three syncs in a row.                                                  |

Any other status is shown as written, for example `Processing devices` or `Looking up warranty` while a sync runs.

{% hint style="warning" %}
After three failed syncs in a row, the card shows **Disabled**. Fix the cause shown in the **Sync Logs** table, then use **Sync** to queue a new sync, or save the integration again from its settings screen.
{% endhint %}

## Table Details

The **Sync Logs** table lists the log entries from the last 7 days that relate to syncing. The full log for your organisation is on the [logs.md](../logs.md "mention") page.

| Column    | Description                                                                                 |
| --------- | ------------------------------------------------------------------------------------------- |
| Timestamp | When the event happened.                                                                    |
| Message   | The details of the log entry.                                                               |
| Severity  | The type of entry, for example `Info` or `Error`.                                           |
| User      | The user whose action led to the entry, where there is one.                                 |
| Type      | The part of the sync the entry came from: `Sync`, `Fetch`, `Process`, `Warranty` or `Writeback`. |
