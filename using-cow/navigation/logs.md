# Logs

The **Logs** page lists the events recorded for your organisation, such as syncs, imports and settings changes.

## Log Filters

Expand **Log Filters** to narrow the table, then click **Apply Filters**. **Clear Filters** removes every filter.

| Filter              | Description                                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------- |
| Select Start Date   | The first day to show. Required when you set an end date.                                     |
| Select End Date     | The last day to show. It must be after the start date.                                        |
| Filter by User      | Shows only entries for the user name you enter. The name must match exactly.                  |
| Filter by Severity  | Shows only entries of the severity you pick: **Info**, **Warning**, **Error**, **Critical**, **Alert** or **Debug**. Picking more than one severity returns no entries. |

{% hint style="info" %}
With no filter applied, the table shows the last 7 days, based on UTC time. A date range longer than 10 days shows a warning, because a large range can time out.
{% endhint %}

## Table Details

| Column    | Description                                                            |
| --------- | ---------------------------------------------------------------------- |
| Timestamp | When the event happened.                                               |
| Message   | The details of the log entry.                                          |
| Severity  | The type of entry, for example `Info` or `Error`.                      |
| User      | The user whose action led to the entry, where there is one.            |
