# Deployment Doctor

An [XrmToolBox](https://www.xrmtoolbox.com/) tool that answers the classic ALM question: **"I deployed the managed solution. Why doesn't my change show?"** Works for **forms, views, web resources, classic workflows, business rules, actions and cloud flows**.

| Version | Install | Offline download |
|---|---|---|
| **1.0.0** | XrmToolBox **Tool Library** > search **Deployment Doctor** > **Install** | [DeploymentDoctor-1.0.0.zip](https://github.com/MontarivaTechnology/Solutions/releases/download/DeploymentDoctor-v1.0.0/DeploymentDoctor-1.0.0.zip) |

## What it finds

| Cause | Applies to |
|---|---|
| Changes not published in Dev before export | forms, views, web resources |
| Component not in the solution (table added without it) | all |
| Unmanaged (Active) layer in the target environment overriding your deployment | all |
| Another managed solution installed above yours | all |
| Staged upgrade never applied / imported as Update, so removed items stay | all |
| Flow or workflow turned off after import, connection reference without a connection, an old copy with the same name still on | processes |
| Form or view inactive, missing from the app, not the default; form security roles or order | forms, views |
| Script not used by any form; browser cache | web resources |

## Features

- **Two environments**: the target (where the change doesn't show) and, optionally, Dev (the source).
- **Verdict first**: "Most likely cause" and the **next step** at the top, then every check as Problem / Warning / OK / Info.
- **Solution layers** of the component, with your solution, layers above it and the unmanaged layer highlighted.
- **Readable Dev vs target comparison**: form tabs, sections and fields; view columns, filters and sort; changed script lines; cloud flow steps and connection references.
- **Guided fixes**: remove the unmanaged layer, publish in Dev, add to the Dev solution, turn a flow or workflow on. Before anything changes, a window shows **which user it runs as**, whether it can be undone, what to check first and the manual steps; nothing runs until you tick "I have read this".
- **Shareable reports**: HTML, CSV or text. Full content and environment URLs are left out unless you choose them.

## How to use

1. Connect XrmToolBox to the **target** environment (UAT / Prod) and open **Deployment Doctor**.
2. Click **Connect Dev (source)...** and pick your Dev connection (optional, but enables the most useful checks).
3. Pick the **solution you deployed**, the **type** (Form, View, Web resource, Process / flow), the **table** (or web resource prefix) and the item.
4. Click **Diagnose**. Read the verdict, then the findings. Use a **Fix** button if one is offered.
5. Click **Export report** to share the result.

Installing, updating or installing offline: [installing XrmToolBox tools](../../docs/installing-xrmtoolbox-tools.md).

## Support

[Open an issue](https://github.com/MontarivaTechnology/Solutions/issues/new/choose) and choose **Deployment Doctor**.
