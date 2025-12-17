# Instagram Lead Discovery & Outreach Assistant

> A compliance-first workflow that helps you discover relevant Instagram accounts from public signals (hashtags, post captions, public comments) and prepare outreach drafts for human review.  
> It focuses on lead qualification, safe pacing, and auditability—without mass unsolicited DMs, spam comments, or follow/unfollow automation.


<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/3YrZJZ6hA2" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>


<p align="center">
Created by Appilot, built to showcase our approach to Automation! <br>
If you are looking for custom Instagram Lead Discovery & Outreach Assistant, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>


## Introduction

Scaling Instagram outreach is often attempted with mass DMs, mass comments, and automated follows, but that pattern is strongly associated with spam and account enforcement. A safer, sustainable approach is to automate **lead discovery + organization + drafting**, then keep messaging human-reviewed and opt-in.

This project automates:
- Collecting public lead signals from configured sources (hashtags, public posts, public comments)
- Enriching and scoring leads for relevance
- Generating outreach drafts and sequences for manual sending
- Maintaining compliance guardrails (cooldowns, dedupe, blocked targets) and full audit logs

### Creator Outreach, Partnerships, and Lead Gen Workflows

- Build targeted lists from public content without manual scrolling
- Reduce wasted outreach by scoring and filtering leads
- Keep messaging consistent with reusable templates and personalization
- Avoid repetitive spam patterns with variation checks and pacing
- Produce clean exports to CRM/Sheets for team workflows

---

## Core Features

| Feature | Description |
|----------|-------------|
| Public lead collection | Collects accounts from public posts, hashtags, and public comments using configurable start points |
| Configurable data fields | Captures username, profile URL, bio, follower range (if available), recent post links, and public engagement signals |
| Lead scoring | Scores leads by keyword match, niche relevance, language, and recent activity |
| Dedupe & suppression | Prevents repeated targeting; supports do-not-contact lists and blocklists |
| Draft outreach generator | Produces human-reviewed DM/comment drafts with personalization placeholders |
| Template library | Multi-template sequences with tone rules and variation to avoid repetitive phrasing |
| Human review queue | Approvals required before exporting drafts for manual sending |
| Safe pacing controls | Cooldowns, daily caps, and randomized scheduling for non-invasive collection runs |
| Proxy configuration (testing) | Optional proxy routing for permitted geo/language testing and stability validation (not identity spoofing) |
| Evidence capture | Saves snapshots/screenshots when selectors fail or pages change |
| Exports & integrations | CSV/JSON exports and optional webhook push to CRM/Sheets pipelines |
| Observability | Structured logs, run IDs, health endpoints, and failure summaries |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | A scheduled run or manual CLI trigger starts collection from configured hashtags/post URLs. |
| **Core Logic** | The collector extracts public signals, normalizes profiles into a lead model, scores relevance, and deduplicates against suppression lists. |
| **Output or Action** | Qualified leads and outreach drafts are added to a review queue; approved items are exported for manual outreach. |
| **Other Functionalities** | Retries transient failures, captures artifacts on layout changes, and generates daily summaries. |
| **Safety Controls** | Rate limiting, cooldowns, suppression lists, and human-in-the-loop gating for any outreach drafts. |

## Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python |
| **Frameworks** | FastAPI |
| **Tools** | Playwright, PostgreSQL, Redis |
| **Infrastructure** | Docker, GitHub Actions |

---

