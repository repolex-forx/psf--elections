# Repolex Knowledge Graph of psf/elections

RDF knowledge graph data for [psf/elections](https://github.com/psf/elections), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download psf/elections
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 68a6bfc25885bcaad627171c46fa6b65342ec527
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 68a6bfc25885bcaad627171c46fa6b65342ec527
│           └── chunk-001.nq.gz
├── blob
│   ├── 284497495fd30a2fa57460b48f06bd1467b5ad31.nq.gz
│   ├── 3b344e40dfcae9a7f7952b32bc1252b6c9fc6725.nq.gz
│   ├── 9728fa7faabb36a15789b7441c08b815862f73ee.nq.gz
│   ├── a801d7974cf50371362d6eff0438e21376926acf.nq.gz
│   └── afed0735dc96c6fc6a05ec52e959b8175f27cee5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 68a6bfc25885bcaad627171c46fa6b65342ec527.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 13 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[psf/elections](https://github.com/psf/elections)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
