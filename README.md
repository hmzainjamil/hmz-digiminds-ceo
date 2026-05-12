# hmz-digiminds-ceo
> DigiMinds AI-powered digital marketing agency OS — Paperclip CEO layer, MAE orchestration, zero-human operations.

[![paperclip](https://img.shields.io/badge/Paperclip-CEO--layer-blue?style=flat&labelColor=555)](https://github.com/paperclipai/paperclip)
[![mae](https://img.shields.io/badge/MAE-12--agents-green?style=flat&labelColor=555)](.)
[![agency](https://img.shields.io/badge/agency-DigiMinds-orange?style=flat&labelColor=555)](https://digiminds.org)
[![zero-human](https://img.shields.io/badge/ops-zero--human-purple?style=flat&labelColor=555)](.)
[![license](https://img.shields.io/badge/license-MIT-lightgrey?style=flat&labelColor=555)](LICENSE)

[concepts](#concepts) · [architecture](#architecture) · [tips](#tips) · [startups](#startups) · [star](#star)

---

## 🧠 CONCEPTS <a id="concepts"></a>

| Feature | Location | Description |
|---|---|---|
| [**Paperclip CEO Layer**](paperclip/) | `paperclip/` | Open-source company OS at localhost:3100 — org charts, goals, budgets, agent tasks |
| [**MAE Daily Ops**](workflows/digiminds-daily.json) | `workflows/` | 4-step daily workflow: systems → queue → execute → report |
| [**Agency Email Pipeline**](automations/agency-email-pickup) | `automations/` | Auto-reads client emails → queues responses → sends via Gmail SMTP |
| [**BDM Pipeline**](automations/hmz-bdm-catchup) | `automations/` | LinkedIn + Indeed job scanning → cover letter generation → auto-apply |
| [**Client Audit PDFs**](scripts/audit-pdf/) | `scripts/audit-pdf/` | 11-page ReportLab 360° audit with client brand palette from URL |
| [**Lead Gen Pipeline**](scripts/lead-gen/) | `scripts/lead-gen/` | Vibe Prospecting + Apollo → Excel → personalized cold outreach |
| [**KPI Dashboard**](scripts/kpi/) | `scripts/kpi/` | Google Ads + Meta Ads metrics → Excel dashboard daily |
| [**Competitor Intel**](scripts/intel/) | `scripts/intel/` | Meta Ad Library scrape + Apollo enrich → swipe file |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [**Codex Delegation**](workflows/codex-delegation.json) | `workflows/` | Delegates complex coding to OpenAI Codex agent — reads repo, edits, tests |
| [**OpenCLI Integration**](automations/opencli/) | `automations/opencli/` | 90+ site adapters — HackerNews, Bilibili, Twitter, Reddit, zero token cost |
| [**Deer Flow Research**](automations/deer-flow/) | `automations/deer-flow/` | ByteDance deep research pipeline for market intelligence |

---

## ⚙️ ARCHITECTURE <a id="architecture"></a>

```
DigiMinds Agency OS
         │
┌────────┴────────────────────────────────┐
│           Paperclip CEO Layer            │
│  localhost:3100                          │
│  Agents · Goals · Budgets · Org chart   │
└────────────────────┬────────────────────┘
                     │
         MAE Orchestration Engine
                     │
    ┌────────────────┼────────────────┐
    │                │                │
Email Pipeline   Lead Gen         BDM Pipeline
    │                │                │
Gmail SMTP    Vibe+Apollo       LinkedIn+Indeed
    │                │                │
Client comms    Excel leads     Cover letters
```

| Workflow | Trigger | Output |
|---|---|---|
| digiminds-daily | 8am LaunchAgent | Status report + task queue |
| agency-email-pickup | SessionStart hook | Queued email responses |
| hmz-bdm-catchup | SessionStart hook | New leads + applications |
| audit-pdf-gen | On demand | 11-page branded PDF |
| lead-gen | On demand | Excel + email sequence |

---

## 💡 TIPS AND TRICKS (16) <a id="tips"></a>

[paperclip](#tips-pc) · [email-pipeline](#tips-email) · [lead-gen](#tips-lead) · [bdm](#tips-bdm)

<a id="tips-pc"></a>
■ **Paperclip CEO Layer (4)**

| Tip | Source |
|---|---|
| Start: `cd ~/installed-repos/paperclip && pnpm dev` — auto-migrates PostgreSQL on port 54329 | [Paperclip AI](https://github.com/paperclipai) |
| Company ID `c5066522-bacc-4a28-b700-6590cbe366ec` — use in API calls to scope to DigiMinds | [hmzainjamil](https://github.com/hmzainjamil) |
| Set agent goals in Paperclip dashboard — MAE reads pending goals on `mae daily` | [Paperclip AI](https://github.com/paperclipai) |
| Paperclip budget tracking: each MAE run logs cost to Paperclip via `paperclip_sync()` | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-email"></a>
■ **Email Pipeline (4)**

| Tip | Source |
|---|---|
| Gmail credentials in macOS Keychain — never in files. Run `python3 send_email.py --setup` once | [hmzainjamil](https://github.com/hmzainjamil) |
| Agency email pickup reads Gmail via IMAP — filters by `from:@client.com` and `subject:` | [hmzainjamil](https://github.com/hmzainjamil) |
| Response drafts go to TCC queue first — review with `tcc queue` before `tcc fire all` | [hmzainjamil](https://github.com/hmzainjamil) |
| Use Kimi K2.6 for email drafting — 262K context reads full thread history before replying | [Moonshot AI](https://moonshot.cn) |

<a id="tips-lead"></a>
■ **Lead Gen (4)**

| Tip | Source |
|---|---|
| Vibe Prospecting: `fetch-entities` → `enrich-prospects` → `export-to-csv` in one MCP chain | [Vibe Prospecting](https://vibe.co) |
| Apollo enrichment adds owner name + email — run `apollo_people_match` after Vibe fetch | [Apollo.io](https://apollo.io) |
| Output always to `~/Downloads/leads.xlsx` — 11-column format, auto-width, bold headers | [hmzainjamil](https://github.com/hmzainjamil) |
| Personalized cold email per lead: `llm-burst "write cold email for {name} at {company}"` | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-bdm"></a>
■ **BDM Pipeline (4)**

| Tip | Source |
|---|---|
| Only LinkedIn and Indeed — Upwork, Freelancer.com, PPH permanently removed | [hmzainjamil](https://github.com/hmzainjamil) |
| Geo blacklist enforced: India, Pakistan, Bangladesh, Philippines, Israel never targeted | [hmzainjamil](https://github.com/hmzainjamil) |
| Cover letters use `feedback_zulqarnain_cover_letter_rules.md` — formatting rules enforced | [hmzainjamil](https://github.com/hmzainjamil) |
| HMZ resume data in `user_zulqarnain_profile.md` — auto-injected into all applications | [hmzainjamil](https://github.com/hmzainjamil) |

---

## ☠️ STARTUPS / BUSINESSES <a id="startups"></a>

| Feature | Replaced |
|---|---|
| **Paperclip CEO company OS** | [Notion AI](https://notion.so/ai), [Monday.com](https://monday.com), [ClickUp](https://clickup.com) |
| **MAE agency operations** | [Zapier](https://zapier.com), [Make.com](https://make.com), [Workato](https://workato.com) |
| **Automated lead gen pipeline** | [Apollo.io](https://apollo.io), [Hunter.io](https://hunter.io), [ZoomInfo](https://zoominfo.com) |
| **AI audit PDF generation** | [AgencyAnalytics](https://agencyanalytics.com), [Reportz](https://reportz.io) |
| **BDM auto-apply pipeline** | [Jobscan](https://jobscan.co), [LazyApply](https://lazyapply.com), [Simplify Jobs](https://simplify.jobs) |

---

## Star History <a id="star"></a>

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/hmz-digiminds-ceo&type=Date)](https://star-history.com/#hmzainjamil/hmz-digiminds-ceo&Date)