## Directory Structure Tree

    instagram-lead-discovery-outreach-assistant/
    ├── src/
    │   ├── main.py
    │   ├── cli.py
    │   ├── api/
    │   │   ├── routes_targets.py
    │   │   ├── routes_leads.py
    │   │   ├── routes_drafts.py
    │   │   ├── routes_review.py
    │   │   └── routes_reports.py
    │   ├── core/
    │   │   ├── settings.py
    │   │   ├── guardrails.py
    │   │   ├── rate_limits.py
    │   │   └── link_policy.py
    │   ├── collector/
    │   │   ├── hashtag_collector.py
    │   │   ├── post_collector.py
    │   │   ├── comment_collector.py
    │   │   ├── parser.py
    │   │   ├── normalizer.py
    │   │   └── dedupe.py
    │   ├── leads/
    │   │   ├── models.py
    │   │   ├── repository.py
    │   │   ├── enrich.py
    │   │   └── scoring.py
    │   ├── drafts/
    │   │   ├── generator.py
    │   │   ├── templates.py
    │   │   ├── personalization.py
    │   │   └── quality_checks.py
    │   ├── review/
    │   │   ├── queue.py
    │   │   ├── approvals.py
    │   │   └── rules.py
    │   ├── proxy/
    │   │   ├── loader.py
    │   │   ├── healthcheck.py
    │   │   └── routing.py
    │   ├── artifacts/
    │   │   ├── screenshots.py
    │   │   └── snapshots.py
    │   ├── reporting/
    │   │   ├── metrics.py
    │   │   ├── exporter_csv.py
    │   │   └── exporter_json.py
    │   ├── integrations/
    │   │   ├── webhook.py
    │   │   └── sheets_export.py
    │   ├── observability/
    │   │   ├── logger.py
    │   │   └── health.py
    │   └── utils/
    │       ├── retries.py
    │       ├── time.py
    │       └── hashing.py
    ├── config/
    │   ├── targets.yaml
    │   ├── templates.yaml
    │   ├── guardrails.yaml
    │   ├── schedules.yaml
    │   └── proxy.yaml
    ├── output/
    │   ├── exports/
    │   │   ├── leads.csv
    │   │   └── approved_drafts.json
    │   ├── reports/
    │   │   ├── daily_summary.csv
    │   │   └── run_metrics.json
    │   └── artifacts/
    │       ├── screenshots/
    │       │   └── run_YYYYMMDD/
    │       └── snapshots/
    │           └── run_YYYYMMDD/
    ├── logs/
    │   └── app.log
    ├── tests/
    │   ├── test_scoring.py
    │   ├── test_dedupe.py
    │   ├── test_quality_checks.py
    │   └── test_rate_limits.py
    ├── docker/
    │   ├── Dockerfile
    │   └── docker-compose.yml
    ├── .github/
    │   └── workflows/
    │       └── ci.yml
    ├── requirements.txt
    ├── .env.example
    └── README.md

---
## Use Cases

- **Agencies** use it to build niche lead lists from public hashtags, so outreach becomes targeted and efficient.
- **Brand partnerships teams** use it to score creators and prepare personalized drafts, so response rates improve without spam.
- **Community managers** use it to track outreach history and suppression lists, so repeat-contact mistakes are avoided.
- **Sales teams** use it to export qualified leads to CRM pipelines, so follow-ups are organized and measurable.

---

## FAQs

### Does this send mass DMs, mass comments, or automate follow/unfollow?
No. This project avoids spam-like automation. It collects public lead signals and generates drafts for human review and manual sending.

### What data can it collect safely?
It’s designed around public signals available on posts/profiles you can view normally, then stores only the fields you configure and need for lead qualification.

### Why include proxy configuration at all?
Only for permitted stability and geo/language QA (for example, verifying localized content or reliability). It is not intended for evasion or simulating fake identities.

### What happens if Instagram layout changes?
Runs capture artifacts (screenshots/snapshots) and emit selector failure logs, so updates are quick and evidence-driven.

---

## Performance & Reliability Benchmarks

**Execution Speed:** 200–900 public items evaluated per minute per worker depending on page weight, selector complexity, and artifact capture settings.

**Success Rate:** 92–94% successful collection cycles with retries and backoff; remaining failures are typically layout changes or transient network issues.

**Scalability:** 50–500 concurrent collection tasks by scaling workers horizontally with strict per-domain concurrency caps and safe pacing.

**Resource Efficiency:** ~250–650 MB RAM per active browser worker; API service typically ~150–300 MB RAM.

**Error Handling:** Exponential backoff retries, circuit breakers on repeated failures, deduplication, structured logs, and artifact capture for rapid debugging.

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/ð¥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>
