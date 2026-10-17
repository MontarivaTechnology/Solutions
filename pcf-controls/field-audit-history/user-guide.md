# Field Audit History - User Guide

**Version 0.1.0** · PCF control for Dynamics 365 / Dataverse model-driven apps · by Montariva Technology

Field Audit History shows, on a model-driven form, who changed which field of the record and when, with the old and new value of every change. Instead of reading the full audit log, users pick a field, a period or a person and see only that history.

<img src="img/field-audit-history.png" width="480" alt="Field Audit History on a form" />

## Features

- Every audited column of the table in one list, with how many times each changed.
- Old and new values, formatted as on the form (lookup names, choice labels, dates).
- Periods: Today, Yesterday, Last 7 days, Last 30 days, All time, or your own dates.
- Search for a person by name and see only what they changed.
- A summary of fields changed, changes and people for the period.
- Changes newest first, grouped by day.

## Requirements

- A model-driven app (Dynamics 365 or Power Apps) on Dataverse.
- **Auditing** turned on at three levels:
  1. The environment: Power Platform admin center > environment > **Settings** > **Audit and logs** > **Audit settings** > *Start auditing*.
  2. The table: make.powerapps.com > **Tables** > your table > **Properties** > **Advanced options** > *Audit changes to its data*.
  3. Each column you want to follow: column > **Advanced options** > *Enable auditing*.
- Users need a security role with **View Audit History** and **View Audit Summary** (Miscellaneous privileges on the Core Records tab), and read access to Users (every standard role has it) for the person search.
- Only changes made after auditing was turned on are recorded, and only for as long as the environment keeps audit logs.

## Install

1. Download **[MrtFieldAuditHistory_managed.zip](https://github.com/MontarivaTechnology/Solutions/releases/download/FieldAuditHistory-v0.1.0/MrtFieldAuditHistory_managed.zip)**.
2. Go to [make.powerapps.com](https://make.powerapps.com), pick your environment, then **Solutions** > **Import solution** > **Browse**, choose the zip and select **Import**. More detail: [installing managed solutions](../../docs/installing-managed-solutions.md).

Import it once per environment. It works for every table.

## Add it to a form

The control needs a column to sit on. It never reads or changes that column, so use a spare one.

1. **Create a host column** on the table (once per table): **Columns** > **New column**, data type *Single line of text*, a name such as *Audit helper*. Save.
2. **Open the form** in the form designer.
3. **Add a tab** named *Audit* (recommended) or a section on an existing tab. One column, full width.
4. **Add the host column** to that section.
5. Select the column, then **Components** > **+ Component** > **Field Audit History (Montariva Technology)**. Set the options below and turn it on for Web (and Phone/Tablet if you want).
6. Select the column again and turn off **Show label**.
7. **Save** and **Publish**.

One control covers all fields of the record, so you only need it once per form.

## Settings

| Setting | Default | What it does |
|---|---|---|
| Host field | (required) | The column the control sits on. Never read or changed. |
| Title | *Field audit history* | Heading at the top of the control. |
| Starting period | Last 30 days | Period selected when the form opens. Users can change it. |
| Starting view | Table | *Table* or *Timeline* when the form opens. Users can switch with the two buttons above the changes. |
| Hide these fields | (empty) | Comma-separated column logical names to leave out, for example `modifiedon,versionnumber`. |
| Audit events per load | 100 | How many audit events are read at a time (25-500). Older ones load with *Load older changes*. |
| List height (px) | 520 | How tall the field list and the list of changes can grow (200-2000). Longer lists scroll inside the control, and the day headings stay visible while you scroll. |

## Using it

- **Period**: choose Today, Yesterday, Last 7 days, Last 30 days or All time. *Pick dates* shows a from and a to date; for a single day choose the same date twice, or fill in only one of them.
- **Fields**: the list on the left shows every audited column with its number of changes in the period. Select *All changes* to see everything, or one field to see only its history. Search narrows the list. *Changed fields only* hides fields with no changes; turn it off to see them all.
- **People**: leave the box empty for everyone, or start typing a name. Suggestions show the people who changed this record first, then other users of the environment whose name matches. Pick one to see only what they changed; the counts and summary then cover that person for the whole period. Typing a new name keeps the current person until you pick someone else; the × clears it.
- **Changes**: each change shows who made it, the time, the **old value** and the **new value**. *(empty)* means the field had no value. Use the buttons at the top right of the list to switch between the **table** (sort by *When*, *Changed by* or *Field* by clicking the column heading) and the **timeline** (grouped by day). Narrow sections and phones always use the timeline.
- **Summary**: the three tiles show fields changed, number of changes and people, for the period and person chosen. Click a tile for the details: *fields changed* lists each field with its number of changes and when it last changed; *changes* lists the days with changes; *people* lists who made changes, how many and on how many fields. Click a row to show that field, that day or that person.
- **Refresh** reads the history again, for example after someone edits the record.

On a narrow section or a phone the field list becomes a drop-down above the changes.

## Limits

- Shows field changes (updates). The values a record was created with are not shown yet.
- Changes to many-to-many relationships, sharing and access aren't shown; use **Related** > **Audit history** for those.
- Long text values are capped by Dataverse at about 5,000 characters in the audit log.
- Each audit event needs one request to read its old and new values, so very long periods take longer. Use a shorter period, or *Load older changes*.
- Microsoft notes that audit history isn't available in the mobile app.

## Security

- The control reads data only through the Dataverse Web API, as the signed-in user. Users see only history they are allowed to see.
- It never writes anything: not the host column, not the record, not the audit log.
- No data leaves the environment.

## Troubleshooting

| Message | What to do |
|---|---|
| Save the record first | The record is new. Save it; history appears once it exists. |
| Auditing is off for *table* | Turn on auditing for the table (and the environment). |
| No columns are audited | Turn on auditing for the columns you want to follow. |
| You can't view audit history | Give the user a role with View Audit History and View Audit Summary. |
| No changes in this period | Nothing audited changed in that period. Try *All time*, or check that the column is audited. |
| Couldn't load the history | Select *Try again*. If it keeps happening, check the browser console and your connection. |

## Update or uninstall

- **Update**: import the newer managed solution over the old one. Forms keep their settings.
- **Uninstall**: remove the control from every form first, then delete the *Field Audit History (Montariva Technology)* solution in **Solutions**. The host column is yours; delete it if you no longer need it.
