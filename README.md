# GST Billing

A free, no-inventory GST invoicing app that works as an installable PWA. Built as a plain HTML, CSS and JavaScript site, so there is nothing to compile.

## Features
- Business profile, GST registration type (Regular, Composition, Not registered), price levels
- Customers: business name, contact person, billing and shipping address, optional GSTIN with validity check, default price level, notes
- Products: brand, variant, category, SKU, weight, pieces per pack, packs per box, pieces per box, MRP, price per level (tax inclusive), active flag, search and filters, CSV import and export
- Invoices with CGST+SGST or IGST by place of supply, optional GST (bill of supply), tax inclusive or exclusive rates, discounts, round-off, amount in words, financial-year numbering (2026-27/001)
- Credit notes numbered CN/2026-27/001, linked to the original invoice
- Payments (paid, partial, unpaid), cancel invoice
- Print or save as PDF, WhatsApp share link
- Monthly GST report with credit notes subtracted, CSV for your CA

## Files
| File | What it is |
| --- | --- |
| `index.html` | Page shell |
| `styles.css` | All styling (change colours and fonts here) |
| `app.js` | All app logic |
| `manifest.webmanifest`, `icons/` | PWA install details and icons |
| `sw.js` | Offline cache. Change `CACHE` to a new name after every edit |
| `netlify.toml` | Netlify settings |

## Run locally
```
python3 -m http.server 8080
```
Open http://localhost:8080. (Opening `index.html` directly works too, but install and offline need http.)

## Deploy free
**Netlify:** drag this folder onto https://app.netlify.com/drop, or connect the GitHub repo (no build command, publish directory `.`).

**GitHub Pages:** push the repo, then Settings, Pages, deploy from branch `main`, folder `/ (root)`. The app uses relative paths, so it works under `username.github.io/repo-name/`.

## Push to GitHub
```
git init
git add .
git commit -m "GST billing app"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

## Important: where data lives
Data is stored in this browser only (localStorage). It does not sync between devices, and clearing browser data erases it. Use Settings, Backup to copy your data out regularly.

## Roadmap
1. Supabase login and cloud sync (so data is available on every device)
2. Bluetooth thermal receipt printing
3. GSTIN lookup of name and address (needs a paid GST verification API behind a small server function)
4. Purchase and expense log for input tax credit
5. e-Invoice and e-way bill (only above the turnover limit)

## GST notes
Check one printed invoice with your CA before real use. The app does not check HSN digit length, cess, or e-invoice rules.
