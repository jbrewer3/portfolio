---
title: "Designing Terraform Modules That Don't Fight You Later"
description: 'Notes on module boundaries, variable design, and state layout, drawn from operating platform infrastructure in production.'
category: 'Infrastructure as Code'
status: 'planned'
date: 2026-09-05
---

This note is planned and not yet written. This is a placeholder outline of the argument it will make.

## Why this note

Most Terraform module problems show up months after the module is written: a variable that should
have been a list, a module boundary drawn around a team's org chart instead of a real infrastructure
seam, state that's too coarse to change safely. The planned note works through those failure modes
using sanitized, fictional examples, not any specific employer's infrastructure.

## Planned sections

1. Where a module boundary should sit — around a resource lifecycle, not a team.
2. Required vs. optional variables, and why permissive defaults quietly become technical debt.
3. State file granularity: one state per module instance vs. shared state, and the blast-radius
   trade-off between them.
4. Testing modules in isolation before they're composed into an environment.

Nothing below this line is written yet.
