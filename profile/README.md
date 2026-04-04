
---

## ✦ Why Schema Lens?

|  | Schema Lens | Browser-based tools | DB admin tools |
|---|:---:|:---:|:---:|
| Runs in VS Code | ✅ | ❌ | ❌ |
| No sign-up required | ✅ | ❌ | ❌ |
| Works without a live DB | ✅ | ❌ | ❌ |
| Reads code directly | ✅ | ❌ | ❌ |
| Fully offline | ✅ | ❌ | ❌ |[file:2]

Schema Lens targets quick visualization from files already open in your editor.[file:2]

## ⚡ Features

- **Interactive ERD in VS Code** — zoom, pan in a side panel.
- **File-first support** — raw SQL (`.sql`), Prisma (`schema.prisma`), Drizzle (`pgTable` etc.), Knex (`createTable`).
- **Live reload on save** — diagram updates automatically.
- **Visual diff mode** — compare schemas (added 🟢, removed 🔴, modified 🟡).
- **Respects VS Code theme** — light/dark mode support.[file:2]

---

## 📋 Supported Formats

| Format     | File Pattern                    | Parser Approach                          |
|------------|---------------------------------|------------------------------------------|
| Raw SQL    | `*.sql`                         | `node-sql-parser` for CREATE/ALTER/FK    |
| Prisma     | `schema.prisma`                 | Line-based for models/fields/@relation   |
| Drizzle    | `*.ts` with pg/mysql/sqliteTable| TypeScript AST walk                      |
| Knex.js    | `*.ts` with `createTable`       | TypeScript AST walk                      |[file:2]

---

## 🚀 Installation

### From VSIX

1. Download `.vsix` from [Releases](https://github.com/schema-lens/schema-lens/releases).[file:2]
2. In VS Code Extensions (`…` menu) > **Install from VSIX…**.
3. Select file and install.[file:2]

### From Marketplace (when available)

1. `Ctrl+Shift+X` > Search **Schema Lens** > Install.[file:2]

---

## 🎯 Usage

1. Open supported file (e.g., `*.sql`, `schema.prisma`).
2. Click **≋ ERD** in editor title bar or `Ctrl+Shift+P` > **Schema Lens: Open ERD**.
3. Zoom with scroll, pan by drag. Save file to refresh.[file:2]

### Diff Mode

1. Open schema file.
2. `Ctrl+Shift+P` > **Schema Lens: Compare With…**.
3. Select second file for visual diff.[file:2]

---

## 🗺️ Limitations

- SQL: PostgreSQL/MySQL focus; vendor specifics may fail.
- Drizzle/Knex: Auto-detects; Drizzle preferred if mixed.
- Ignores Prisma enums, views, procedures.
- Large schemas (>50 tables): Use zoom/pan.[file:2]

## 🤝 Contributing

See [CONTRIBUTING-3.md](CONTRIBUTING-3.md) for process, governance, and dev setup. Maintainer approves all PRs; open issues first for non-trivial work.[file:3]

Contributions licensed under AGPL-3.0.[file:1][file:3]

---

## 📜 License

Licensed under [GNU Affero General Public License v3.0](LICENSE). Copyright (C) 2026 Sangeeth Promod.[file:1][file:2]

See LICENSE for full terms.[file:1]

---

<div align="center">

**Built for execution. No fluff.**

<img src="logo.svg" width="20" /> By Sangeeth Promod — Westbridge & Co.

</div>
