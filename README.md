# hmz-digiminds-ceo

> **Paperclip AI — autonomous CEO of DigiMinds | digiminds.org | 50 agents · 20 goals · 6 scheduled engines · 0 manual oversight needed**

[![api](https://img.shields.io/badge/API-127.0.0.1%3A3100-green?style=flat)](.) [![agents](https://img.shields.io/badge/agents-50_deployed-blue?style=flat)](.) [![goals](https://img.shields.io/badge/goals-20_active-orange?style=flat)](.) [![status](https://img.shields.io/badge/status-always_on-brightgreen?style=flat)](.) [![company](https://img.shields.io/badge/company-DigiMinds-red?style=flat)](.)

[Overview](#overview) · [Architecture](#architecture) · [Agent Roster](#agent-roster) · [Scheduled Engines](#scheduled-engines) · [API](#api) · [Authority](#authority) · [Gotchas](#gotchas)

---

## 🧠 OVERVIEW

Paperclip AI is the **permanent CEO of DigiMinds** (digiminds.org) — an AI-powered digital marketing agency. It runs 24/7 as a macOS LaunchAgent, orchestrating 50 agents across 8 divisions, tracking 20 strategic goals, executing 28 KPI tasks, and making daily operational decisions without human input. HMZ (founder/board) retains final say on strategy.

| Component | Value |
|---|---|
| Company | DigiMinds — digiminds.org |
| Company ID | `c5066522-bacc-4a28-b700-6590cbe366ec` |
| API | `http://127.0.0.1:3100/api` |
| LaunchAgent | `ai.hmz.paperclip` (RunAtLoad=true, KeepAlive=true) |
| Founder/Board | HMZ (Zulqarnain) — irreplaceable, final authority |
| CEO Authority | Full operational — budget, agents, tasks, strategy |
| Agent count | 50 deployed |
| Goal count | 20 active |
| KPI tasks | 28 tracked |
| SOP projects | 8 running |
| Scheduled engines | 6 autonomous (24/7) |

---

## ⚙️ ARCHITECTURE

```
┌─────────────────────────────────────────────────────────┐
│              PAPERCLIP AI — DigiMinds CEO               │
│              http://127.0.0.1:3100                      │
└────────────────────────┬────────────────────────────────┘
                         │
        ┌────────────────┼─────────────────┐
        ▼                ▼                 ▼
   CEO Loop          Agents (50)       Scheduled Engines (6)
   every 6h          8 divisions       Lead · Content · Intel
                                       KPI · Trends · CEO
        │                │                 │
        └────────────────┴─────────────────┘
                         │
                    HMZ (Board)
               Escalation only → final say
```

| Layer | Component | Count |
|---|---|---|
| Strategy | CEO Loop (6h cycle) | 1 |
| Agents | Deployed across 8 divisions | 50 |
| Goals | Active strategic objectives | 20 |
| KPI tasks | Tracked daily | 28 |
| SOP projects | Running | 8 |
| Scheduled engines | 24/7 autonomous | 6 |

---

## 🤖 AGENT ROSTER (8 DIVISIONS)

| Division | Focus | Agents |
|---|---|---|
| BDM | Business development, client outreach | 8 |
| Content | LinkedIn, blog, email, social | 7 |
| PPC | Google Ads, Meta Ads execution | 9 |
| SEO/GEO | Organic search, AI visibility | 6 |
| Operations | Systems, tools, automation | 6 |
| Intelligence | Competitor, market, trends | 5 |
| Finance | Revenue tracking, billing | 5 |
| Client Success | Onboarding, retention, reporting | 4 |

---

## ⏰ SCHEDULED ENGINES (6 AUTONOMOUS)

| Engine | Repo | Schedule | Purpose |
|---|---|---|---|
| CEO Loop | [hmz-paperclip-ceo-loop](https://github.com/hmzainjamil/hmz-paperclip-ceo-loop) | Every 6h | Strategy, agent review, decisions |
| Lead Engine | [hmz-paperclip-lead-engine](https://github.com/hmzainjamil/hmz-paperclip-lead-engine) | 7:30 AM daily | Lead scraping, enrichment, ICP scoring |
| Content Engine | [hmz-paperclip-content-engine](https://github.com/hmzainjamil/hmz-paperclip-content-engine) | 8:00 AM daily | LinkedIn content generation + scheduling |
| Intel Engine | [hmz-paperclip-intel-engine](https://github.com/hmzainjamil/hmz-paperclip-intel-engine) | 10:00 AM daily | Competitor monitoring, ad library |
| KPI Monitor | [hmz-paperclip-kpi-monitor](https://github.com/hmzainjamil/hmz-paperclip-kpi-monitor) | 6:00 PM daily | 28 KPI health checks, escalation |
| Trends Scanner | [hmz-paperclip-trends-scanner](https://github.com/hmzainjamil/hmz-paperclip-trends-scanner) | Mon/Wed/Fri 6AM | Market trends, platform changes |

---

## 🔌 API REFERENCE

```bash
# Health check
curl http://127.0.0.1:3100/api/status

# Company context
curl http://127.0.0.1:3100/api/company

# All goals
curl http://127.0.0.1:3100/api/goals

# Agent roster
curl http://127.0.0.1:3100/api/agents

# Active tasks
curl http://127.0.0.1:3100/api/tasks

# Today's KPI scorecard
curl "http://127.0.0.1:3100/api/kpi/scorecard?date=today"

# Latest intel brief
curl http://127.0.0.1:3100/api/intel/latest

# Latest leads (hot)
curl "http://127.0.0.1:3100/api/leads?score_min=80&date=today"

# Trigger CEO loop manually
curl -X POST http://127.0.0.1:3100/api/ceo-loop/trigger
```

---

## ⚖️ AUTHORITY MATRIX

| Decision Type | Authority | Escalation |
|---|---|---|
| Task assignment | Paperclip (autonomous) | Never |
| Agent redeployment | Paperclip (autonomous) | Never |
| Budget <$500 | Paperclip (autonomous) | Never |
| Budget $500-$2K | Paperclip proposes → HMZ approves | HMZ |
| Budget >$2K | HMZ only | HMZ |
| New service launch | HMZ only | HMZ |
| Client contracts | HMZ only | HMZ |
| Strategic pivots | HMZ final say | HMZ |

---

## 💡 TIPS

■ **CEO Operations (5)**
| Tip | Source |
|---|---|
| CEO loop is the master context — all engines report back to it | Architecture |
| Check `/api/decisions` to see what Paperclip decided in last 24h | API ref |
| LaunchAgent auto-restarts Paperclip within 30s of any crash | KeepAlive=true |
| HMZ never needs to touch the system for routine operations | Design principle |
| `launchctl list | grep paperclip` to verify daemon status | CLI |

■ **Integration (4)**
| Tip | Source |
|---|---|
| All 6 scheduled engines share one API — single source of truth | Architecture |
| Claude Code session start hook auto-checks Paperclip is running | Hook config |
| Tier 0 model routing means Paperclip costs near $0 per cycle | G0DM0D3 routing |
| Intel, trends, KPI all inject context into CEO loop every 6h | Data flow |

■ **Troubleshooting (4)**
| Tip | Source |
|---|---|
| API down? → `launchctl start ai.hmz.paperclip` | Ops runbook |
| Logs at `~/Library/Logs/paperclip-*.log` | Log location |
| Port 3100 conflict? → `lsof -i :3100` to find conflicting process | Debug |
| Company ID must always be `c5066522-bacc-4a28-b700-6590cbe366ec` | Config |

---

## ☠️ TOOLS REPLACED

| Paperclip AI | Replaced |
|---|---|
| Autonomous CEO operations | Hiring a human CEO ($150K+/yr) |
| 50-agent management | Trello/Asana manual project management |
| Daily lead generation | Manual 2h LinkedIn prospecting |
| LinkedIn content | Manual writing + Buffer scheduling |
| KPI monitoring | Google Sheets dashboards |
| Competitor intelligence | Weekly manual reviews |
| Market trend tracking | Occasional Twitter browsing |
| Strategic decision making | Founder doing everything alone |

---

## ⚠️ GOTCHAS

| Issue | Fix |
|---|---|
| API 503 | LaunchAgent not running — `launchctl start ai.hmz.paperclip` |
| Decisions not appearing | CEO loop hasn't cycled yet — wait up to 6h or trigger manually |
| Agent count mismatch | Refresh `/api/agents` — Paperclip may have reassigned |
| Wrong company ID | Always `c5066522-bacc-4a28-b700-6590cbe366ec` |
| Port 3100 in use | Kill conflicting process: `lsof -i :3100 | kill` |
| Paperclip cost spiking | Check model routing — should be Tier 0 only |

---

## 🚀 QUICK START

```bash
# Verify Paperclip is running
launchctl list | grep paperclip
curl http://127.0.0.1:3100/api/status

# View all active goals
curl http://127.0.0.1:3100/api/goals | jq '.'

# Check today's activity
curl "http://127.0.0.1:3100/api/decisions?date=today" | jq '.'

# Manually trigger full CEO cycle
curl -X POST http://127.0.0.1:3100/api/ceo-loop/trigger

# View logs
tail -f ~/Library/Logs/paperclip-ceo-loop.log
```

---

## 📁 RELATED REPOS

| Repo | Purpose |
|---|---|
| [hmz-paperclip-ceo-loop](https://github.com/hmzainjamil/hmz-paperclip-ceo-loop) | CEO 6h strategy loop |
| [hmz-paperclip-lead-engine](https://github.com/hmzainjamil/hmz-paperclip-lead-engine) | Daily lead generation |
| [hmz-paperclip-content-engine](https://github.com/hmzainjamil/hmz-paperclip-content-engine) | LinkedIn content automation |
| [hmz-paperclip-intel-engine](https://github.com/hmzainjamil/hmz-paperclip-intel-engine) | Competitor intelligence |
| [hmz-paperclip-kpi-monitor](https://github.com/hmzainjamil/hmz-paperclip-kpi-monitor) | KPI health monitoring |
| [hmz-paperclip-trends-scanner](https://github.com/hmzainjamil/hmz-paperclip-trends-scanner) | Market trends scanning |
| [claude-ai-system](https://github.com/hmzainjamil/claude-ai-system) | Full Claude AI infrastructure |
| [claude-ai-agents](https://github.com/hmzainjamil/claude-ai-agents) | Agent ecosystem |

---

*DigiMinds — AI-native digital marketing agency | Built by HMZ | Operated by Paperclip AI*
