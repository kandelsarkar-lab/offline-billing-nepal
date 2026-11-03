# Changelog

All notable changes to this project are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project uses [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Planned

- Nepali UI language toggle.
- Barcode/QR scanning.
- Customer credit ledger.
- Sales and purchase returns.
- Multi-store support.
- Optional encrypted backup to a location the user chooses.

## [1.1.1] - 2026-11-03

### Fixed

- Prevented clicking or dragging outside an add/edit form from accidentally closing it and losing unsaved text.
- Backdrop clicks now only close a form when the click starts and ends on the backdrop and the form has not been changed.

## [1.1.0] - 2026-11-02

### Added

- Installable mobile PWA with `manifest.webmanifest`, service worker and app icons.
- In-app **Settings → Mobile app** install button and Android/iPhone instructions.
- Offline app-shell caching after the first load.
- Product CSV template, export and bulk import.
- Customer/supplier CSV template, export and bulk import.
- Excel/Google Sheets workflow documentation and a dedicated mobile/data guide.
- CSV import records stock adjustments when imported stock differs.

### Changed

- Updated the app version label to `1.1.0`.
- Expanded README and user guide with mobile installation, storage and Excel/CSV instructions.

### Fixed

- Prevented negative stock when the same product is added to a bill more than once.
- Prevented saving a bill whose edited quantities exceed the available stock.
- Prevented negative stock when deleting a purchase that lists the same product on multiple lines.
- Blocked saving a negative stock quantity for a tracked product.
- Estimates can now include quantities above current stock, because estimates do not deduct stock.

## [1.0.0] - 2026-10-31

### Added

- Single-file, fully offline billing app for Nepal.
- **VAT bills**, **PAN bills** and **estimates / quotations**.
- Configurable VAT rate (default 13%), line discounts, partial payments and change calculation.
- Invoice numbering based on the Bikram Sambat fiscal year, with AD and BS dates.
- Amount in words using the lakh/crore numbering system.
- A4 invoice and 80 mm thermal receipt layouts with browser printing and Save as PDF.
- Business profile, logo upload, PAN/VAT numbers, bank details, terms and footer note.
- Product and service management with SKU, category, unit, cost, price, stock tracking and low-stock alerts.
- Stock in, stock adjustments and stock movement history.
- Purchases from suppliers with VAT and weighted-average cost updates.
- Customers and suppliers with phone, address, PAN and VAT numbers.
- Invoice list, search, filters, payments, deletion and automatic stock restoration.
- Dashboard with sales, low stock and recent invoices.
- Reports for sales, output VAT, input VAT, net VAT, estimated profit, top products, daily sales and stock value.
- CSV export for sales, VAT and stock.
- JSON backup, restore and demo data.
- Responsive interface for desktop, tablet and mobile.
- Embedded Bikram Sambat calendar data; no external dependencies or network requests.
- GitHub Pages deployment workflow.
- English and Nepali quick-start documentation.
