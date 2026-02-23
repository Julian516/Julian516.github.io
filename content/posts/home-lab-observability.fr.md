+++
title = "Concevoir une stack d’observabilité pour mon home-lab"
date = 2024-10-05T08:30:00+02:00
description = "Comment j’assemble traces, métriques et logs pour mon infra personnelle."
summary = "Grafana, ClickHouse et un agent Go minimal gardent mes side-projects honnêtes."
+++

J’héberge plus de services à la maison que je ne veux bien l’avouer : runners CI, playground LLM, sauvegarde photo et toutes les expériences du moment. Sans observabilité, ce chaos devient vite incontrôlable.

## Principes

1. **Tout émet des traces.** Un agent Go léger enveloppe `otelhttp` et un exporter maison qui batch dans ClickHouse.
2. **Les logs sont structurés.** Sortie JSON pour injecter rapidement le contexte dans Grafana ou Loki.
3. **Les dashboards restent sobres.** Je privilégie le signal et laisse la typographie du site faire le reste.

## Stack

- Agents Go avec le SDK OpenTelemetry
- ClickHouse pour traces et métriques
- Grafana pour dashboards et alerting
- Mosquitto pour remonter les événements légers des appareils

Prochaine étape : tester InfluxDB 3.0 et une mini UI pour visualiser la consommation électrique du foyer. Je posterai les updates dans l’archive dès que c’est en ligne.
