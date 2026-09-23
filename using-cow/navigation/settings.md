# Settings

This page allows you to configure and modify the setup initially completed through the onboarding wizard, offering you the flexibility to adjust the integrations and preferences as needed.

## General

The **General Settings** card shows the details of your COW organisation.

| Field           | Description                                                                                       |
| --------------- | ------------------------------------------------------------------------------------------------- |
| Domain          | The email domain your organisation is registered under.                                           |
| Owner           | The organisation owner. Click the card to open the **Advanced** tab, where the owner is changed.  |
| Tier            | Your current subscription tier. Click the card to open the **Subscription** tab.                  |
| Organization ID | The unique identifier of your organisation in COW.                                                |

## Subscription

The **Subscription Plans** card lists the three tiers and outlines your current one.

| Plan   | Price          | Devices                                                           | Button                                                                                                                                                  |
| ------ | -------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Free   | $0             | 250                                                               | None.                                                                                                                                                   |
| Pro    | $69 / month    | **Unlimited devices**, under a fair use policy with a default limit of 50,000 | **Subscribe** opens the payment page in a new tab. On the Pro tier the button reads **Cancel** and opens an email to request cancellation.   |
| Vendor | Custom pricing | **Unlimited devices**, and includes API access                    | **Contact Us** opens an email to ask about the Vendor plan. On the Vendor tier the button reads **Cancel** and opens an email to request cancellation. |

Taxes apply to the Pro plan for businesses based in the Netherlands.

## Email Notifications

The **Email Notifications** tab sets who receives notification emails and which events they cover.

{% hint style="warning" %}
You can configure email notification settings, but emails are not currently being sent out. This functionality is still under development.
{% endhint %}

| Setting                      | Description                                                                                      |
| ---------------------------- | ------------------------------------------------------------------------------------------------ |
| Notification Email Addresses | The recipients. Select a saved address or type a new one.                                        |
| Notification Types           | The events to notify about: **Sync Complete**, **Sync Fail** and **Warranty Update**.            |

**Save** stores the recipient list, and needs at least one address and one notification type selected. **Notification Types** starts empty each time you open the tab, so select the types again before saving.

**Test** sends a test email to the recipients already saved.

## Branding

The **Branding** tab sets the look of the PDF reports COW produces, such as the **Device Lifecycle Report** on the [Devices](devices/ "mention") page. The default branding applies to every report. A preset is a complete, named set of branding that you can assign to an individual report instead.

### Editing

The **Editing** row shows a **Default** chip and one chip for each preset. Click a chip to load that branding into the editor. The caption under the row confirms whether your changes apply to the default branding or to one preset only.

| Action     | Description                                                                                                                                                  |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| New preset | Creates a preset from the branding currently on screen, so you only change what differs. Enter a **Preset name** of up to 128 characters and click **Create**. |
| Rename     | Renames the selected preset. Reports assigned to it stay assigned.                                                                                             |
| Duplicate  | Saves a copy of the selected preset under a new name.                                                                                                          |
| Delete     | Deletes the selected preset straight away, without a confirmation prompt.                                                                                      |

**Rename**, **Duplicate** and **Delete** appear only while a preset is selected.

### Default Preset Per Report

Each report has a dropdown that sets the branding it uses: **Use default branding**, or one of your presets. A change here is saved as soon as you make it. When you generate a report, its **Branding preset** option overrides this choice for that report only.

### Logo and Cover Image

Uploaded images are shared between the default branding and every preset, so each preset picks from the same library. An upload is stored straight away. The image you select is saved when you save the branding.

| Setting     | Description                                                                                                                                                                                                                                                                                 |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logo        | Shown on the cover and in the page headers. Click **Upload logo** to add one, or select **No logo**. PNG or SVG works best, with JPG and WebP also accepted. A transparent background at around 200 × 100 px is ideal.                                                                            |
| Cover Image | Shown full-bleed at about 50% opacity behind the cover text, on cover pages only. Click **Upload cover** to add one, select **No cover image**, or pick one of the stock images: **SOC**, **Board**, **Glasses**, **Working**, **Laptop** or **City**. Use a JPG or PNG in portrait, around 1240 × 1754 px, and prefer soft or dark imagery. |

Each image must be under 1 MB, and each library holds up to five uploads. Delete an upload with the bin icon on its tile before adding another.

### Preview

The **Cover Preview** updates as you change settings. Click **Preview full report** to page through the whole report rendered with sample data, and **Show cover only** to return. **Report Type Preview** picks which report the preview shows. Sample figures appear only in the preview, never in a real report.

### Colours

