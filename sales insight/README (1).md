# SalesIQ — Pro 📊

A single-file, client-side **Sales Intelligence Dashboard** with authentication (login/register), interactive charts, and full CRUD for sales records — all built in one self-contained HTML file with no backend required.

---

## ✨ Features

- **Authentication flow** — Login, Register, and Dashboard views in one page (no reloads)
  - Demo login: `admin@salesiq.com` / `123456`
  - "Remember me" and "Forgot password" (mocked) support
  - Password strength meter on registration
  - Client-side form validation with inline error messages
- **Dashboard**
  - 7 KPI stat cards: Total Revenue, Total Orders, Best Selling Product, Avg. Order Value, Total Profit, Profit Margin, Total Cost
  - 7 interactive charts (via Chart.js): monthly revenue trend, category revenue trend, category share donut, weekly sales radar, top products bar chart, monthly profit vs revenue, and profit margin by category
  - Date range filter applied across all stats/charts/table
  - Light / dark theme toggle
- **Sales record management**
  - Add new sales via modal (product, category, qty, unit price, unit cost)
  - Auto-calculated revenue, total cost, and profit per record
  - Sales records table with sorting (most recent first)
  - Export all records to CSV
  - Import records from CSV
  - Clear all data (with confirmation)

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Markup/Styling | HTML5, vanilla CSS (CSS custom properties for theming) |
| Fonts | Google Fonts — Syne (headings), DM Sans (body) |
| Charts | [Chart.js 4.4.1](https://www.chartjs.org/) (via CDN) |
| Logic | Vanilla JavaScript (ES5-style, no build step, no frameworks) |
| Storage | Browser `localStorage` |

No package manager, bundler, or server is required — it's a single `.html` file.

---

## 🚀 Getting Started

1. Download the HTML file (e.g. `salesiq.html`).
2. Open it directly in any modern browser (Chrome, Firefox, Edge, Safari).
3. Log in with the demo account, or click **Create one →** to register a new account.

```
admin@salesiq.com
123456
```

No installation, server, or internet connection is required to run the app (aside from loading the Google Fonts and Chart.js CDN scripts on first load).

---

## 📂 Project Structure

Everything lives in a single file:

```
salesiq.html
├── <style>   — All CSS (dark/light theme via [data-theme])
├── <body>
│   ├── #pageLogin       — Login page
│   ├── #pageRegister    — Registration page
│   ├── #pageDashboard   — Main dashboard (stats, charts, table)
│   └── #addSaleModal    — "Add Sale" modal dialog
└── <script>  — App logic (auth, charts, CRUD, import/export)
```

---

## 💾 Data & Storage

All data is stored in the browser's `localStorage` — **nothing is sent to a server**. This means data is per-browser/per-device and will be lost if browser storage is cleared.

| Key | Purpose |
|---|---|
| `salesiq_users` | Registered user accounts (name, email, password — stored in plaintext) |
| `salesiq_session` | Currently logged-in user session |
| `salesiq_data` | All sales records |
| `salesiq_remember` | Remembered email for "Remember me" |

### Sales record shape

```json
{
  "id": 1234567890,
  "date": "2026-09-01",
  "product": "iPhone 15 Pro",
  "category": "Electronics",
  "qty": 2,
  "unitPrice": 999.00,
  "unitCost": 700.00,
  "revenue": 1998.00,
  "totalCost": 1400.00,
  "profit": 598.00
}
```

### CSV import format

Headers required (case-insensitive): `Date, Product, Category, QTY, Unit Price` (with optional `Unit Cost`).

```csv
Date,Product,Category,QTY,Unit Price,Unit Cost
2026-01-15,iPhone 15 Pro,Electronics,2,999.00,700.00
```

---

## ⚠️ Known Limitations

- **Not production-secure**: passwords are stored in plaintext in `localStorage`. This is a front-end demo/prototype, not suitable for real user data without a proper backend and authentication service.
- **No multi-device sync**: data is local to a single browser.
- **XML/SQL import** is not actually implemented — the import button only parses CSV; other formats show an alert asking the user to convert to CSV first.
- All calculations (revenue, cost, profit, margin) are computed client-side from the data currently in `localStorage`.

---

## 🗺️ Possible Future Improvements

- Replace `localStorage` with a real backend (e.g. Node/Express + database) and hash passwords
- Add real XML/SQL import parsing
- Add per-user data isolation (currently all sales data is shared regardless of which account is logged in)
- Add pagination/search/sort to the sales records table
- Add edit/delete actions for individual sales records

---

## 📄 License

© 2026 SalesIQ. All rights reserved. (Update this section with your actual license before distributing.)
