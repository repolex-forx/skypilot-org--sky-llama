# Repolex Knowledge Graph of skypilot-org/sky-llama

RDF knowledge graph data for [skypilot-org/sky-llama](https://github.com/skypilot-org/sky-llama), parsed by [repolex](https://repolex.ai).

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
rlex download skypilot-org/sky-llama
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b2d8e2f0c8ede6c972dcbf16c7ab5c70bc38aaac
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b2d8e2f0c8ede6c972dcbf16c7ab5c70bc38aaac
│           └── chunk-001.nq.gz
├── blob
│   ├── 098899a06781a90594acdb1ece680f721e63f52f.nq.gz
│   ├── 13df309d1ed8f5db2c3055915036b08efb77fd23.nq.gz
│   ├── 346a59662db27f0fb7bbba580bcd697eac4d0408.nq.gz
│   ├── 492c34fa2414e744e46ab92adc44077b65199fe4.nq.gz
│   ├── 56a83acfd0f225d47902122cb7b6c67b5b76d47d.nq.gz
│   ├── 883fb11b32bc4a19ae162f1cc869e82ce32a43b9.nq.gz
│   ├── 8d2fb6c0c64ca8e54e85b055724d3d5b39ca29ef.nq.gz
│   ├── 953cce9a3dbd5307502fa23e2cca875dcbd17bc6.nq.gz
│   ├── e572aa563704840af907dcaa99c1c6a10d7966ab.nq.gz
│   └── edf617213d8d1b1cb9b095c5b74e11c664a6fb87.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b2d8e2f0c8ede6c972dcbf16c7ab5c70bc38aaac.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 17 files
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

[skypilot-org/sky-llama](https://github.com/skypilot-org/sky-llama)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
