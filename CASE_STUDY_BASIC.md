# Amplitude Analytics — Strideway (Basic)

*⭐⭐⭐ Built · event segmentation, real Amplitude account*

> Exported from the portfolio page on 2026-10-19. The live page is the canonical version: https://bhawnamanglapm.github.io/travel-tech-more.html#case-amplitude-strideway-basic

- 3,000 users · 52,082 events, real Amplitude account
- 10-event tracking plan built via the Amplitude API
- Fictional habit app (Strideway), documented behavior model
- 5 segmentation charts, real screenshots

**Tools used:** Amplitude (tracking plan, Event Segmentation), Python + Amplitude's HTTP API V2 for data ingestion.

### Why This Exists

Amplitude/Mixpanel are listed among the tools worth having, alongside SQL — but with no prior hands-on use. This project is the real thing, not a simulation: a genuine Amplitude organization (free Starter plan), a tracking plan built for real through Amplitude's own API, and real usage data sent through Amplitude's actual ingestion pipeline for a fresh scenario — "Strideway," a fictional fitness/habit-tracking app.

### My Approach

First, a real tracking plan: 10 events (Sign Up, Complete Onboarding, Log Workout, Hit Streak Milestone, View Paywall, Start Free Trial, Upgrade to Premium, Cancel Subscription, Open App, Invite Friend), 7 event properties, and 5 user properties, created directly in the live Amplitude project — this is the part of the job that happens before any engineer writes a tracking call. Then a documented synthetic dataset: 3,000 users and 52,082 events, with every behavioral difference modeled on a deliberate, real pattern rather than random noise — Referral- and Organic-acquired users complete onboarding and retain far better than Influencer-driven signups (lower-intent curiosity clicks, a real growth pattern), and hitting a 7-day workout streak sharply raises the odds of seeing — and converting on — the premium paywall shortly after (a real behavioral-commitment upsell pattern). That data was sent into the actual Amplitude project through Amplitude's own HTTP API, run from a Python script with my own API key — real ingestion, not fabricated chart data.

### Key Findings

- **Daily signups climbed from single digits in May to 50-65/day by late July** across all 4 channels, with Organic consistently the largest share — the deliberate growth ramp built into the dataset, confirmed in real Amplitude charts, not just the generator script.
- **Onboarding completion clearly splits by channel**: Organic and Referral-driven signups convert to a completed profile far more consistently than Paid Social or Influencer signups — visible directly in the segmentation chart, matching the model's Referral 88%/Organic 81% vs. Influencer 55% completion rates.
- **Cardio and Strength are Strideway's most-logged workout types**, HIIT and Yoga meaningfully behind — a simple distribution chart, still a real product-mix read.
- **iOS modestly outpaces Android** (55/45 split, matching the model) — a simple platform check, useful before reading too much into any other channel's numbers.

[image: Amplitude Segmentation chart: Daily Unique Users for Sign Up Event, May 1 to Aug 13, grouped by signup_channel — Organic (blue) consistently highest, all 4 channels trending upward] [image: Amplitude Segmentation chart: Daily Unique Users Logging Workouts by Workout Type — Cardio and Strength leading, HIIT and Yoga lower, all trending upward with overall growth] [image: Amplitude Segmentation chart: Daily Unique Users Completing Onboarding by Signup Channel — Organic (blue) clearly highest, Referral/Paid Social/Influencer lower and closer together] [image: Amplitude Segmentation chart, full browser view: Daily Unique Sign Up Users by Platform — iOS (blue) modestly higher than Android (green), both trending upward]

All 4 screenshots are real charts from my own live Amplitude project, built through the actual Amplitude UI against the ingested dataset — the platform chart left with the full browser window visible rather than cropped to just the chart.

### Beyond the Guide: Amplitude's Own Default Dashboard

Past the specific charts in the practice guide, I also opened Amplitude's auto-generated "User Activity" notebook — a template it builds automatically once real data starts flowing in, not something I set up. It confirmed the data pipeline end to end: 243 daily active users, new-signup and returning-user trends, and a visible retention decay curve, all matching the pattern the dataset was built around. It also surfaced something worth understanding rather than dismissing: the device/country/platform breakdown panels all show **"Invalid chart definition."** That's not the pipeline breaking — those panels reference Amplitude's own auto-captured device/geo properties, normally filled in by a real mobile/web SDK. Since this dataset was sent server-side through the HTTP API rather than a live app SDK, those specific built-in properties were never populated — expected, not a bug, and a real distinction between "data sent by a script" and "data sent by an instrumented app" worth knowing.
  [ [image: Amplitude's auto-generated User Activity dashboard: 243 daily active users, new-user and returning-user trend charts, a retention decay curve, and device/country/platform breakdown panels showing 'Invalid chart definition' since this data was sent server-side without SDK-captured device properties] ](https://bhawnamanglapm.github.io/projects/amplitude-strideway/screenshots/basic-04-user-activity-overview.png)

Amplitude's own auto-generated dashboard, exported as PDF directly from the tool — included as-is, "Invalid chart definition" panels and all, rather than cropped down to only the clean parts.

### Quick recall

| Section | Summary |
|---|---|
| **Problem** | Amplitude is listed as a skill worth having, but with no prior hands-on use demonstrated anywhere on the site — the gap this project closes with a real account and real data, not a simulation. |
| **Research steps** | Built a real 10-event tracking plan (7 event properties, 5 user properties) directly in a live Amplitude project, the part of the job that happens before an engineer writes a tracking call → generated a documented synthetic dataset (3,000 users, 52,082 events) with every behavioral difference modeled on a real growth pattern → sent it through Amplitude's own HTTP API with a personal key, real ingestion rather than fabricated chart data → opened Amplitude's own auto-generated dashboard as a second, independent check and investigated rather than dismissed the "Invalid chart definition" panels it surfaced. |
| **Solution** | 5 real segmentation charts (signup by channel, workout type distribution, onboarding completion by channel, platform split) plus Amplitude's own auto-generated User Activity dashboard, all built against live ingested data. |
| **Conclusion** | The "Invalid chart definition" panels weren't a bug — they're the expected result of sending data server-side via API instead of through a live app SDK, which never populates Amplitude's auto-captured device/geo properties. Understanding that distinction, not just getting clean charts, is the real finding. |

Guide[practice guide →](https://bhawnamanglapm.github.io/projects/amplitude-strideway/AMPLITUDE_GUIDE.md) Dataset[generator script →](https://bhawnamanglapm.github.io/projects/amplitude-strideway/generate_dataset.py) NextAdvanced: funnels, retention, cohorts (T33) →
