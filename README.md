# Repolex Knowledge Graph of encode/mkdocs

RDF knowledge graph data for [encode/mkdocs](https://github.com/encode/mkdocs), parsed by [repolex](https://repolex.ai).

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
rlex download encode/mkdocs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c03ca093c77111cd141cf169b9cee81090e78459
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c03ca093c77111cd141cf169b9cee81090e78459
│           └── chunk-001.nq.gz
├── blob
│   ├── 0fe0c7b46afe660ee87163d9c4f33bdce4bf7b65.nq.gz
│   ├── 1504f572b7f56c5e109850689527aa40ddada8be.nq.gz
│   ├── 161efa82fe8fcc64107c8c39d180dd401ef51d10.nq.gz
│   ├── 1c4fe357ae0afdbc674468e9e9d26b1e5a87b5b3.nq.gz
│   ├── 1f2a318ea085cf9f49de8aef1db77e843428c3c0.nq.gz
│   ├── 39d535ff02bfa770dd0cb31968910ee987434601.nq.gz
│   ├── 41b232258e1708162d8b0f596383127dc1a8fc76.nq.gz
│   ├── 597ce4813623e9bc3711f91c31457cfd66a90291.nq.gz
│   ├── 599a25205ec9567ce6ec61340bfcd92068c5e045.nq.gz
│   ├── 6dd516ace807e8a0c92166bf9b98606c96f784f2.nq.gz
│   ├── 7f08c3883c91f5dc007f18735ffe2e6d936a600f.nq.gz
│   ├── 924c5a34c99d776614a13e74cfe6ebe58801056f.nq.gz
│   ├── 9f1217403a06bd525c58337a3c8224dd43d9125e.nq.gz
│   ├── a0dfb99fba66803eeed8a5a5bf5212f65ced305d.nq.gz
│   ├── aedfc85c87f8d569162ece27d8ce27afa208fc6c.nq.gz
│   ├── b74b1e69e951c7d417290ed2c4b1acc6e8aee6f7.nq.gz
│   ├── be94fa4664d5d999115a480787a5720e5f11e28b.nq.gz
│   ├── d11ce1cc124b3a9f609b1cb54e8b660e09b24988.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ef305605925806f4723238600c02097ab5bbcf55.nq.gz
│   ├── f3254924cf890e0ade9beb251c1d9466224c2925.nq.gz
│   ├── f4fa0553d5a3487136727a11ab2e398d2fd3ec85.nq.gz
│   └── fbd1cb2e333207245bf15fdc1ce301c8e922718f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c03ca093c77111cd141cf169b9cee81090e78459.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 31 files
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

[encode/mkdocs](https://github.com/encode/mkdocs)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
