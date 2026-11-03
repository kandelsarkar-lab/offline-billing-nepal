# Contributing to Billing Nepal

Thank you for helping make billing easier for small businesses in Nepal. This project is free, offline-first, and intentionally simple to run: **there is no build step and no server**.

## Ways to contribute

- **Report a bug** with clear steps to reproduce.
- **Suggest a feature** that solves a real problem for a shop, hotel, office or company.
- **Improve the Nepali text** and make labels easier to understand.
- **Test** on another browser, phone, printer or operating system.
- **Improve the documentation** or add screenshots.
- **Share** the project with a business that needs it.

## Before you start

1. Search existing issues and pull requests to avoid duplicates.
2. For a large change, open an issue first so we can agree on the approach.
3. Keep the app **fully offline**. Do not add CDNs, external fonts, analytics, trackers or network calls.
4. Keep the app **self-contained** in `index.html`. The download-and-open workflow must keep working.
5. Do not add a framework or build tool unless there is a very strong reason.

## Development

The entire application lives in `index.html`.

```bash
git clone <your-fork-url>
cd offline-billing-nepal
```

Open `index.html` directly in a browser. For a local HTTP server:

```bash
python3 -m http.server 8080
```

Then open <http://localhost:8080>.

There is no `npm install`, no bundler and no compilation step.

### Code style

- Vanilla JavaScript, HTML and CSS only.
- 2-space indentation, single quotes in JavaScript, semicolons.
- Keep the existing helper functions and rendering patterns where possible.
- Escape user-provided text before inserting it into HTML. The existing `esc()` helper should be used.
- Avoid inline event handlers in generated HTML; use the existing delegated event system.
- Keep localStorage data compatible with existing backups. If you change the schema, add a migration and bump the schema version.
- Do not remove or rename existing settings without a migration.

### Data and privacy rules

- Never send business data to a server.
- Never add third-party scripts.
- Never log customer data to the console.
- Keep backup import and export working.

## Testing checklist

Before opening a pull request, test the flows you touched. At minimum:

- [ ] App opens from `file://` without console errors.
- [ ] Dashboard loads with empty data and with demo data.
- [ ] Create a **VAT bill**; VAT and totals are correct.
- [ ] Create a **PAN bill**; no VAT is added.
- [ ] Create an **estimate**; stock is not deducted.
- [ ] Save a bill; stock is deducted.
- [ ] Delete a bill; stock is restored.
- [ ] Record a payment and check the balance.
- [ ] Add a product and use **Stock in** and **Stock adjustment**.
- [ ] Record a purchase with VAT; stock and input VAT update.
- [ ] Check reports for a date range and export CSV.
- [ ] Export a JSON backup, reset data, and import the backup.
- [ ] Print an A4 invoice and a thermal 80 mm receipt (or save as PDF).
- [ ] Test at desktop width and at a mobile width (around 390 px).
- [ ] Confirm there are no horizontal scrollbars or overlapping controls.

## Pull requests

- Keep each pull request focused on one change.
- Describe **what** changed and **why**.
- Include steps to test, and screenshots for UI changes.
- Mention any data migration or backup compatibility impact.
- Update `README.md` and `docs/USER_GUIDE.md` when behavior changes.
- Add an entry to `CHANGELOG.md` under **Unreleased**.

## Commit messages

Use clear, short messages, for example:

```text
Fix VAT rounding on discounted lines
Add low-stock filter to inventory
Update Nepali quick-start guide
```

## Reporting bugs

Please include:

- What you expected and what happened.
- Exact steps to reproduce.
- Browser, version and operating system.
- Whether the app was opened from `file://` or a web server.
- A screenshot if the issue is visual.
- Any console errors (open DevTools → Console).

**Do not attach real customer data or backups containing personal information.** Use demo data or redact the file.

## Feature ideas

Good places to help:

- Nepali UI language toggle.
- Barcode/QR scanning.
- Customer credit ledger and reminders.
- Sales returns and purchase returns.
- Multi-store or multi-counter support.
- Better thermal printer compatibility.
- More automated tests.
- Accessibility improvements.

## License

By contributing, you agree that your contributions are licensed under the **MIT License** of this project.
