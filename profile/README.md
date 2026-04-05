<div align="center">

<img src="logo.svg" alt="Schema Lens" width="80" />

# Schema Lens

**Your schema, in focus.**
*Instant ERD from the files you already write — right inside VS Code.*

[![VS Code](https://img.shields.io/badge/VS%20Code-Extension-007ACC?style=flat-square&logo=visual-studio-code&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=SangeethPromod.schema-lens)
[![License](https://img.shields.io/badge/License-AGPL--3.0-4ec9b0?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/SchemaLens/schema-lens/blob/main/CONTRIBUTING.md)
[![GitHub](https://img.shields.io/badge/GitHub-schema--lens-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/SchemaLens/schema-lens)

<br/>

> ⚠️ **Early-stage and evolving.** Expect rough edges.
> Issues and contributions welcome — see [CONTRIBUTING.md](https://github.com/SchemaLens/schema-lens/blob/main/CONTRIBUTING.md).

</div>

---

## What is Schema Lens?

Schema Lens parses your SQL migrations, Prisma schemas, Drizzle schemas, and Knex migrations and renders an interactive ERD directly inside VS Code — no database connection required.

---

## Why Schema Lens?

|  | Schema Lens | Browser-based tools | DB admin tools |
|---|:---:|:---:|:---:|
| Runs in VS Code | ✅ | ❌ | ❌ |
| No sign-up required | ✅ | ❌ | ❌ |
| Works without a live DB | ✅ | ❌ | ❌ |
| Reads code directly | ✅ | ❌ | ❌ |

---

## Features

- **Interactive ERD in VS Code** — zoom and pan in a side panel next to your editor
- **File-first support** — raw SQL (`.sql`), Prisma (`schema.prisma`), Drizzle (`pgTable`, `mysqlTable`, `sqliteTable`), Knex (`createTable`)
- **Live reload on save** — diagram refreshes automatically when you save
- **Visual diff mode** — compare two schema files and see added 🟢, removed 🔴, and modified 🟡 tables
- **Respects your VS Code theme** — light and dark mode support

---

## Supported Formats

| Format | File Pattern | Parser Approach |
|---|---|---|
| Raw SQL | `*.sql` | `node-sql-parser` for `CREATE`, `ALTER`, `FOREIGN KEY` |
| Prisma | `schema.prisma` | Line-based parser for `model`, fields, `@relation` |
| Drizzle | `*.ts` with `pgTable` / `mysqlTable` / `sqliteTable` | TypeScript AST walk |
| Knex.js | `*.ts` with `createTable` | TypeScript AST walk |

---

## Installation

Install directly from the VS Code Marketplace:

1. Open VS Code and go to **Extensions** (`Ctrl+Shift+X`)
2. Search for **Schema Lens**
3. Click **Install**

Or install via the [VS Code Marketplace page](https://marketplace.visualstudio.com/items?itemName=SangeethPromod.schema-lens).

---

## Usage

1. Open a supported schema file (`*.sql`, `schema.prisma`, or a Drizzle/Knex `.ts` file)
2. Click the **Schema Lens icon** in the top-right of the editor title bar, or run **Schema Lens: Open ERD** from the Command Palette (`Ctrl+Shift+P`)
3. The ERD opens in a side panel next to your code
4. **Zoom** with the scroll wheel, **pan** by clicking and dragging
5. Save the file to refresh the diagram with your latest changes

### Diff Mode

1. Open a schema file
2. Run **Schema Lens: Compare With…** from the Command Palette
3. Select a second schema file to compare
4. A diff ERD opens showing added 🟢, removed 🔴, and modified 🟡 tables

---

## Limitations

- **SQL dialect coverage** — targets PostgreSQL and MySQL; vendor-specific syntax (e.g., SQL Server `IDENTITY`) may not parse cleanly
- **Drizzle and Knex detection** — for `.ts` files, format is auto-detected from imports and function calls; if a file mixes both patterns, Drizzle is preferred
- **Prisma enums** — `enum` blocks are currently ignored and do not appear in the ERD
- **Views and procedures** — not parsed or shown
- **Very large schemas** — diagrams with more than ~50 tables can feel heavy; use zoom and pan to navigate

---

## Contributing

See [CONTRIBUTING.md](https://github.com/SchemaLens/schema-lens/blob/main/CONTRIBUTING.md) for the process, governance, and development setup. All pull requests require maintainer approval — please open an issue first for any non-trivial work.

Contributions are licensed under AGPL-3.0.

---

## License

Licensed under the [GNU Affero General Public License v3.0](LICENSE).  
Copyright (C) 2026 Sangeeth Promod.

---

<div align="center">

**Built for execution. No fluff.**

<img src="logo.svg" width="20" /> By Sangeeth Promod

</div>
