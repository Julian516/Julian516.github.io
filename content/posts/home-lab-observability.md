+++
title = "Designing a Home-Lab Observability Stack"
date = 2024-10-05T08:30:00+02:00
description = "How I'm piecing together tracing, metrics, and logs for my personal infrastructure."
summary = "Grafana, ClickHouse, and a tiny Go agent keep my side projects honest."
+++

I have more services running at home than I care to admit: CI runners, an LLM playground, my photo backup pipeline, and whatever experiment I'm currently hacking on. Observability keeps all of that chaos understandable.

## Principles

1. **Everything ships traces.** A lightweight Go agent wraps `otelhttp` plus a custom exporter that batches to ClickHouse.
2. **Logs are structured.** JSON outputs make it trivial to pull context into Grafana or Loki.
3. **Dashboards stay boring.** I optimize for signal and let the typography from this site carry the aesthetics.

## Stack

- Go agents with OpenTelemetry SDK
- ClickHouse for traces and metrics
- Grafana for dashboards and alerting
- Mosquitto to pipe lightweight device events

Next iteration will experiment with InfluxDB 3.0 and a minimal UI to visualize home power usage. I'll post updates in the archive once it's live.
