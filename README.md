# hmz-digiminds-ceo
DigiMinds Global AI CEO — autonomous business operations, client pipeline, and growth automation.

![ceo](https://img.shields.io/badge/role-AI_CEO-orange?style=flat&labelColor=555)
![company](https://img.shields.io/badge/company-DigiMinds_Global-blue?style=flat&labelColor=555)
![status](https://img.shields.io/badge/status-live-green?style=flat&labelColor=555)
![endpoint](https://img.shields.io/badge/endpoint-127.0.0.1%3A3100-lightgrey?style=flat&labelColor=555)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat&labelColor=555)

[Concepts](#-concepts) · [Architecture](#️-architecture) · [Tips](#-tips-and-tricks-22) · [Kills](#️-startups--businesses) · [Stars](#star-history)

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**CEO Loop**](ceo-loop/main.js) | `ceo-loop/main.js` | Autonomous decision engine — monitors KPIs, triggers actions, runs 24/7 [![live](https://img.shields.io/badge/status-live-green?style=flat&labelColor=555)] |
| [**Client Pipeline**](pipeline/client-tracker.js) | `pipeline/client-tracker.js` | Tracks leads → proposals → retainers — LinkedIn + Indeed sources only |
| [**BDM Outreach**](outreach/bdm.js) | `outreach/bdm.js` | Automated outreach sequences — personalized cover letters per prospect |
| [**PDF Audit Engine**](audits/pdf-engine.py) | `audits/pdf-engine.py` | ReportLab 11-page 360° audits — brand palette from client URL |
| [**KPI Monitor**](monitoring/kpi.js) | `monitoring/kpi.js` | Real-time metrics — ROAS, CPL, CTR, conversion rate tracking |
| [**Content Engine**](content/engine.js) | `content/engine.js` | LinkedIn posts, case studies, Reddit (1/day max throttle) |
| [**Competitor Intel**](intel/competitor.js) | `intel/competitor.js` | Weekly scrape of competitor pricing, services, reviews |
| [**Proposal Generator**](proposals/generator.py) | `proposals/generator.py` | Per-prospect PDF proposals with business name + brand palette |
| [**Email Sequences**](emails/sequences.js) | `emails/sequences.js` | Cold outreach → follow-up → close — B2B digital marketing focus |
| [**Revenue Tracker**](finance/revenue.js) | `finance/revenue.js` | MRR, ARR, pipeline value tracking — feeds CEO Loop decisions |
| [**Paperclip Integration**](paperclip/sync.js) | `paperclip/sync.js` | DigiMinds instance of Paperclip AI OS — company ID c5066522 |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**Geo Blacklist Filter**](filters/geo-blacklist.js) | `filters/geo-blacklist.js` | Blocks India, Pakistan, Bangladesh, Philippines, Israel from client targeting |
| [**Platform Filter**](filters/platform.js) | `filters/platform.js` | LinkedIn + Indeed only — Upwork, Freelancer.com, PeoplePerHour permanently removed |
| [**Auto Troubleshoot**](ops/troubleshoot.sh) | `ops/troubleshoot.sh` | SessionStart check — verifies CEO loop running, LaunchAgents healthy |

## ⚙️ ARCHITECTURE

```
DigiMinds AI CEO OS
  ┌─────────────────────────────────────┐
  │  Paperclip AI (127.0.0.1:3100)      │
  │  Company: c5066522-bacc-4a28-...    │
  │                                     │
  │  CEO Loop (24/7 daemon)             │
  │    ├─ Morning: KPI review           │
  │    ├─ Daytime: BDM outreach         │
  │    ├─ Evening: content posting      │
  │    └─ Night: competitor intel       │
  └─────────────────────────────────────┘
          │
          ▼
  Tool Layer (Tier 0 models)
    ├─ Groq → analysis
    ├─ Gemini → research
    ├─ DeepSeek → code/proposals
    └─ GPT-4o-mini → content
```

| Module | Frequency | Model | Output |
|--------|-----------|-------|--------|
| KPI Monitor | Hourly | Groq | Slack alert if metric drops |
| BDM Outreach | 08:00 daily | GPT-4o-mini | 3-5 personalized messages |
| Content Engine | 10:00 daily | Gemini | LinkedIn post + Reddit (throttled) |
| Competitor Intel | Weekly Sun | DeepSeek | Competitor report PDF |
| Audit Generator | On-demand | ReportLab | 11-page PDF per prospect |
| CEO Loop | Continuous | Groq | Decision log + actions |

## 💡 TIPS AND TRICKS (22)

[ops](#tips-ops) · [bdm](#tips-bdm) · [content](#tips-content) · [reports](#tips-reports)

<a id="tips-ops"></a>■ **Operations (6)**

| Tip | Source |
|-----|--------|
| CEO loop at 127.0.0.1:3100 — always verify running before session with `curl localhost:3100/health` | [HMZ](https://github.com/hmzainjamil) |
| Company ID `c5066522-bacc-4a28-b700-6590cbe366ec` — required for all Paperclip API calls | [HMZ](https://github.com/hmzainjamil) |
| LaunchAgent `KeepAlive=true` — CEO loop restarts within 10s of any crash | [HMZ](https://github.com/hmzainjamil) |
| `auto-troubleshoot` SessionStart hook verifies CEO loop before every Claude session | [HMZ](https://github.com/hmzainjamil) |
| All files saved to ~/Downloads — never Desktop (enforced across all PDF engines) | [HMZ](https://github.com/hmzainjamil) |
| Log CEO loop decisions to `~/.claude/logs/ceo-loop.log` — review weekly | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-bdm"></a>■ **Business Development (6)**

| Tip | Source |
|-----|--------|
| LinkedIn + Indeed only — Upwork/Freelancer.com/PPH permanently blacklisted | [HMZ](https://github.com/hmzainjamil) |
| Geo blacklist: India, Pakistan, Bangladesh, Philippines, Israel — never target | [HMZ](https://github.com/hmzainjamil) |
| Cover letter rules: no formatting fluff, no skill lists, result-first tone | [HMZ](https://github.com/hmzainjamil) |
| Per-prospect PDF: include business name, city, brand palette from their URL | [HMZ](https://github.com/hmzainjamil) |
| Reddit posting cap: max 1 post/day — account on bot-watch, never schedule more | [HMZ](https://github.com/hmzainjamil) |
| LinkedIn Chrome profile: always `--profile-directory=Profile 1` — never sign out | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-content"></a>■ **Content Engine (5)**

| Tip | Source |
|-----|--------|
| LinkedIn posts: thought leadership, no sales pitch in first post — warm → convert | [HMZ](https://github.com/hmzainjamil) |
| Use Gemini for first-draft content — cheap, fast, 1M context for brand alignment | [HMZ](https://github.com/hmzainjamil) |
| Case study format: problem → solution → results (ROAS numbers required) | [HMZ](https://github.com/hmzainjamil) |
| Reddit: value-first, no agency links in body — 30% of posts get removed otherwise | [HMZ](https://github.com/hmzainjamil) |
| Content calendar: batch-generate week ahead on Sunday via CEO loop | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-reports"></a>■ **Audit PDF Reports (5)**

| Tip | Source |
|-----|--------|
| 11 pages minimum per audit — client expects comprehensive, not surface-level | [HMZ](https://github.com/hmzainjamil) |
| Brand palette from client URL: Playwright screenshot + color extraction (top 5 colors) | [HMZ](https://github.com/hmzainjamil) |
| ReportLab: never `canvas.drawString` for body — always `platypus.Paragraph` | [HMZ](https://github.com/hmzainjamil) |
| Include competitor benchmarks in every audit — makes report 3x more valuable | [HMZ](https://github.com/hmzainjamil) |
| Per-prospect cover page: their logo + business name + city pulled automatically | [HMZ](https://github.com/hmzainjamil) |

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **AI CEO Loop** | [Lindy AI](https://lindy.ai), [Beam AI](https://beam.ai), [Artisan](https://artisan.co) |
| **BDM Pipeline** | [Apollo.io](https://apollo.io), [Outreach](https://outreach.io), [Salesloft](https://salesloft.com) |
| **Audit PDF Engine** | [AgencyAnalytics](https://agencyanalytics.com), [DashThis](https://dashthis.com), [Databox](https://databox.com) |
| **Content Engine** | [Buffer](https://buffer.com), [Hootsuite](https://hootsuite.com), [Sprout Social](https://sproutsocial.com) |
| **Competitor Intel** | [Similarweb](https://similarweb.com), [SEMrush](https://semrush.com), [SpyFu](https://spyfu.com) |
| **Email Sequences** | [Instantly](https://instantly.ai), [Lemlist](https://lemlist.com), [Smartlead](https://smartlead.ai) |

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-digiminds-ceo&type=Date)](https://star-history.com/#hmzainjamil/hmz-digiminds-ceo&Date)
