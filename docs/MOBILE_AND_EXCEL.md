# Mobile install, data storage and Excel/CSV import

This guide explains how to install **Offline Billing Nepal** on a phone, where the data is stored, how to back it up, and how to add products or contacts from Excel/CSV.

---

## 1. Install on a phone

The hosted app is a **Progressive Web App (PWA)**. It can be added to the home screen and opened like a normal app.

**Live app:** <https://kandelsarkar-lab.github.io/offline-billing-nepal/>

### Android — Chrome

1. Open the live app in **Chrome**.
2. Tap the **three-dot menu** (⋮).
3. Tap **Add to Home screen** or **Install app**.
4. Confirm.

### iPhone — Safari

1. Open the live app in **Safari**.
2. Tap the **Share** button.
3. Scroll down and tap **Add to Home Screen**.
4. Tap **Add**.

### After installation

- Open the app from the home screen.
- The app shell is cached by a service worker, so it works offline after the first load.
- The app still stores data in the phone's browser storage. It does not sync automatically.

### If the install button does not appear

- Make sure you opened the **HTTPS GitHub Pages URL**, not a local `file://` path.
- On Android, use Chrome. On iPhone, use Safari.
- You can also install manually with the browser menu steps above.
- Inside the app, open **Settings → Mobile app → How to install** for the same instructions.

---

## 2. Where is the data stored?

All data is stored in the browser's **localStorage** on the device.

- Products, invoices, purchases, customers, suppliers and settings are saved there.
- Nothing is uploaded to a server.
- There is no login, cloud sync or analytics.
- Data is tied to the browser and device. A different browser or phone has a separate data store.
- Clearing browser data, clearing the app data, using private/incognito mode, or uninstalling the browser can delete the data.

### Back up regularly

1. Open **Settings → Backup & restore**.
2. Tap **Export backup (.json)**.
3. Save the file in Files, Downloads, Google Drive or another safe place.

### Restore on a new phone

1. Install or open the app on the new phone.
2. Open **Settings → Backup & restore**.
3. Tap **Import backup**.
4. Select the `.json` backup file.

> The JSON backup contains everything: products, invoices, purchases, contacts and settings. Keep it private.

---

## 3. Add products from Excel/CSV

You can prepare product data in Excel, Google Sheets, LibreOffice Calc or any spreadsheet app.

### Step 1 — Download the template

Open **Inventory** and tap **Download template**.

The template has these columns:

```text
name,sku,category,unit,cost,price,stock,lowStock,vat,track
```

Example:

```csv
name,sku,category,unit,cost,price,stock,lowStock,vat,track
Basmati Rice 25kg,RICE-25,Grocery,bag,2200,2500,10,3,yes,yes
Milk 1L,MILK-1L,Dairy,pcs,90,110,24,6,yes,yes
Delivery charge,DELIVERY,Service,service,0,100,0,0,no,no
```

### Column meaning

| Column | Meaning | Example |
| --- | --- | --- |
| `name` | Product or service name. Required. | `Basmati Rice 25kg` |
| `sku` | Optional product code. Used to match existing products. | `RICE-25` |
| `category` | Optional group. | `Grocery` |
| `unit` | Unit of measure. | `pcs`, `kg`, `bag`, `service` |
| `cost` | Purchase cost per unit. | `2200` |
| `price` | Selling price per unit. | `2500` |
| `stock` | Opening/current stock quantity. | `10` |
| `lowStock` | Low-stock alert level. | `3` |
| `vat` | `yes` or `no`. Apply VAT? | `yes` |
| `track` | `yes` or `no`. Track stock? Use `no` for services. | `yes` |

### Step 2 — Save as CSV UTF-8

- In **Excel:** File → Save As → choose **CSV UTF-8 (Comma delimited) (*.csv)**.
- In **Google Sheets:** File → Download → **Comma-separated values (.csv)**.
- Do not upload `.xlsx` directly. The app reads CSV text.

### Step 3 — Import

1. Open **Inventory**.
2. Tap **Import Excel/CSV**.
3. Select the CSV file from Files/Downloads.
4. Confirm the import.

### What happens on import

- New products are added.
- Existing products are updated when the **SKU** matches, or when the **name** matches.
- If the stock quantity changes, the app records a stock adjustment in the product history.
- Products with `track = no` are treated as services and do not affect stock.
- Rows without a name are skipped.

You can also tap **Export products CSV** to download your current products, edit them in Excel, and import them again.

---

## 4. Add customers and suppliers from Excel/CSV

### Step 1 — Download the template

Open **Customers** and tap **Download template**.

Columns:

```text
type,name,phone,address,pan,vat
```

Example:

```csv
type,name,phone,address,pan,vat
customer,Ram Bahadur Thapa,9846000001,Pokhara-8 Kaski,301111111,
supplier,Himalayan Traders,061-456123,Pokhara-6 Kaski,,303333333
```

### Column meaning

| Column | Meaning | Example |
| --- | --- | --- |
| `type` | `customer` or `supplier`. | `customer` |
| `name` | Contact or business name. Required. | `Ram Bahadur Thapa` |
| `phone` | Phone or mobile number. | `9846000001` |
| `address` | City, area or full address. | `Pokhara-8, Kaski` |
| `pan` | PAN number. | `301111111` |
| `vat` | VAT number. | `303333333` |

### Step 2 — Save as CSV UTF-8

Use the same steps as above.

### Step 3 — Import

1. Open **Customers**.
2. Tap **Import Excel/CSV**.
3. Select the CSV file.
4. Confirm the import.

Existing contacts are updated when the **name and type** match. New contacts are added.

You can tap **Export contacts CSV** to download all customers and suppliers, edit them, and import them again.

---

## 5. Move data between phone and computer

### Phone to computer

1. On the phone, open **Settings → Export backup (.json)**.
2. Send the file to the computer using email, Google Drive, WhatsApp or a USB cable.
3. On the computer, open the app and use **Settings → Import backup**.

### Computer to phone

1. On the computer, open **Settings → Export backup (.json)**.
2. Send the file to the phone.
3. On the phone, open the app and use **Settings → Import backup**.

> CSV import is for products and contacts only. Use the JSON backup to move invoices, purchases, stock history and settings.

---

## 6. Clear data safely

To erase everything on a device:

1. Open **Settings → Danger zone**.
2. Tap **Erase all data**.
3. Confirm twice.

Before erasing, export a JSON backup if you might need the data later.

> Clearing the browser's site data also erases the app data. Export a backup first.

---

## 7. Troubleshooting

### CSV import says the file is invalid

- Make sure the first row has column headers.
- Make sure the file is saved as **CSV UTF-8**, not `.xlsx`.
- Make sure the product file has a `name` column and the contact file has a `name` column.
- Remove blank rows above the header.
- If using Excel, check that numbers are not formatted with unusual currency text. The app removes common symbols and commas, but plain numbers are safest.

### The imported stock is wrong

- Check the `stock` column.
- If the product already existed, the import updates it and records an adjustment.
- Use **Inventory → product history** to see the change.
- For services, set `track` to `no`.

### Install option is missing

- Use the HTTPS GitHub Pages link.
- On Android use Chrome; on iPhone use Safari.
- Open the browser menu and choose **Add to Home screen** manually.

### Data disappeared after clearing the browser

Browser storage is local. If you did not export a backup, the data cannot be recovered from a server because there is no server. Restore the last JSON backup if you have one.

---

## 8. Privacy

- No account is required.
- No data is sent to a server.
- CSV files are read locally in the browser.
- The service worker only caches the app's own files for offline use.
- Keep your JSON backups private because they contain your business and customer data.
