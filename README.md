# Repolex Knowledge Graph of allenai/XYBench

RDF knowledge graph data for [allenai/XYBench](https://github.com/allenai/XYBench), parsed by [repolex](https://repolex.ai).

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
rlex download allenai/XYBench
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e39eb25aec2a5fc7c69366a366e0714bba5abfe2
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e39eb25aec2a5fc7c69366a366e0714bba5abfe2
│           └── chunk-001.nq.gz
├── blob
│   ├── 0053b76797ea0440f6cd80418f51eca7220aa7a7.nq.gz
│   ├── 1d74195003e4f7be0c79e5e0946506ad9fa15ddf.nq.gz
│   ├── 2a36e601a0f0c1a86847a8212947cab23f98ed84.nq.gz
│   ├── 2d0aec08d6c5a254486c1a1b36f503bec67a27b0.nq.gz
│   ├── 5626d56ad2dabf7947e6e1a7639890cf3715974f.nq.gz
│   ├── 6945088ee98f930af080fb3b3700694e2acf7302.nq.gz
│   ├── 6bf078c39f0d0e3560f2d34676d35d47de1da068.nq.gz
│   ├── a5b27cfcfa81bc1d5ddb8306dde6e088004c947d.nq.gz
│   ├── acaa59e2ac8200f3285c598eb52d0db264e601ec.nq.gz
│   ├── af416eba59b5fe98c2799a84f1da9ccf32bad06f.nq.gz
│   ├── af53a86e6501bee2f031d9500c5d6a733fef7ca5.nq.gz
│   ├── bc7df565111d8c326164cc42d4ed7b59a3a9507b.nq.gz
│   ├── c3dc218719ba2ba3a1472bbfb8c42de638a569f3.nq.gz
│   ├── ced7a1eaed2251ffd5ced925039a1af7d6543491.nq.gz
│   ├── d3d62b2ff7f50f0d755d0b3750c3126adf6dd877.nq.gz
│   └── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e39eb25aec2a5fc7c69366a366e0714bba5abfe2.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
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

[allenai/XYBench](https://github.com/allenai/XYBench)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
