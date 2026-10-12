# Installing XrmToolBox tools

[XrmToolBox](https://www.xrmtoolbox.com/) is a free Windows application with hundreds of tools for Dataverse / Dynamics 365. Our tools run inside it.

## Install (recommended)

1. Open **XrmToolBox**.
2. Click **Tool Library** (on the Start page or in the Configuration menu).
3. Search for the tool name, for example **Deployment Doctor** or **Unmanaged Layer Finder**.
4. Tick it and click **Install**. Restart XrmToolBox if it asks.
5. Open it from the **Tools** list and connect to an environment.

## Update

When a new version is out, the **Tool Library** shows it as an update. Select the tool and click **Update**.

## Install offline (no internet on that PC)

1. On a PC with internet, download the tool's zip from its product page or the [Releases page](https://github.com/MontarivaTechnology/Solutions/releases), e.g. `DeploymentDoctor-1.0.0.zip`.
2. Close XrmToolBox on the offline PC.
3. Unzip and copy the `.dll` into XrmToolBox's **Plugins** folder:
   - installed version: `%APPDATA%\MscrmTools\XrmToolBox\Plugins\`
   - portable version: the `Plugins` folder next to `XrmToolBox.exe`
4. Right-click the `.dll` > **Properties** > tick **Unblock** if shown > **OK**.
5. Start XrmToolBox.

Offline installs don't update themselves; repeat these steps for a new version.

## Remove

**Tool Library** > select the tool > **Uninstall**, or delete its `.dll` from the Plugins folder while XrmToolBox is closed.
