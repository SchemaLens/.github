<div align="center">
```
 ___      _                          _
/ __| ___| |_  ___ _ __  __ _   | |  ___ _ _  ___
\__ \/ __| ' \/ -_) '  \/ _` |  | |_/ -_) ' \(_-<
|___/\___|_||_\___|_|_|_\__,_|  |____\___|_||_/__/
```
Your schema, in focus.
Instant ERD from the files you already write — right inside VS Code.

Show Image
Show Image
Show Image
Show Image
Show Image
Show Image
<br/>

⚠️ Early-stage, vibe-coded, and evolving. Expect rough edges.
PRs and issues are very welcome — this is built in public.

</div>

≋ What is Schema Lens?
You know that moment when you're three files deep into a migration and you can no longer remember how orders relates to line_items without grep-ing through five files? Yeah. That's why this exists.
Schema Lens is a VS Code extension that reads your schema and migration files and renders an interactive ERD in a side panel. No browser tab. No SaaS login. No database connection. Just click ≋ View ERD and see your schema.
  You have this:              Schema Lens gives you this:

  schema.prisma               ┌─────────────┐     ┌─────────────┐
  migrations/001.sql    ───▶  │  users      │────▶│  posts      │
  drizzle/schema.ts           │  PK id      │     │  PK id      │
                              │  email      │     │  FK author  │
                              │  name       │     │  title      │
                              └─────────────┘     └─────────────┘

✦ Why not just use [existing tool]?
Fair question. There are great ERD tools out there. Here's the honest comparison:
Schema LensBrowser-based toolsDB admin toolsRuns in VS Code✅❌❌No sign-up required✅mostly ❌❌Works without a live DB✅sometimes❌Reads code directly✅upload/paste❌Zero external service✅❌❌Feature-complete modeling suite❌✅✅
Schema Lens isn't trying to replace those tools. It's the thing you reach for when you already have a migration file open and just want to see it, fast.

⚡ Features

≋ ERD on demand — click one button in the editor title bar, get a diagram
Interactive canvas — zoom, pan, drag nodes, hover columns for details
Multi-format parsing — Prisma, Drizzle, Knex, and raw SQL (coverage growing)
Fully offline — nothing leaves your machine
Zero config to start — open a supported file, click the button, done
Schema diff (planned) — compare two migrations visually

<details>
<summary><strong>📋 Supported formats (click to expand)</strong></summary>
<br/>
FormatFile patternsStatusRaw SQL*.sql, migrations/*.sql✅ WorkingPrismaschema.prisma✅ WorkingDrizzle ORM*.ts with pgTable / mysqlTable✅ WorkingKnex migrations*.ts with knex.schema.createTable✅ WorkingTypeORM*.entity.ts🔜 PlannedSequelize*.model.ts🔜 Planned
Missing your stack? Open an issue — parser contributions are especially welcome.
</details>

🚀 Installation

Not on the marketplace yet? Skip to the .vsix instructions below.

Option A — VS Code Marketplace:

Open VS Code
Hit Ctrl+Shift+X (or Cmd+Shift+X)
Search Schema Lens
Click Install

Option B — Install from .vsix:
bashcode --install-extension schema-lens-x.y.z.vsix
Option C — Clone and run locally:
bashgit clone https://github.com/yourusername/schema-lens
cd schema-lens
npm install
# Press F5 in VS Code to launch the Extension Development Host

🎯 Usage

Open a folder containing your schema or migration files
Open any supported file (schema.prisma, *.sql, etc.)
Click ≋ View ERD in the editor title bar
— or run Schema Lens: Open ERD from the Command Palette (Ctrl+Shift+P)
The ERD panel opens to the side. Explore away.

  ┌──────────────────────────────────────────┐
  │  westbridge-api › migrations › schema.sql │  ← breadcrumb
  │                                  [≋ ERD]  │  ← click this
  ├──────────────────────────────────────────┤
  │  CREATE TABLE users (                     │
  │    id   SERIAL PRIMARY KEY,               │
  │    email VARCHAR(255) UNIQUE NOT NULL      │
  │  );                                       │
  └──────────────────────────────────────────┘
<details>
<summary><strong>⚙️ Configuration options (click to expand)</strong></summary>
<br/>
Configuration lives in your VS Code settings.json. Options are evolving — check the extension settings panel for the latest.
jsonc{
  // Paths to scan for schema/migration files
  "schemaLens.includePaths": ["./migrations", "./src/db"],

  // Explicitly set the parser (auto-detected by default)
  "schemaLens.parser": "auto", // "prisma" | "drizzle" | "knex" | "sql" | "auto"

  // How many tables to show before paginating the ERD
  "schemaLens.maxTablesPerView": 20
}
</details>

🗺️ Roadmap
This is tracked properly in GitHub Issues and the project board, but here's the high-level picture:
Near-term (rough priority order):

 TypeORM entity parser
 Schema diff between two files / commits
 Keyboard shortcuts for zoom and navigation
 Configurable themes (light mode, custom colors)

Medium-term:

 Jump-to-definition from ERD column → source file
 Better layout engine for large schemas (>20 tables)
 Multi-root workspace support

Longer-term / exploratory:

 GitHub Action to generate ERD PNGs on schema change
 Optional team diff viewer (potential paid add-on)

Have an idea? Open a discussion rather than an issue if it's exploratory.

🤝 Contributing
Contributions are welcome — especially:

🐛 Bug reports with clear repro steps
🔌 New parsers for schema/migration formats not yet supported
⚡ ERD performance or layout improvements
📖 Docs, examples, and config samples

Before opening a PR:

Check existing issues first
Open an issue describing what you want to change
Keep changes focused and minimal

By contributing, you agree your work is licensed under the same terms as the project.
<details>
<summary><strong>🛠️ Dev setup (click to expand)</strong></summary>
<br/>
```bash
git clone https://github.com/yourusername/schema-lens
cd schema-lens
npm install
Run tests
npm test
Build the extension
npm run build
Package as .vsix
npm run package

