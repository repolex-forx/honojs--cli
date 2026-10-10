# Repolex Knowledge Graph of honojs/cli

RDF knowledge graph data for [honojs/cli](https://github.com/honojs/cli), parsed by [repolex](https://repolex.ai).

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
rlex download honojs/cli
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c1b6028d8ea9bacaa1f08eed9345fb4301e9215c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c1b6028d8ea9bacaa1f08eed9345fb4301e9215c
│           └── chunk-001.nq.gz
├── blob
│   ├── 097cfb99a47741fb6f17e48356822cb0ed5dab91.nq.gz
│   ├── 12109204d6d543e0008fdb5c08ab4763d95fe29c.nq.gz
│   ├── 43c994c2d3617f947bcb5adf1933e21dabe46bb5.nq.gz
│   ├── 45e34eebb46cd08d75d76df3a0bb3c0b0d9ec262.nq.gz
│   ├── 4ebbcce7355eeaa8c14a91c249e9ec4234230314.nq.gz
│   ├── 531bfc9e11cc51f0c8df144dac67ccb6f8b08820.nq.gz
│   ├── 54a89e1897b6fb85016f7def3ceb6210b9d37680.nq.gz
│   ├── 6606c3c947818c92be3a9e5f1fa984082bd3ef46.nq.gz
│   ├── 6b7c99cd64092dd8743dea67b36f6e0dbafa5711.nq.gz
│   ├── 6c458abaecb8f28aebb2830188d48d0c3939ace1.nq.gz
│   ├── 6d24091865a55a0e4fa17d119b506f98627016de.nq.gz
│   ├── 74fdab42b0980d59bae4ec66df23a938f9824976.nq.gz
│   ├── 7838c59a9317be407e142f69223d896c8f86fae3.nq.gz
│   ├── 7a2eb4ec4c71ccac1054d2ad921b5b3289018670.nq.gz
│   ├── 7f1e3732095425b9e1c2bf49d3392e414158e01e.nq.gz
│   ├── 800ba72d30e8cc3e042364dcf2b916d4b587b33f.nq.gz
│   ├── 8a5ff97320add95b15ebff1054bbfa8783fe3e69.nq.gz
│   ├── 94b038785b2e5d4921bf554f2dbbbff02e9bf8bb.nq.gz
│   ├── 958ab8d0c777a741733da1c1a58755d1f9fb4b97.nq.gz
│   ├── 973171fd6ddbc206f104b4875032f6d54445e116.nq.gz
│   ├── 97452d52664b2e00171af1c936ac1d703598d0e1.nq.gz
│   ├── 9cc5f6b52ae450235a8d0e8a0f2083d56ebf4bc3.nq.gz
│   ├── 9f6bff52d9d25d4df803202a56ced92a932f6116.nq.gz
│   ├── 9fb8e0ce0348288ba19fbd632c26a820cb80b067.nq.gz
│   ├── a456dc9af26599fe0694289efeed48646f174952.nq.gz
│   ├── a7cfaaeec22240bd45ce683711868ad30aeb0482.nq.gz
│   ├── ba350b99d4d28c94e9e3276c9c12c1ac4d68a884.nq.gz
│   ├── be0943df7b6c7b6bb215582db54a32bef498e447.nq.gz
│   ├── c3bc6affc3ddb55161aed51f19902fb1b610ecc2.nq.gz
│   ├── c7a9e0f0f4e6486d7311187a7482ac8b9fe5ec30.nq.gz
│   ├── c7ac298cab69d823cf76774bd755feea2c2a6d84.nq.gz
│   ├── d3ce346e8b0bc1617476680a5d28cb201e9a49c7.nq.gz
│   ├── e1c0c967d1bae25422d6de67634328328bc021bf.nq.gz
│   ├── e6270a1e76e68b9dd620b4fb9bc195063eb0a177.nq.gz
│   ├── e8366e57dbc8075667a7655325f13ab034cfb19a.nq.gz
│   └── fa764cd77d10b92dd93223bbb3147c11a1487eaa.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c1b6028d8ea9bacaa1f08eed9345fb4301e9215c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[honojs/cli](https://github.com/honojs/cli)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
