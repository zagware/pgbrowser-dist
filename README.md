# pgbrowser

A **k9s-style terminal UI** for browsing PostgreSQL clusters. Navigate databases, schemas, tables, and data with keyboard-driven drill-down — no GUI required.

Inspired by [k9s](https://k9scli.io/) for Kubernetes, pgbrowser brings the same hierarchical browsing experience to PostgreSQL.

## Features

- **Split-panel layout** — left panel lists items, right panel shows a live preview that updates as you move the cursor
- **Hierarchical navigation** — browse Databases > Schemas > Tables with Enter/Esc drill-down
- **Live preview** — schema-level shows tables preview, table-level shows columns/indexes/data tabs
- **Cluster-wide query** — run read-only SQL across every database in the cluster from the databases view, with results in a combined table showing a `database` column
- **SQL query panel** — built-in query editor at the table level with results table (`Ctrl+E` to execute)
- **Panel focus cycling** — `Tab` moves focus between left panel, detail tabs, query input, and query results
- **Breadcrumb trail** — always know where you are in the cluster hierarchy
- **Live fuzzy filtering** — press `/` to filter whichever panel has focus
- **Command mode** — press `:` to jump directly to a resource level (`:databases`, `:schemas`)
- **Table detail tabs** — view Columns, Indexes, and Sample Data (first 50 rows) with `[`/`]` tab switching
- **Estimated row counts** — fast row count estimates (no full table scans)
- **Keyboard-driven** — vim-style `j`/`k` navigation, no mouse required
- **Fast startup** — single binary, connects and renders in under a second
- **Cross-platform** — macOS (Intel + Apple Silicon), Linux (amd64 + arm64), Windows

## Installation

### Homebrew (macOS / Linux)

```bash
brew tap zagware/tap
brew install pgbrowser
```

### Manual Download

Download the latest binary for your platform from the [Releases](https://github.com/zagware/pgbrowser-dist/releases) page.

#### macOS / Linux

```bash
# Extract and move to your PATH
tar -xzf pgbrowser_darwin_arm64.tar.gz
sudo mv pgbrowser /usr/local/bin/
```

#### Windows

Download the `.zip` archive from Releases, extract, and add `pgbrowser.exe` to your PATH.

## Usage

```bash
# Connect to a PostgreSQL cluster
pgbrowser --url "postgres://user:password@host:5432/dbname"

# Local development (peer auth)
pgbrowser --url "postgres://localhost/mydb"

# Show version
pgbrowser version
pgbrowser --version

# Show help
pgbrowser --help
```

## Key Bindings

| Key | Action |
|-----|--------|
| `j` / `k` / `Up` / `Down` | Move up/down in lists |
| `Enter` | Drill into selected item |
| `Esc` | Go back one level |
| `Tab` | Cycle focus between panels |
| `/` | Live fuzzy filter (applies to focused panel) |
| `:` | Command mode (`:databases`, `:quit`) |
| `[` / `]` | Switch tabs in table detail view |
| `Ctrl+E` | Execute SQL in query panel |
| `q` | Quit |

## Layout

pgbrowser uses a split-panel layout that shows more information at a glance:

```
┌──────────────────┬──────────────────────────────┐
│ Tables           │ Columns | Indexes | Data      │
│ ▸ users          │  id       bigint   NOT NULL   │
│   orders         │  email    varchar  NOT NULL   │
│   products       │  name     varchar  YES        │
│                  ├──────────────────────────────┤
│                  │ Query [Ctrl+E to run]         │
│                  │ SELECT * FROM users LIMIT 10  │
│                  │──────────────────────────────│
│                  │ id │ email       │ name       │
│                  │  1 │ foo@bar.com │ Alice      │
└──────────────────┴──────────────────────────────┘
```

- **Database level** — database list (left) + cluster query panel (right) — run SQL across all databases
- **Schema level** — schema list (left) + live tables preview (right)
- **Table level** — table list (left) + detail tabs + query panel (right)

## Navigation Hierarchy

```
Cluster (connection info)
  +-- Databases (right panel: cluster query — run SQL across all DBs)
       +-- Schemas (right panel previews tables)
            +-- Tables (right panel shows detail + query)
                 +-- Columns   (name, type, nullable, default)
                 +-- Indexes   (name, definition)
                 +-- Data      (first 50 rows)
                 +-- Query     (SQL editor + results)
```

## Screenshots

*Coming soon — pgbrowser is in active development.*

## Requirements

- PostgreSQL 12 or later
- A valid PostgreSQL connection string

## License

pgbrowser binaries are distributed under a proprietary license. See [LICENSE](LICENSE) for terms.

Copyright (c) 2026 Zagware. All rights reserved.
