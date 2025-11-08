+++
date = '2025-07-05T16:31:32+05:30'
draft = false
title = 'NOC Multi-LLM Agent'
+++

# NOC Multi-LLM Agent

**Project Date:** October 2025  
**Technologies:** Python (FastAPI, LangGraph), PostgreSQL, Redis, Weaviate, Gemini APIs, Docker, Grafana MCP  
**Repository:** <a href="https://github.com/sonali-rajput/noc-ai-agent" target="_blank" rel="noopener noreferrer">github.com/sonali-rajput/noc-ai-agent</a>

## Summary

An automated network operations centre agent that orchestrates multiple LLMs to triage incidents, correlate telemetry, and notify the right response team in seconds instead of hours.

## Key Capabilities

- **Multi-agent orchestration:** Coordinates specialised LangGraph agents for intake, enrichment, triage, and remediation planning across every alert.
- **Vector-powered correlation:** Uses Weaviate embeddings to match incoming incidents with historical fixes and eliminate duplicate pagers.
- **Real-time observability:** Streams metrics and incident timelines into Grafana MCP dashboards for end-to-end visibility.
- **Automated routing:** Applies Gemini policy agents to pick the correct on-call team based on runbooks, severity, and blast radius.

## Architecture

- **Event ingestion:** FastAPI webhook gateway normalises alerts from Prometheus, CloudWatch, and custom sensors.  
- **State and context:** Redis backs short-lived agent memory while PostgreSQL persists incident timelines, actions, and audit trails.  
- **AI execution layer:** LangGraph orchestrates task-specific LLMs (intake, triage, diagnostics) with Gemini APIs providing long-context reasoning.  
- **Insights & visualisation:** Grafana MCP renders live incident heatmaps, recovery timers, and post-incident analytics.

## Impact

- Reduced manual alert handling time by over 70% through automated triage and escalation.  
- Improved mean time to acknowledge (MTTA) and resolve (MTTR) by surfacing runbook matches within seconds.  
- Delivered a reusable template for LLM-first NOC automation that integrates cleanly with existing SRE tooling.

[Back to Projects](/projects/)