| Setting      | Description                                                                                                                                                                                                  |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Brand Color  | Your main brand colour, `#F77F00` by default. It sets the cover accent, page rules, section headings, table headers and the first chart series. Text placed on it switches between white and near-black to stay readable. |
| Accent Color | Optional. It sets subheadings, callout rules and the second chart series. Leave it empty to use the brand colour everywhere.                                                                                    |
| Report Colors | Colours for individual parts of a report, listed below. Each part keeps its default until you set it, and parts that follow the brand colour keep following it.                                            |

| Report colour          | What it colours                                                                          |
| ---------------------- | ---------------------------------------------------------------------------------------- |
| Charts                 | The first series in every donut, bar and trend chart.                                    |
| Chart accent           | The second chart series. The remaining series are built between the two.                 |
| Page titles            | The large heading at the top of every content page.                                      |
| Cover text             | The title, subtitle, date and client name on the cover page.                             |
| Subtitles              | The line under a page title, and captions beneath charts and stats.                      |
| Section headings       | The heading above each block of content, and the rule under the page header.             |
| Body text              | Paragraphs, bullet lists and table cells.                                                |
| Footer                 | Footer text and page numbers.                                                            |
| Info cards             | The accent stripe on callout boxes and the rule above each stat card.                    |
| Data tables            | The header band across the top of every table. The header text follows it.               |
| Infographic figure     | The large statistic on full-bleed chapter dividers.                                      |
| Infographic background | The full-bleed divider page behind the artwork. Its text follows it.                     |
| Watermark              | The diagonal mark across each page, drawn at low opacity.                                |

Colours are hex values in the form `#RRGGBB`.

### Page Footer and Watermark

| Setting           | Description                                                                                                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Page Footer       | Text at the bottom of every report page. It accepts `%tenantname%`, `%clientname%`, `%orgname%`, `%reportname%` and `%reportdate%`, and is cut to 200 characters once they are filled in. |
| Cover Note        | Replaces the confidentiality note on cover pages. Leave it empty to keep each report's own wording. Also cut to 200 characters.                                                |
| Show footer text  | Shows or hides the page footer text.                                                                                                                                         |
| Show page numbers | Shows or hides page numbers.                                                                                                                                                 |
| Watermark         | Faint diagonal text across every page, cover included. Use `%tenantname%`, `%clientname%` or `%orgname%`, or a fixed mark such as `DRAFT`. Cut to 40 characters once filled in. |
| Show watermark    | Turns the watermark off without losing its text. Entering text is enough to show it.                                                                                         |

`%tenantname%` and `%clientname%` are replaced by the client the report is for. A placeholder the report cannot fill is printed as written.

### Saving and resetting

Click **Save Branding** to save the default branding. While a preset is selected, the button carries the preset's name, for example **Save "Client facing"**, and saves that preset only.

**Reset** appears only while **Default** is selected.

{% hint style="danger" %}
**Reset** acts immediately, with no confirmation prompt. It restores the default branding, deletes every uploaded logo and cover image, and clears the **Default Preset Per Report** choices. Presets are kept.
{% endhint %}

## User Management

The **Organization Users** table lists everyone with access to your organisation in COW.

| Column              | Description                                     |
| ------------------- | ----------------------------------------------- |
| User Principal Name | The user's email address.                       |
| Row Key             | The unique identifier of the user's COW account. |

Click **Add User**, enter the **User Email**, and confirm to give that person access. An address that already belongs to another COW organisation cannot be added.

<table><thead><tr><th>Action</th><th>Description</th><th data-type="checkbox">Bulk Action Available</th></tr></thead><tbody><tr><td>Delete User</td><td>Removes the user's access to your organisation. You cannot delete your own account.</td><td>true</td></tr></tbody></table>

## Advanced

The **Advanced Settings** card holds ownership, sync and data removal options. Only the organisation owner can change the owner or purge data.

| Setting                 | Description                                                                                                                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Owner Email             | Enter the new owner's address and click **Save**, then confirm in the **Update Organization Owner** dialog. Ownership transfers to that address. |
| Clear Sync Status       | Click **Clear Sync Status** to reset the sync status of every integration, so the next sync starts fresh. Use it when a sync appears stuck and new syncs are skipped.                                                           |
| Purge Organization Data | Permanently deletes the data you select, after a confirmation prompt. See below.                                                                                                                                               |

Turn on the data to delete, then click **Purge Selected**:

* **Purge Devices**: every device record.
* **Purge Logs**: every log entry.
* **Purge Messages**: every message.
* **Purge Credentials**: your integration credentials.
* **Purge PSA Config**: your PSA configuration.
* The final switch removes your organisation entry from COW completely. Turning it on also turns on every other option.

{% hint style="danger" %}
A purge cannot be undone.
{% endhint %}
