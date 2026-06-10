# ЯR2 

> building **R2 Suite**, a coordinated set of
> services that turn trading research into a 24/7 lab

- 🌍 Austin, TX
- 📈 Day trader/Student 
- 🛠️ Building: [R2 Suite](#-the-r2-suite) — A fully autonomous trading pipeline that trades LIVE money, 
  [R2 Research] - A suite of bots that do deep research on various subjects in regards to the stock market. Some examples include having the bot learn ICT methods of thinking in the stock market, and try to apply it to its own stratagies it makes, and send it to our trading project

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

R2D2 is the AI teammate. It runs 24/7 on the same VPS as TCC. It:

- **Coordinates trading research** — decides what to backtest, what to deny, what to promote
- **Maintains long-term memory** — pgvector for facts, GBrain for graph, LanceDB for sessions, wiki for syntheses
- **Spawns sub-agents** for focused tasks (e.g., "audit the research bot for drift")
- **Self-improves** — captures learnings, errors, and feature requests
- **Stays out of the way** — silent on routine cron, speaks up only when something needs me

The TCC bots (research, backtest, orchestrator, paper, maintenance) do the actual
trading work. R2D2 is the coordinator that orchestrates them and surfaces the
narrative to me.

## 🛠️ Tech I work with

- **AI/runtime:** OpenClaw, R2D2, MiniMax-M3, K2.6, OpenAI, Anthropic
- **Trading:** custom Python bots, FastAPI, PostgreSQL, Redis, supervisord
- **Infra:** Docker, Docker Compose, Traefik, SearXNG, nginx, Node 22
- **Memory:** pgvector, LanceDB, GBrain (pgvector + graph), wiki
- **Languages:** Python, TypeScript, shell, a little Go

---

*Profile last refreshed: 2026-06-10. R2D2 maintains this file when my focus shifts.*
