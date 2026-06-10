# Ryan Goedhart 🤖

> **AI-augmented day trader** building **R2 Suite**, a coordinated set of
> services that turn trading research into a 24/7 lab.

- 🌍 Austin, TX (America/Chicago)
- 📈 Day trader (active 8AM–8PM CT)
- 🛠️ Building: [R2 Suite](#-the-r2-suite) — a monorepo on top of OpenClaw + R2D2
- 🎯 North star: ship only when there's a real bottleneck, scale the lab when it earns its keep

---

## 🛸 The R2 Suite

**One monorepo. Three layers. One VPS.**

| Repo | What | Status |
|---|---|---|
| **[ryangoedhart/r2-suite](https://github.com/ryangoedhart/r2-suite)** | R2 Suite monorepo — OpenClaw workspace + R2D2 platform + Trading Command Center + VPS infrastructure | 🟢 Active |

The 3 split repos (`r2d2-platform`, `trading-command-center`, `vps-infrastructure`) were merged into the monorepo on 2026-06-10 and are now archived.

### How the pieces fit together

```
   Internet (HTTPS)
        │
        ▼
   Traefik  ──────────────────────  vps-infrastructure (in monorepo)
        │
        ├── r2d2.world  ─────────►  r2d2-gateway (nginx + Node)
        │                            ▲
        │                            │
        │                            └─ openclaw-goll  ◄── r2d2-platform (in monorepo)
        │                                 │
        │                                 │ (R2D2 the AI reads AGENTS.md,
        │                                 │  SOUL.md, MEMORY.md from the
        │                                 │  monorepo root)
        │                                 │
        │                                 ▼
        │                            tcc-app (FastAPI + 5 bots)
        │                                 │
        └── trading.r2d2.world ──►       ├── tcc-db (postgres 16)
                                         └── tcc-redis (redis 7)
                                          ▲
                                          │
                            trading-command-center (in monorepo)
```

---

## 🤖 What R2D2 does

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

- ✅ **TCC bots stable** — 317 tests passing, paper-trading clean state
- ✅ **Memory pipeline** hardened — 14 bugs fixed across 4 audits, watchdog with runaway detector
- ✅ **VPS CPU 100% incident** resolved (PGLite index corruption + watchdog conflict)
- ✅ **GitHub production-level** — 1 monorepo, CI on every push, Dependabot weekly, issue/PR templates, CODEOWNERS
- ✅ **R2 Suite** — one umbrella name for the whole stack

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
- **Source code:** [github.com/ryangoedhart/r2-suite](https://github.com/ryangoedhart/r2-suite)

---

*Profile last refreshed: 2026-06-10. R2D2 maintains this file when my focus shifts.*
