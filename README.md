# hmz-digiminds-ceo
Paperclip AI — permanent autonomous CEO of DigiMinds agency. 50 agents, 20 goals, 28 KPIs, 6 scheduled engines, port 3100. Zero daily human input.

![api](https://img.shields.io/badge/API-127.0.0.1%3A3100-green?style=flat&labelColor=555) ![agents](https://img.shields.io/badge/agents-50_deployed-blue?style=flat&labelColor=555) ![goals](https://img.shields.io/badge/goals-20_active-orange?style=flat&labelColor=555) ![kpis](https://img.shields.io/badge/KPIs-28_tracked-red?style=flat&labelColor=555) [![company](https://img.shields.io/badge/DigiMinds-digiminds.org-white?style=flat&labelColor=555)](https://digiminds.org)

[Concepts](#-concepts) · [Hot](#-hot) · [Architecture](#️-architecture) · [Authority](#authority-matrix) · [Tips](#-tips-and-tricks-26) · [Replaced](#️-startups--businesses) · [Stars](#star-history)

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**Paperclip API**](http://127.0.0.1:3100/api) | `http://127.0.0.1:3100/api` | Central command — all 50 agents read/write state here. Company: `c5066522-bacc-4a28-b700-6590cbe366ec` |
| [**CEO Loop**](https://github.com/hmzainjamil/hmz-paperclip-ceo-loop) | `ai.hmz.paperclip.plist` | Every 6h: reviews goals → re-assigns agents → logs decisions → escalates critical-only to HMZ |
| [**Lead Engine**](https://github.com/hmzainjamil/hmz-paperclip-lead-engine) | `ai.hmz.paperclip-lead-engine.plist` | Daily 7:30 AM: Apollo+LinkedIn → enrich → ICP score → CRM. Geo blacklist enforced |
| [**Content Engine**](https://github.com/hmzainjamil/hmz-paperclip-content-engine) | `ai.hmz.paperclip-content-engine.plist` | Daily 8:00 AM: trends → angle → generate → quality gate → LinkedIn scheduled 10 AM |
| [**Intel Engine**](https://github.com/hmzainjamil/hmz-paperclip-intel-engine) | `ai.hmz.paperclip-intel-engine.plist` | Daily 10:00 AM: Meta Ad Library + LinkedIn + Clutch → competitor brief |
| [**KPI Monitor**](https://github.com/hmzainjamil/hmz-paperclip-kpi-monitor) | `ai.hmz.paperclip-kpi-monitor.plist` | Daily 6:00 PM: 28 KPIs, RED = CEO escalation |
| [**Trends Scanner**](https://github.com/hmzainjamil/hmz-paperclip-trends-scanner) | `ai.hmz.paperclip-trends-scanner.plist` | Mon/Wed/Fri 6 AM: platform changes, market signals |
| [**HMZ Board Authority**](agents/authority.md) | `agents/authority.md` | HMZ = irreplaceable founder. Budget <$500 = autonomous. $500-2K = propose. >$2K = HMZ only |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**Real-time decisions log**](http://127.0.0.1:3100/api/decisions) | `GET /api/decisions?date=today` | See what the CEO decided in the last 24h — full audit trail |
| [**Manual CEO trigger**](http://127.0.0.1:3100/api/ceo-loop/trigger) | `POST /api/ceo-loop/trigger` | Force immediate CEO review without waiting 6h |
| [**Agent health dashboard**](http://127.0.0.1:3100/api/agents) | `GET /api/agents` | Live status of all 50 agents — last run, output quality, assignment |

---

## ⚙️ ARCHITECTURE

```
HMZ (Founder / Board)
  └── escalation only, final authority on budget >$2K

Paperclip AI CEO (localhost:3100)
  ├── CEO Loop (every 6h)
  │     reviews: 20 goals · 50 agents · 28 KPI tasks
  │     decides: reassign · reprioritize · escalate
  │
  ├── Lead Engine    (7:30 AM) → CRM
  ├── Content Engine (8:00 AM) → LinkedIn
  ├── Intel Engine   (10:00 AM) → CEO context
  ├── KPI Monitor    (6:00 PM) → CEO alerts
  └── Trends Scanner (Mon/Wed/Fri 6AM) → CEO context

Agent Divisions (50 total):
  BDM(8) Content(7) PPC(9) SEO/GEO(6)
  Ops(6) Intel(5)  Finance(5) Client(4)
```

---

<a id="authority-matrix"></a>

## ⚖️ AUTHORITY MATRIX

| Decision | Authority | Escalation |
|----------|-----------|------------|
| Task assignment | Paperclip (autonomous) | Never |
| Agent redeployment | Paperclip (autonomous) | Never |
| Budget <$500 | Paperclip (autonomous) | Never |
| Budget $500-$2K | Paperclip proposes → HMZ approves | HMZ |
| Budget >$2K | HMZ only | Always |
| New service launch | HMZ only | Always |
| Client contracts | HMZ only | Always |

---

## 💡 TIPS AND TRICKS (26)

[CEO Ops](#tips-ceo) · [API](#tips-api) · [Engines](#tips-eng) · [Agents](#tips-agents) · [Debug](#tips-debug)

<a id="tips-ceo"></a>■ **CEO Operations (6)**

| Tip | Source |
|-----|--------|
| Check `/api/decisions?date=today` every morning — see what Paperclip decided overnight | [Transparency](http://127.0.0.1:3100) |
| All 6 engines report to CEO loop — it's the master context for the full agency | [Architecture](agents/) |
| CEO loop is idempotent — safe to trigger multiple times without duplicate actions | [Design](agents/ceo-loop.md) |
| `launchctl list \| grep paperclip` — verify CEO daemon running at session start | [Startup check](../claude-ai-system/automations/bin/auto-troubleshoot) |
| CEO decisions are time-stamped + logged — full audit trail in `/api/decisions` | [Compliance](http://127.0.0.1:3100) |
| HMZ overrides any CEO decision via `POST /api/decisions/override` | [Authority](agents/authority.md) |

<a id="tips-api"></a>■ **API Reference (6)**

| Tip | Source |
|-----|--------|
| `curl http://127.0.0.1:3100/api/status` — health check (should return `{"status":"ok"}`) | [API](http://127.0.0.1:3100) |
| `GET /api/goals` — all 20 active strategic goals with progress | [API](http://127.0.0.1:3100) |
| `GET /api/leads?score_min=80&date=today` — today's hot leads | [API](http://127.0.0.1:3100) |
| `GET /api/kpi/scorecard?date=today` — today's 28-KPI health report | [API](http://127.0.0.1:3100) |
| `GET /api/intel/latest` — latest competitor intelligence brief | [API](http://127.0.0.1:3100) |
| `POST /api/ceo-loop/trigger` — manual CEO cycle (use after major changes) | [API](http://127.0.0.1:3100) |

<a id="tips-eng"></a>■ **Scheduled Engines (5)**

| Tip | Source |
|-----|--------|
| Lead engine geo blacklist: India, Pakistan, Bangladesh, Philippines, Israel — hardcoded | [HMZ rule](../hmz-paperclip-lead-engine/) |
| Content engine quality gate: fail → draft queue, not published — safe failure | [Error handling](../hmz-paperclip-content-engine/) |
| Intel engine: Meta Ad Library is ground truth — weight 3x over news | [Intel SOP](../hmz-paperclip-intel-engine/) |
| KPI monitor: >20% below target = RED → CEO escalation within next 6h cycle | [Threshold](../hmz-paperclip-kpi-monitor/) |
| Trends scanner Mon (most important) — covers weekend announcements | [Schedule logic](../hmz-paperclip-trends-scanner/) |

<a id="tips-agents"></a>■ **Agent Management (5)**

| Tip | Source |
|-----|--------|
| All 50 agents use Tier 0 routing — zero Claude tokens for agent sub-tasks | [G0DM0D3](../hmz-g0dm0d3/) |
| Agent output quality scores tracked — CEO loop reduces assignments for underperforming agents | [Self-improvement](agents/) |
| BDM agents skip Upwork/Freelancer.com/PeoplePerHour — LinkedIn and Indeed only | [HMZ platform rule](agents/bdm/) |
| PPC agents never change client budgets without logging to Paperclip API first | [Audit rule](agents/ppc/) |
| Content agents never post without passing quality gate (hook strength check) | [Content rule](agents/) |

<a id="tips-debug"></a>■ **Debug (4)**

| Tip | Source |
|-----|--------|
| API 503 → `launchctl start ai.hmz.paperclip` | [Runbook](launchagents/) |
| Port 3100 conflict → `lsof -i :3100` to find conflicting process | [Debug](launchagents/) |
| Company ID always `c5066522-bacc-4a28-b700-6590cbe366ec` — never change | [Config](http://127.0.0.1:3100) |
| CEO loop logs at `~/Library/Logs/paperclip-ceo-loop.log` | [Log location](launchagents/) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **Autonomous CEO operations** | Hiring a human COO/CEO ($150K+/yr) |
| **50-agent org management** | [Trello](https://trello.com), [Asana](https://asana.com), [Monday](https://monday.com) — passive task boards, not autonomous |
| **Daily lead engine** | [Clay](https://clay.com), [Instantly](https://instantly.ai) — manual trigger, per-lead pricing |
| **Daily content engine** | [Taplio](https://taplio.com), [Buffer](https://buffer.com), [Hootsuite](https://hootsuite.com) — no generation |
| **Daily competitor intel** | [Crayon](https://crayon.co), [Klue](https://klue.com) — $500+/mo, no autonomous brief |
| **KPI monitoring** | [Databox](https://databox.com), [Klipfolio](https://klipfolio.com) — passive dashboards |
| **Authority matrix** | Unstructured — HMZ decides everything manually (bottleneck) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-digiminds-ceo&type=Date)](https://star-history.com/#hmzainjamil/hmz-digiminds-ceo&Date)