---
title: 'Kubernetes Observability: Metrics, Logs, and the Gap Between Them'
description: 'A planned walkthrough of building an observability stack for Kubernetes: what Prometheus, Grafana, and Loki are each good at, and where they fall short alone.'
category: 'Kubernetes'
status: 'planned'
date: 2026-09-01
---

This note is planned. It has not been written yet.

## Planned scope

A practical, sanitized walkthrough of the observability stack referenced in the site's
[Architecture Explorer](/#architecture-explorer): Prometheus for metrics, Grafana for
visualization, and Loki for logs. The goal is to explain what each tool answers well on its own,
and the specific questions that require correlating all three — for example, tracing a latency
spike from a dashboard, to the pods involved, to the log lines that explain it.

## Planned outline

- Metrics vs. logs vs. events: what each signal type is and isn't good at.
- A minimal, fictional alerting setup and the failure modes it's meant to catch.
- Why dashboards alone don't replace an incident runbook, and what closes that gap.

This note will be filled in as the accompanying lab entry takes shape.
