# pgbrowser

A **k9s-style TUI** for browsing PostgreSQL clusters — databases, schemas, tables, and data.

## Install

### Homebrew (macOS / Linux)

```bash
brew tap zagware/tap
brew install pgbrowser
```

### Manual download

Download the latest binary from the [Releases](https://github.com/zagware/pgbrowser-dist/releases) page.

## Usage

```bash
pgbrowser --url "postgres://user:password@host:5432/dbname"
```

### Key Bindings

| Key | Action |
|-----|--------|
| `j` / `k` / arrows | Move up/down |
| `Enter` | Drill into selected item |
| `Esc` | Go back one level |
| `/` | Live fuzzy filter |
| `:` | Command mode |
| `[` / `]` | Switch tabs (in table detail) |
| `q` | Quit |

## License

pgbrowser binaries are distributed under a proprietary license. See [LICENSE](LICENSE) for terms.

Copyright (c) 2026 Zagware. All rights reserved.
