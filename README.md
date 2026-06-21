<div align="center">

<img src="assets/hero.png" alt="PixlForge Sentinel" width="100%">

# ðŸ›°ï¸ PixlForge Sentinel

### Budget-gated B2B lead intelligence

*You run it. You deliver a clean CSV + branded PDF. Spending can never exceed your cap.*

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Claude](https://img.shields.io/badge/AI-Claude_Haiku_4.5-14b8a6)](https://www.anthropic.com/)
[![Playwright](https://img.shields.io/badge/Render-Playwright-2EAD33?logo=microsoftedge&logoColor=white)](https://playwright.dev/)
[![SQLite](https://img.shields.io/badge/Audit-SQLite-003B57?logo=sqlite&logoColor=white)](https://www.sqlite.org/)
[![License](https://img.shields.io/badge/License-Proprietary-1f2937)](#-license)

</div>

---

## ðŸŽ¬ ~55-second demo

> **â–¶ [Watch the narrated walkthrough â†’](assets/sentinel-teaser.mp4)** *(AI-narrated + subtitled)*

<div align="center">

[<img src="assets/screenshots/01-terminal.png" alt="Watch the demo" width="80%">](assets/sentinel-teaser.mp4)

</div>

<video src="https://github.com/Namanjain723/pixlforge-sentinel/raw/main/assets/sentinel-teaser.mp4" controls width="100%"></video>

---

## ðŸ’¡ Why it exists

Apollo, Hunter and ZoomInfo are great at scale â€” and terrible at **niche** targeting and **honest** verification. The naive DIY approach is worse: directory scraping (Yelp / YellowPages / Google) gets you IP-banned and violates ToS, and DIY SMTP on port 25 is blocked by most ISPs so it marks everything "unverifiable".

**Sentinel keeps every good idea from that brief â€” budget cap, AI scoring, catch-all flagging, full audit, CSV + PDF â€” but swaps the fragile parts for reliable, legitimate sources.**

---

## âš™ï¸ How it works â€” 5 stages, one hard cap

![Pipeline](assets/screenshots/02-pipeline.png)

| Stage | Engine (free combo default) | Why |
|---|---|---|
| **â‘  Discover** | Google Places API | Legitimate, never IP-banned, structured business data |
| **â‘¡ Enrich** | **Playwright** render + on-site email extraction | Catches emails injected by JavaScript a static fetch can't see |
| **â‘¢ Qualify** | **Claude Haiku 4.5** | A 1â€“5 fit score + a one-line reason per lead |
| **â‘£ Verify** | **SMTP** probe + catch-all check | Real RCPT-level deliverability; honest catch-all detection â€” no false "verified" |
| **â‘¤ Deliver** | CSV + branded PDF | Client-ready, sorted best-first, with an honest status legend |

> **Start free, upgrade when revenue justifies it.** Out of the box Sentinel runs on a free verification + scraping stack (Playwright + SMTP) â€” only Claude + Google Places cost anything. Paste a **Hunter.io** key to auto-upgrade and additionally *find* decision-maker emails that aren't published anywhere.

---

## ðŸ–¥ï¸ One command, start to finish

```bash
python sentinel.py --niche "Marketing Agencies in Austin Texas" --budget 2 --max-leads 25 --yes
```

![Terminal run](assets/screenshots/01-terminal.png)

**Three ways to run, safest â†’ live:**

| Command | Spends money? | What it proves |
|---|---|---|
| `--dry-run` | No | The whole pipeline works (mock data) |
| `--live-test` | A few cents | Keys + billing + connectivity healthy â€” and the free stack (port 25 open, Playwright renders) |
| *(normal run)* | Yes (capped) | Produces a real client deliverable |

---

## â›½ Budget control â€” the signature feature

![Budget ledger](assets/screenshots/04-budget-ledger.png)

Set `budget_cap_usd`. Before **every** paid action â€” each Claude call, each Places page, each Hunter find/verify â€” Sentinel checks whether it can afford it. If not, the run **halts gracefully** and still produces a report from whatever it completed. Every event is recorded in the `spend_ledger` table. **The run total can never exceed your cap.** No surprise bills â€” ever.

---

## ðŸ“¦ The deliverable your client receives

![PDF report](assets/screenshots/03-pdf-report.png)

A branded, dark-theme PDF (plus a CSV), sorted best-first, with an **honest status legend**:

- **VERIFIED** â€” inbox confirmed at the RCPT level
- **CATCH-ALL** â€” domain accepts everything; flagged for manual review
- **UNVERIFIABLE** â€” host (e.g. Microsoft) blocks live verification

> Sentinel never claims a 0% bounce rate. That transparency is a selling point, not a weakness.

---

## ðŸ§± Tech stack

**Python 3.11+** Â· **Playwright** (headless Chromium render) Â· **Anthropic SDK** (Claude Haiku 4.5) Â· **Google Places API** Â· **SMTP** RCPT verification Â· **SQLite** (runs, spend ledger, dedup) Â· **ReportLab** (branded PDF) Â· pluggable verifier providers (SMTP / Hunter / MX-basic).

```
sentinel.py            # CLI entry + pipeline orchestration
core/
  cost_gate.py         # unified USD budget enforcer (the signature feature)
  discovery.py         # Google Places business discovery
  scraper.py           # Playwright headless renderer (JS-injected emails)
  ai_analyzer.py       # Claude Haiku 4.5 qualification
  verifier.py          # verification dispatcher
  providers/           # pluggable verifiers (smtp, hunter, mx_basic)
  store.py             # SQLite: runs, spend_ledger, verified_leads
  reporter.py          # CSV + branded dark-theme PDF
business/              # SALES + MARKETING + LEGAL kit (pricing, gig, compliance)
```

---

## ðŸ’¼ Built to be sold as a service

Sentinel ships with a full **business kit** (`business/`): pricing & packages with ~99% margins, an order-intake checklist, a client one-pager, a ready-to-publish Fiverr gig, outreach templates, and a plain-English CAN-SPAM / GDPR / CASL compliance guide.

---

## ðŸ‘¤ Author

**Naman Jain** â€” PixlForge Studio
ðŸ“§ [info@pixlforgestudio.in](mailto:info@pixlforgestudio.in)
ðŸ”— [github.com/Namanjain723](https://github.com/Namanjain723)

## ðŸ“„ License

Â© PixlForge Studio. All rights reserved. This public repository is a **showcase** â€” documentation, screenshots and the demo video only. The full source is private.

---

<div align="center"><sub>PixlForge Sentinel â€” qualified leads, on a budget you control.</sub></div>
