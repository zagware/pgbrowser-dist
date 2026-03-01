# pgbrowser

A **k9s-style terminal UI** for browsing PostgreSQL clusters. Navigate databases, schemas, tables, and data with keyboard-driven drill-down — no GUI required.

Inspired by [k9s](https://k9scli.io/) for Kubernetes, pgbrowser brings the same hierarchical browsing experience to PostgreSQL.

## Features

- **Hierarchical navigation** — browse Databases > Schemas > Tables > Table Detail with Enter/Esc drill-down
- **Breadcrumb trail** — always know where you are in the cluster hierarchy
- **Live fuzzy filtering** — press `/` to instantly filter any list as you type
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
| `/` | Live fuzzy filter (type to narrow, Esc to clear) |
| `:` | Command mode (`:databases`, `:quit`) |
| `[` / `]` | Switch tabs in table detail view |
| `q` | Quit |

## Navigation Hierarchy

```
Cluster (connection info)
  +-- Databases
       +-- Schemas
            +-- Tables (with estimated row counts)
                 +-- Table Detail
                      +-- Columns   (name, type, nullable, default)
                      +-- Indexes   (name, definition)
                      +-- Data      (first 50 rows)
```

## Screenshots

*Coming soon — pgbrowser is in active development.*

## Requirements

- PostgreSQL 12 or later
- A valid PostgreSQL connection string

## License

pgbrowser binaries are distributed under a proprietary license. See [LICENSE](LICENSE) for terms.

Copyright (c) 2026 Zagware. All rights reserved.
