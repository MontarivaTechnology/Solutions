# Deployment Doctor

An [XrmToolBox](https://www.xrmtoolbox.com/) tool that answers the classic ALM question: **"I deployed the managed solution. Why doesn't my change show?"**
Check **one component** and get the cause and the fix, or **compare a whole solution** between Dev and Target in one go.

| Version | Install | Offline download |
|---|---|---|
| **1.5.2** | XrmToolBox **Tool Library** > search **Deployment Doctor** > **Install** | [DeploymentDoctor-1.5.2.zip](https://github.com/MontarivaTechnology/Solutions/releases/download/DeploymentDoctor-v1.5.2/DeploymentDoctor-1.5.2.zip) |

## Two ways to use it

- **Check one item**: pick the solution, the component type and the component, click **Diagnose**. You get the most likely cause, what to do next, and every check behind it.
- **Compare whole solution**: pick the solution you deployed and compare every component between Dev and Target. Red = different or missing in Target, orange = state differs (for example a flow on in Dev but off in Target), not published in Dev, or only in Target; green = same. Click a row for the exact differences, then open that component in the doctor.

## What it can check

Forms, views, site maps, ribbons (command bars), classic workflows, business rules, actions, business process flows, cloud flows, environment variables, connection references, plug-in steps, plug-in assemblies and web resources.

## What it finds

| Cause | Applies to |
|---|---|
| Changes not published in Dev before export | forms, views, web resources |
| Component not in the solution (table added without it) | all |
| Unmanaged (Active) layer in the target environment overriding your deployment, with what it changed and when it was last changed | all |
| Another managed solution installed above yours | all |
| Staged upgrade never applied / imported as Update, so removed items stay | all |
| Flow or workflow turned off after import, connection reference without a connection, an old copy with the same name still on | processes, connection references |
| Environment variable with no value in the target | environment variables |
| Plug-in step disabled, or an older assembly version in the target | plug-in steps, assemblies |
| Form or view inactive, missing from the app, not the default; form security roles or order | forms, views |
| Script not used by any form; browser cache | web resources |
| Form, site map or ribbon XML damaged, or pointing at fields, scripts, views or tables that don't exist | forms, site maps, ribbons |

## Features

- **Two environments**: the target (where the change doesn't show) and, for the full diagnosis and Compare whole solution, Dev (the source).
- **Verdict first**: "Most likely cause" and the **next step** at the top, then every check as Problem / Warning / OK / Info.
- **"Is it really corrupted?"**: a health check with a **What was checked** list, so you can show a developer exactly what was looked at.
- **Solution layers** of the component, with your solution, layers above it and the unmanaged layer highlighted, and whether the unmanaged change is older or newer than your last deployment.
- **Readable Dev vs target comparison**: form tabs, sections and fields; view columns, filters and sort; site map areas and sub areas; ribbon buttons and commands; changed script lines; flow steps and connection references; environment variable defaults; plug-in step settings and assembly versions.
- **Guided fixes**: remove the unmanaged layer, publish in Dev, add to the Dev solution, turn a flow or workflow on, enable a plug-in step. Before anything changes, a window shows **which user it runs as**, whether it can be undone, what to check first and the manual steps; nothing runs until you tick "I have read this".
- **Shareable reports**: HTML, CSV or text, for one component or for a whole-solution compare. Full content and environment URLs are left out unless you choose them.

## What it does not do (yet)

- It never changes anything by itself: only a fix button changes something, after you confirm.
- Compare whole solution does not compare tables, columns, choices, security roles, model-driven apps or dashboards yet (they are only counted).
- It compares published content, not unpublished work in progress.
- It cannot remove the unmanaged layer of a ribbon, environment variable, connection reference or plug-in.
- It cannot tell for sure who made an unmanaged change or when it was first added: Dataverse keeps only the time of the last change.

## How to use

1. Connect XrmToolBox to the **target** environment (UAT / Prod) and open **Deployment Doctor**.
2. Open the **Dev** menu and choose **Connect Dev (source)...** (needed for Compare whole solution, and it enables the most useful checks).
3. **Check one item**: pick the solution, the component type and the component, then click **Diagnose**. Use a **Fix** button if one is offered.
   **Compare whole solution**: click it in the toolbar, pick the solution and click **Compare with Dev**.
4. Click **Export report** to share the result.

Installing, updating or installing offline: [installing XrmToolBox tools](../../docs/installing-xrmtoolbox-tools.md).

## Support

[Open an issue](https://github.com/MontarivaTechnology/Solutions/issues/new/choose) and choose **Deployment Doctor**.