---
title: 'Parquet vs. CSV for Public Sports Data'
description: 'Why a columnar format like Parquet is worth the extra complexity over CSV for a project like 12th Data, and where CSV is still the right call.'
category: 'Data'
status: 'draft'
date: 2026-09-10
---

This note is a draft. It is an outline of the argument, not a finished piece.

## The question

12th Data will pull public play-by-play and season data that's most commonly distributed as CSV.
Before building pipelines around that format by default, it's worth writing down why Parquet is
the better storage layer for the analytical side of the platform, and where CSV should stay.

## Rough outline

- **Schema and types.** CSV has none; every reader re-infers types. Parquet carries a schema, which
  matters once multiple pipeline stages and a Postgres load step depend on consistent typing.
- **Columnar reads.** Analytical queries touch a handful of columns across many rows. Parquet reads
  only those columns; CSV requires a full row scan.
- **Compression and file size.** Columnar encoding compresses far better than row-based text,
  which matters for a public dataset meant to be downloaded, not just queried.
- **Where CSV still wins.** Human-readability, diffability in git, and zero-tooling access for
  anyone who just wants to open a file in a spreadsheet. Raw source drops and small reference
  tables will likely stay CSV even after the pipeline standardizes on Parquet internally.

## Still open

- Whether to publish both formats side by side, or Parquet only with a documented conversion step.
- Partitioning strategy once there's more than one season of data.

This will be rewritten once the first pipeline stage of 12th Data actually exists.