Press **F5** in VS Code to open an Extension Development Host with Schema Lens loaded.

The main modules:
src/
extension.ts       ← entry point, command registration
parsers/           ← one file per format (sql, prisma, drizzle, knex)
renderer/          ← webview HTML + ERD canvas logic
diff/              ← schema diff engine

</details>

---

## ⭐ Star History

If Schema Lens saves you even one "wait, what was that foreign key again?" moment — a star helps a lot. It makes the project more visible and keeps the motivation to ship.

[![Star History Chart](https://api.star-history.com/svg?repos=yourusername/schema-lens&type=Date&theme=dark)](https://star-history.com/#yourusername/schema-lens&Date)

> Replace `yourusername` with your GitHub username for the star chart to work.

---

## 📜 License

Schema Lens is **source-available under the [PolyForm Noncommercial 1.0.0](./LICENSE) license**.

**TL;DR:**

| Use case | Allowed? |
|---|---|
| Personal projects | ✅ Yes |
| Learning, studying the code | ✅ Yes |
| Open source projects (noncommercial) | ✅ Yes |
| Commercial products or services | ❌ Requires a separate license |
| SaaS built on top of Schema Lens | ❌ Requires a separate license |

This is intentionally *not* an OSI "open source" license — commercial use needs a separate agreement. This keeps the code public and accessible for personal use while letting me build something sustainable around it.

**For commercial licensing:** reach out via [email / website — add yours here].

<details>
<summary><strong>🤔 Why PolyForm NC and not MIT?</strong></summary>

<br/>

The short version: I want the code to be readable, learnable, and usable for personal tooling without friction — but I also want the option to build something commercial around it without someone immediately wrapping it in a SaaS and undercutting it.

PolyForm Noncommercial is a clean, well-scoped license that achieves this. It's not hostile to individual developers or open source projects. If you're unsure whether your use case qualifies, just ask.

</details>

---

## ⚠️ Disclaimer

Schema Lens is provided **"as is"** — no warranties, no guarantees, no SLA. Use it at your own risk, especially in production or critical environments.

This README may lag behind the actual implementation. Treat it as a best-effort description, not a formal spec. When in doubt, read the source.

---

## 📬 Contact

| For what | Where |
|---|---|
| Bugs and feature requests | [GitHub Issues](../../issues) |
| Ideas and discussion | [GitHub Discussions](../../discussions) |
| Commercial licensing | [your@email.com — update this] |
| Just want to say hi | Same as above, that's fine |

---

<div align="center">

**Built in public · Vibe-coded with care · PRs welcome**

*If this saved you a grep, consider leaving a ⭐*

<br/>

Made with ☕ by [Your Name](https://github.com/yourusername)

</div>
