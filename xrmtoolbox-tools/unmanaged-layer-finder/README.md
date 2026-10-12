# Unmanaged Layer Finder

An [XrmToolBox](https://www.xrmtoolbox.com/) tool that finds **unmanaged (Active) layers** on the components of your Dataverse / Dynamics 365 solutions, and shows **what changed, when and by whom**.

| Version | Install | Offline download |
|---|---|---|
| **1.3.0** | XrmToolBox **Tool Library** > search **Unmanaged Layer Finder** > **Install** | [UnmanagedLayerFinder-1.3.0.zip](https://github.com/MontarivaTechnology/Solutions/releases/download/UnmanagedLayerFinder-v1.3.0/UnmanagedLayerFinder-1.3.0.zip) |

## Why

In a healthy ALM setup, test and production environments contain **managed** solutions only. When someone edits a component directly in one of those environments, Dataverse creates an **unmanaged (Active) layer** on top of the managed one. That layer silently overrides what your next deployment ships and is hard to find: the maker portal only shows layers one component at a time.

**Unmanaged Layer Finder scans a whole solution in one go** and tells you which components have an unmanaged layer, what was changed and who changed it.

## Features

- **Solution picker with filters**: managed / unmanaged / both, by publisher, and one click to hide Microsoft solutions.
- **Component type filter**: Forms, Views, Cloud Flows, Environment Variables and more, with per-type counts.
- **Layer stack per component**, e.g. `Active > MySolution`.
- **What changed**: the attributes touched by the unmanaged layer.
- **Who and when**: last modified by / on, plus an optional audit-log lookup.
- **Export to CSV** for reports and clean-up tracking.
- **Read-only**: the tool never changes your environment.

## How to use

1. Connect XrmToolBox to an environment and open **Unmanaged Layer Finder**.
2. Filter and pick a solution, then click **Load components**.
3. Optionally choose a **Component type**, tick **Select all**, and click **Check layers**.
4. Rows with an unmanaged layer are highlighted; tick **Show only unmanaged** to focus on them.
5. Click **Export CSV** to share the results.

Installing, updating or installing offline: [installing XrmToolBox tools](../../docs/installing-xrmtoolbox-tools.md).

## Support

[Open an issue](https://github.com/MontarivaTechnology/Solutions/issues/new/choose) and choose **Unmanaged Layer Finder**.
