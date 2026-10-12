# Installing a managed solution

All PCF controls in this repository come as **managed solutions** (`Mrt<Product>_managed.zip`), published by **Montariva Technology** (prefix `mrt`). The steps are the same for every product.

## Before you start

- You need the **System Administrator** or **System Customizer** role in the environment.
- Try it in a **development or test environment** first, then move it to production.
- Download the zip from the product page or the [Releases page](https://github.com/MontarivaTechnology/Solutions/releases). Don't unzip it.

## Import

1. Go to [make.powerapps.com](https://make.powerapps.com) and check the **environment** at the top right.
2. **Solutions** > **Import solution** > **Browse** > pick the `.zip` > **Next**.
3. Check the details and click **Import**.
4. Wait for "Solution imported successfully" (about a minute).

The control is now available in the form designer under **Components** > **+ Component**. Each product's guide explains how to add it to a form.

## Upgrade to a newer version

1. Download the newer zip.
2. Import it the same way. Keep the default **Upgrade** option.
3. Forms that already use the control pick up the new version on their own. Ask users to refresh the page (Ctrl+F5).

## Remove

1. First remove the control from every form that uses it (form designer > select the column > **Components** > remove the component > **Save and publish**).
2. **Solutions** > select the solution (e.g. *File Drop Zone*) > **Delete**.

Removing the solution doesn't delete any data: files and images stay as Note attachments on the records.

## Common import problems

| Message | What to do |
|---|---|
| "You don't have the privileges..." | Ask an administrator, or get the System Customizer role. |
| "This solution package contains a newer version..." vs. "older version" | You're importing an older version over a newer one. Download the latest release. |
| Import fails on a missing dependency | Check the product's requirements (e.g. the table must allow notes). |

Still stuck? [Open an issue](https://github.com/MontarivaTechnology/Solutions/issues/new/choose) with the error message.
