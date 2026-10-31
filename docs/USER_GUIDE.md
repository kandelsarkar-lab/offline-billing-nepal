# User Guide

This guide explains how to set up and use **Offline Billing Nepal** for a kirana shop, hotel, restaurant, office, company or service business. The app is a single `index.html` file. It works without internet and stores data in your browser.

> **Before you start:** the app stores data only in the browser on the current device. Export a JSON backup regularly. See [Backup and restore](#backup-and-restore).

## Contents

1. [Getting started](#getting-started)
2. [A tour of the interface](#a-tour-of-the-interface)
3. [Set up your business](#set-up-your-business)
4. [Add products and services](#add-products-and-services)
5. [Add customers and suppliers](#add-customers-and-suppliers)
6. [Create a bill](#create-a-bill)
7. [Manage invoices and payments](#manage-invoices-and-payments)
8. [Record purchases](#record-purchases)
9. [Check reports](#check-reports)
10. [Print or save a PDF](#print-or-save-a-pdf)
11. [Backup and restore](#backup-and-restore)
12. [Demo data and reset](#demo-data-and-reset)
13. [Examples for different businesses](#examples-for-different-businesses)
14. [Troubleshooting](#troubleshooting)
15. [Glossary](#glossary)
16. [Important notes on VAT and legal compliance](#important-notes-on-vat-and-legal-compliance)

---

## Getting started

### Option 1: Open the file directly

1. Download or clone the repository.
2. Find `index.html`.
3. Double-click it, or right-click and choose **Open with → Chrome / Edge / Firefox / Safari**.

The app runs from `file://` and does not need a server. Data is saved in that browser's local storage for that file location.

### Option 2: Use GitHub Pages

If the repository owner has enabled GitHub Pages:

1. Open the Pages URL in a browser.
2. Bookmark it for daily use.
3. Keep using the same browser and the same URL so your data stays available.

### Option 3: Run a local server

This is optional and useful if a browser restricts local files:

```bash
cd offline-billing-nepal
python3 -m http.server 8080
```

Open <http://localhost:8080>.

### First run

On the first run, the app shows a short welcome dialog. You can:

- **Load demo data** to explore the app with sample products and invoices, or
- **Start fresh** and enter your own business details.

You can load demo data later from **Settings → Load demo data**.

---

## A tour of the interface

The left sidebar (or the menu button on mobile) contains:

| Page | What it is for |
| --- | --- |
| **Dashboard** | Today's sales, this month's sales, outstanding balance, stock value, low-stock items and recent invoices. |
| **New Bill** | Create a VAT bill, PAN bill or estimate. |
| **Invoices** | Search, filter, view, print, record payments and delete invoices. |
| **Inventory** | Products, services, stock levels, stock in, adjustments and stock history. |
| **Purchases** | Record stock bought from suppliers, including VAT. |
| **Customers** | Customers and suppliers with contact and PAN/VAT details. |
| **Reports** | Sales, VAT, profit, top products, daily sales and CSV exports. |
| **Settings** | Business profile, invoice preferences, backup, restore and reset. |

The top bar shows today's AD and BS dates and a **New Bill** shortcut.

---

## Set up your business

Open **Settings** and complete the **Business profile**:

| Field | What to enter |
| --- | --- |
| **Business name** | The name printed on invoices. Required. |
| **Tagline** | A short line such as `Kirana & General Store`. |
| **Address** | Street, city and district. |
| **Phone / Email** | Contact details for the invoice. |
| **PAN No.** | Your business PAN. |
| **VAT No.** | Your VAT registration number, if registered. |
| **Invoice prefix** | Defaults to `INV`. Use a short prefix such as `KIR`, `HTL` or `OFF`. |
| **VAT rate (%)** | Defaults to `13`. Change only if your situation requires it. |
| **Currency symbol** | Defaults to `Rs.`. |
| **Default print size** | A4 invoice or thermal 80 mm. |
| **Bank / payment details** | eSewa, Khalti, bank account or QR instructions. |
| **Terms & conditions** | Printed near the bottom of the invoice. |
| **Footer note** | A thank-you message or return policy. |
| **Show BS dates** | Print Bikram Sambat dates alongside AD dates. |

Click **Save settings**.

### Add a logo

In **Settings**, choose a PNG, JPG or WebP image under the logo preview. The app resizes it and stores it on the device. Click **Remove logo** to delete it.

> A very large logo can make the saved data bigger. Use a simple logo under a few hundred kilobytes.

---

## Add products and services

Go to **Inventory → Add product**.

### Product fields

| Field | Notes |
| --- | --- |
| **Product / service name** | Required. For example, `Basmati Rice 25kg`. |
| **SKU / code** | Optional code for search and stock records. |
| **Category** | Optional group such as `Grocery`, `Food`, `Stationery` or `Room`. |
| **Unit** | `pcs`, `kg`, `ltr`, `plate`, `hour`, `service`, etc. |
| **Purchase cost** | What you pay per unit. Used for profit estimates and stock value. |
| **Selling price** | Default rate when adding the item to a bill. |
| **Stock quantity** | Current quantity on hand. |
| **Low stock alert at** | Show a warning when stock reaches this level. |
| **Apply VAT** | Whether VAT is added to this item on a VAT bill. |
| **Track stock** | Turn off for services, room rent, tuition, repairs, etc. |

### Three ways stock can change

1. **Stock in** — use for opening stock, a return from a customer, or a simple correction. You can also update the cost per unit.
2. **Adjust** — use for damage, expiry, theft, or a physical stock count. Choose **Add stock (+)** or **Remove stock (−)** and enter a reason.
3. **Purchases** — use when you buy stock from a supplier. This records the supplier bill number, VAT and weighted-average cost.

Use **History** on a product row to see sales, purchases and adjustments in one place.

### Services

For a service:

- turn **Track stock** off,
- choose a unit such as `service` or `hour`,
- set the selling price.

Selling a service does not change stock.

### Low stock

The dashboard and inventory page show items at or below the low-stock level. Click **Restock** on the dashboard or **Stock in** in inventory to add stock.

---

## Add customers and suppliers

Go to **Customers**.

Use the **Customers** and **Suppliers** tabs to switch between them.

For each contact you can store:

- name,
- phone,
- address,
- PAN number,
- VAT number.

Customers appear in the **Saved customer** dropdown while billing. Suppliers appear in the **Supplier** dropdown on the Purchases page.

You can still create a bill for a walk-in customer without saving them. The invoice will show `Walk-in Customer`.

> Deleting a contact does not change existing invoices. Those invoices keep the name and details that were saved with them.

---

## Create a bill

Go to **New Bill**.

### Step 1: Choose the bill type

| Type | VAT | Stock |
| --- | --- | --- |
| **VAT Bill** | Adds VAT to taxable items. | Deducted when saved. |
| **PAN Bill** | No VAT. | Deducted when saved. |
| **Estimate** | No VAT. | Not deducted. |

An estimate is a quotation. It is saved in the invoice list with the status **Estimate** and is excluded from sales and VAT reports.

### Step 2: Check the invoice number and date

The invoice number is generated from:

```text
<prefix>-<BS fiscal year>-<counter>
```

For example:

```text
INV-2083-84-0001
```

The number is based on the invoice date. The BS fiscal year runs from Shrawan 1. The app shows the BS date under the AD date field.

You can change the invoice date. The due date is optional.

### Step 3: Choose or enter the customer

- Pick a saved customer from the dropdown, or
- leave it as **Walk-in / Cash customer** and type a name, phone, PAN/VAT and address.

The customer details are copied onto the invoice.

### Step 4: Add items

1. Select a product or service.
2. Enter the quantity.
3. Check the rate. It is filled from the selling price, but you can change it.
4. Enter a discount percentage if needed.
5. Click **Add**.

You can edit the quantity, rate and discount directly in the item table. The totals update immediately.

For a tracked product, the app will not let you add more than the available stock. For services and untracked items, there is no stock limit.

### Step 5: Review the summary

The summary shows:

- subtotal,
- discount,
- taxable amount,
- VAT,
- grand total,
- balance due,
- change to return.

Enter the **Amount received**. Click **Mark as fully paid** to fill the full total automatically. A partial amount creates a **Partial** invoice; zero received creates an **Unpaid** invoice.

Choose a **Payment method**: Cash, Card, eSewa, Khalti, Bank Transfer, Credit or Other.

Add an optional note or remark.

### Step 6: Save

- **Save & print** saves the invoice, deducts stock and opens the print dialog for an A4 invoice.
- **Save invoice** saves it and opens the invoice preview without automatically printing.
- **Clear** empties the current bill draft.

After saving, the invoice preview lets you print A4, print a thermal 80 mm receipt, or close.

### What happens to stock

For VAT and PAN bills, each tracked product's stock is reduced by the quantity sold. Estimates do not change stock.

If you delete an invoice later, the stock is added back automatically.

---

## Manage invoices and payments

Go to **Invoices**.

### Search and filter

Use the search box to find an invoice by:

- invoice number,
- customer name,
- phone,
- PAN or VAT number.

Filter by **type** (VAT, PAN, estimate) or **status** (paid, partial, unpaid, estimate).

### View and print

Click **View** to open the invoice preview. From there you can print A4 or thermal.

### Record a payment

Click **Pay** on an unpaid or partially paid invoice. Enter the amount received now and choose the method. The app updates:

- amount received,
- balance due,
- change,
- status.

### Delete an invoice

Click the trash icon. Confirm the deletion. For VAT and PAN bills, stock is restored for every tracked item.

> Deleting an invoice is permanent unless you have a backup. Consider exporting a backup before cleaning up old records.

### Export sales CSV

Click **Export CSV** to download a sales list for the current invoice list. The file can be opened in Excel, LibreOffice or Google Sheets.

---

## Record purchases

Go to **Purchases → New purchase**.

1. Choose a supplier, or leave it as **Cash / unregistered supplier**.
2. Check the purchase date and enter the supplier's bill number if available.
3. Tick **Include VAT** if the supplier charged VAT.
4. Select a product, enter the quantity and cost per unit, and click **Add**.
5. Review the subtotal, VAT and total.
6. Click **Save purchase**.

When saved:

- stock is added for tracked products,
- the weighted-average purchase cost is updated,
- input VAT is recorded for reports.

### Viewing and deleting purchases

Click **View** to see the purchase details.

Deleting a purchase removes the stock that the purchase added. If some of that stock has already been sold, the app may refuse to delete the purchase. This prevents negative stock.

> Use **Stock in** for opening stock or simple corrections. Use **Purchases** when you want a supplier, bill number and input VAT record.

---

## Check reports

Go to **Reports**.

Choose a preset or a custom **From** and **To** date. Presets include this month, last month, this fiscal year and all time.

The report shows:

- **Sales** — number of invoices, taxable amount and total including VAT.
- **Output VAT** — VAT charged on VAT bills.
- **Input VAT** — VAT recorded on purchases.
- **Net VAT** — output VAT minus input VAT. A negative figure is a credit.
- **Estimated gross profit** — sales excluding VAT minus the cost of items sold.
- **Top products** — by sales value.
- **Sales by day** — daily totals.
- **Stock value** — at cost and at retail.

### Export reports

- **Sales CSV** — invoice-level sales data.
- **VAT CSV** — output VAT, input VAT and a summary row.
- **Stock CSV** — product stock, cost and retail value.

Open CSV files in a spreadsheet. Check that your spreadsheet uses UTF-8 so Nepali text displays correctly.

### Print a report

Click **Print report** for a clean A4 layout. Use the browser's **Save as PDF** option if you need a digital copy.

> The VAT report is a working aid, not a filed return. Verify the figures with your accountant and the IRD before filing.

---

## Print or save a PDF

### A4 invoice

1. Open an invoice and click **Print A4**.
2. In the browser print dialog, choose a printer or **Save as PDF**.
3. Select **A4** paper.
4. Enable **Background graphics** if you want shaded table headers.
5. Use default or minimum margins.

### Thermal 80 mm

1. Open an invoice and click **Thermal 80mm**.
2. Choose the receipt printer.
3. Set paper width to **80 mm** or the roll width supported by the printer.
4. Disable browser headers and footers.
5. Set margins to **None** or **Minimum**.

If the receipt is cut off, reduce the scale in the print dialog or choose **Fit to page**.

### Print quality tips

- Use the same browser for consistent results.
- Install the printer driver before printing.
- For PDFs, choose **Save as PDF** rather than a screenshot.
- Keep the invoice preview open until printing finishes.

---

## Backup and restore

### Why backup matters

All data is stored in the browser's `localStorage`. It is not in a server or cloud account. Data can be lost if you:

- clear browsing data,
- use private/incognito mode,
- reset the browser or device,
- change to a different browser,
- open the app from a different URL or file location,
- uninstall the browser.

### Export a backup

1. Go to **Settings → Backup & restore**.
2. Click **Export backup (.json)**.
3. Save the file somewhere safe, such as a USB drive or your own cloud storage.

The backup includes settings, products, parties, invoices, purchases and stock adjustments.

### Restore a backup

1. Go to **Settings → Backup & restore**.
2. Click **Import backup**.
3. Select the JSON file.
4. Confirm the replacement.

Importing replaces the current data in that browser. Export the current data first if you might need it.

### Recommended routine

- Export a backup at the end of each day or week.
- Keep at least two copies in different places.
- Before updating the app, export a backup.
- Before resetting the browser or changing computers, export a backup.
- Test a restore on a spare browser occasionally so you know the backup works.

---

## Demo data and reset

### Load demo data

Go to **Settings → Load demo data**. This replaces the current data with sample products, customers, invoices and purchases. It is useful for training or for trying the reports.

Export your real data first if you do not want to lose it.

### Erase all data

Go to **Settings → Danger zone → Erase all data**. This removes products, invoices, purchases, customers and settings from the browser. It cannot be undone without a backup.

---

## Examples for different businesses

### Kirana / general store

- Create products such as rice, oil, sugar, soap and biscuits.
- Set units to `kg`, `ltr`, `pcs` or `pack`.
- Set low-stock alerts for fast-moving items.
- Use **Purchases** when stock arrives from the wholesaler.
- Create **VAT bills** for VAT-registered customers and **PAN bills** where appropriate.
- Check **Low stock** on the dashboard before ordering.

### Hotel / restaurant

- Create food items with units such as `plate` or `cup`.
- Create services for room rent, laundry or catering with **Track stock** off.
- Use **Stock in** for kitchen ingredients if you track them.
- Use **Purchases** for supplier bills.
- Add a footer note such as `Thank you for dining with us.`
- Print thermal receipts for the counter and A4 invoices for companies.

### Office / company

- Add services such as consulting, design, maintenance or monthly support.
- Turn **Track stock** off for services.
- Save company customers with PAN/VAT numbers.
- Use **Estimates** for quotations.
- Use **Reports → Sales CSV** for accounting.
- Print A4 invoices with bank details and terms.

### Wholesale / distribution

- Use SKU codes for each item.
- Record purchases with supplier bill numbers.
- Set low-stock alerts.
- Use **Stock adjustment** for damage or expiry.
- Filter invoices by customer and export sales CSV for reconciliation.

---

## Troubleshooting

### My data disappeared

Check that you are using:

- the same browser,
- the same device,
- the same URL or file path,
- a normal window, not private/incognito mode.

If browser data was cleared, restore your latest JSON backup. If you do not have a backup, the data cannot be recovered from the app.

### The app opens but the page is blank

- Try another modern browser.
- Open the browser console (F12 → Console) and check for errors.
- Make sure the file is complete and not a partial download.
- If you use a local server, confirm the server is still running.

### Printing is cut off

- Choose the correct paper size.
- Set margins to minimum or none.
- Reduce the scale.
- For thermal, set the paper width to 80 mm.
- Try **Save as PDF** first to check the layout.

### A product cannot be added to a bill

The quantity may be greater than the available stock. Check the stock level in **Inventory**, or receive stock first. Services with **Track stock** off do not have this limit.

### A purchase cannot be deleted

Some of the stock from that purchase may already have been sold. The app prevents deletion to avoid negative stock. Adjust stock or handle the correction another way, or restore from a backup if appropriate.

### The invoice number looks unexpected

Invoice numbers use the BS fiscal year of the invoice date and a counter. If you change the invoice date, the number can change. The counter is stored in the app data. Restoring an older backup can also restore an older counter.

### VAT figures look different from my accountant's

Check:

- the VAT rate in Settings,
- which items have **Apply VAT** enabled,
- whether the bill is a VAT bill, PAN bill or estimate,
- discounts on each line,
- the report date range,
- input VAT from purchases.

Round-off and the treatment of discounts can differ between systems. Confirm the correct method with your accountant.

### Nepali text in CSV looks broken

Open the CSV with UTF-8 encoding. In Excel, use **Data → From Text/CSV** and choose UTF-8. In LibreOffice, choose the UTF-8 filter option.

---

## Glossary

| Term | Meaning |
| --- | --- |
| **AD** | Anno Domini; the Gregorian calendar used internationally. |
| **BS** | Bikram Sambat; the Nepali calendar. |
| **Fiscal year** | In Nepal, the government fiscal year usually runs from Shrawan 1 to Ashad end. |
| **VAT** | Value Added Tax. The default rate in this app is 13%. |
| **PAN** | Permanent Account Number issued by the IRD. |
| **Output VAT** | VAT charged on sales. |
| **Input VAT** | VAT paid on purchases. |
| **Net VAT** | Output VAT minus input VAT. |
| **Estimate** | A quotation; it does not deduct stock and is excluded from sales reports. |
| **SKU** | Stock Keeping Unit; an internal product code. |
| **Weighted-average cost** | An average purchase cost updated as new purchases arrive. |

---

## Important notes on VAT and legal compliance

- This app is a general-purpose billing and inventory tool. It is **not** an IRD-certified billing system.
- Some VAT-registered businesses in Nepal are required to use IRD-approved billing software and to follow specific invoice and reporting rules.
- Tax rules, VAT rates and thresholds can change. Verify the current requirements with the **Inland Revenue Department (IRD)** and a qualified accountant.
- The reports are estimates and working aids. Do not file a return based only on this app without checking the figures.
- Keep your backups and supporting purchase bills. Good records make tax filing and audits easier.
- The software is provided under the MIT License, without warranty. See [LICENSE](../LICENSE).

---

## Need more help?

- Read the [README](../README.md) for a quick overview.
- Read the [Nepali quick guide](../README.np.md).
- Open an issue on GitHub with steps to reproduce a problem.
- Do not attach real customer data, backups or personal information to a public issue.

Made with ❤️ for Nepal.
