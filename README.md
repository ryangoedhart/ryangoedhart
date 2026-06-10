# Ryan Goedhart 🤖

> **AI-augmented day trader** building R2D2, a multi-agent research platform
> that turns my trading research into a 24/7 lab.

- 🌍 Austin, TX (America/Chicago)
- 📈 Day trader (active 8AM–8PM CT)
- 🛠️ Building: [R2D2](#-the-r2d2-platform) — a coordinator + sub-agent system on top of OpenClaw
- 🎯 North star: scale multi-agent research and trading support, ship only when there's a real bottleneck

---

## 🛸 The R2D2 Platform

Three repos, one VPS, one mission: turn ideas into validated trading strategies.

| Repo | What | Stack |
|---|---|---|
| **[r2d2-platform](https://github.com/ryangoedhart/r2d2-platform)** | The R2D2 AI runtime + OpenClaw workspace | OpenClaw, R2D2 agent, pgvector, LanceDB, GBrain, Obsidian-style wiki |
| **[trading-command-center](https://github.com/ryangoedhart/trading-command-center)** | TCC — 24/7 trading research lab | FastAPI, 5 supervised bots, PostgreSQL, Redis, Vibe-Trading, tradingagents |
| **[vps-infrastructure](https://github.com/ryangoedhart/vps-infrastructure)** | VPS plumbing + master inventory | Docker Compose, Traefik, SearXNG |

### How they fit together

```
   Internet (HTTPS)
        │
        ▼
   Traefik  ──────────────────────────  vps-infrastructure
        │
        ├── r2d2.world  ──────────────►  r2d2-gateway (nginx + Node)  ─┐
        │                                                                   ├─ r2d2-platform
        └── trading.r2d2.world  ──────►  tcc-app (FastAPI + 5 bots)  ────┘
                                          │
                                          ├── tcc-db (postgres)
                                          └── tcc-redis (cache)
```

- **`r2d2.world`** — R2D2's front door. Static landing page + AI status JSON.
- **`trading.r2d2.world`** — TCC's control UI + dashboard.
- **`traefik.r2d2.world`** — Traefik dashboard (basic-auth).
- All orchestrated by Traefik (from `vps-infrastructure`).

---

## 🤖 What R2D2 does (the short version)

R2D2 is my AI teammate. It runs 24/7 on the same VPS as TCC. It:

- **Coordinates trading research** — decides what to backtest, what to deny, what to promote
- **Maintains long-term memory** — pgvector for facts, GBrain for graph, LanceDB for sessions, wiki for syntheses
- **Spawns sub-agents** for focused tasks (e.g., "audit the research bot for drift")
- **Self-improves** — captures learnings, errors, and feature requests
- **Stays out of the way** — silent on routine cron, speaks up only when something needs me

The TCC bots (research, backtest, orchestrator, paper, maintenance) do the actual
trading work. R2D2 is the coordinator that orchestrates them and surfaces the
narrative to me.

---

## 📊 Current focus (June 2026)

- **TCC bots stable**, 300+ tests passing, paper-trading clean state
- **Memory pipeline** hardened — 14 bugs fixed across 4 audits, watchdog with runaway detector
- **VPS CPU 100% incident** resolved (PGLite index corruption + watchdog conflict)
- **GitHub restructured** — three clean repos with production READMEs, descriptions, topics

---

## 🛠️ Tech I work with

- **AI/runtime:** OpenClaw, R2D2, MiniMax-M3, K2.6, OpenAI, Anthropic
- **Trading:** custom Python bots, FastAPI, PostgreSQL, Redis, supervisord
- **Infra:** Docker, Docker Compose, Traefik, SearXNG, nginx, Node 22
- **Memory:** pgvector, LanceDB, GBrain (pgvector + graph), wiki
- **Languages:** Python, TypeScript, shell, a little Go

---

## 📫 Find me

- **Trading site:** [trading.r2d2.world](https://trading.r2d2.world)
- **R2D2:** [r2d2.world](https://r2d2.world)

---

*Profile last refreshed: 2026-06-10. R2D2 maintains this file when my focus shifts.*
