---
title: 'Building 12th Data in the Open'
description: "A running log of designing 12th Data, a planned public Texas A&M football data platform: architecture decisions, open questions, and what isn't built yet."
category: 'Data'
status: 'planned'
date: 2026-09-15
---

This note is planned as the build log for [12th Data](/projects/#12th-data). Nothing described
below is implemented yet — this is the design thinking before any code is written.

## What 12th Data is meant to be

An open-source, public-data platform built around Texas A&M football data: ingestion pipelines,
a Postgres store for structured queries, Parquet for analytical workloads, and visualizations on
top. The intent is to document the real path from raw public data to a usable analysis, including
the parts that don't work on the first try.

## Planned log entries

- Why the pipeline will land on Python + SQL first, before any orchestration tooling.
- Initial schema design for game, play, and season-level data.
- How Docker, Kubernetes, Terraform, and GitOps fit a project this size without becoming
  overhead for their own sake.
- The first public dataset released, once one exists.

As of this writing, 12th Data is a plan, not a running system. This note will be updated as that
changes.
