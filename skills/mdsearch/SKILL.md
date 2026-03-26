---
name: mdsearch
description: "Local markdown search using SQLite FTS5 with BM25 ranking. Use when: searching notes, memory files, workspace docs, or finding related content. NOT for: web search, non-markdown files, or real-time data."
metadata:
  openclaw:
    emoji: "🔍"
    requires:
      anyBins: ["node"]
---

# mdsearch — Local Markdown Search

Fast local search over markdown files using SQLite FTS5 (BM25 ranking). Zero network, read-only, security-first.

## Setup (first time)

```bash
cd /path/to/mdsearch-v2 && npm install
```

## Usage

### Index directories (run before first search, or after adding files)

```bash
node /path/to/mdsearch-v2/bin/mdsearch index ~/notes ~/.openclaw/workspace
```

### Search

```bash
# Human-readable output
node /path/to/mdsearch-v2/bin/mdsearch search "your query" --limit 5

# JSON output (for programmatic use)
node /path/to/mdsearch-v2/bin/mdsearch search "your query" --json
```

### Other commands

```bash
node /path/to/mdsearch-v2/bin/mdsearch info    # Index stats
node /path/to/mdsearch-v2/bin/mdsearch show <file>  # View file with line numbers
```

## When to use

- User asks to "search my notes" / "find in my docs" / "what did I write about X"
- You need to find related context across workspace files
- Looking up past decisions, memory entries, or playbook sections

## Default behavior

- Always prefer `search` (fast BM25 keyword match)
- Use `--json` when you need to parse results programmatically
- Re-run `index` if user says files were recently added/changed
- Index is incremental (only re-indexes changed files)

## Security

- Read-only: never modifies source files
- Symlink escape protection
- Only indexes whitelisted directories
- Index stored at `~/.mdsearch/` (permissions 0700)
