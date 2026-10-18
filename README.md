# Amplitude product analytics on a fictional habit app (Basic and Advanced)

**Analytics practice project on a synthetic dataset, with Python ingestion script and screenshots.**

## In one minute

'Strideway' is a fictional fitness and habit app. A Python script generated 3,000 users and 52,082 events with behaviour modeled on deliberate patterns, and a second script sends them to Amplitude's HTTP API. The page says the data went into a real Amplitude organization on the free plan and that the tracking plan was created there. Basic covers event segmentation. Advanced covers a six-step funnel, retention by channel and cohorts, and a funnel under-reporting caused by Amplitude's default 1-day conversion window, which the page says was fixed by widening it to 90 days.

## Links

- Portfolio case study: https://bhawnamanglapm.github.io/travel-tech-more.html#case-amplitude-strideway-basic
- Portfolio case study: https://bhawnamanglapm.github.io/travel-tech-more.html#case-amplitude-strideway-advanced

## What is in this repo

| File | What it is |
|---|---|
| generate_dataset.py | Generates the synthetic users and events |
| events.jsonl | The generated events |
| send_to_amplitude.py | Sends the events to Amplitude's HTTP API; reads the key from the AMPLITUDE_API_KEY environment variable |
| AMPLITUDE_GUIDE.md | Setup and chart guide |
| screenshots/ | Amplitude chart screenshots (basic-01 to 05, advanced-01 to 05) |
| CASE_STUDY_BASIC.md, CASE_STUDY_ADVANCED.md | The write-ups, exported from the portfolio page |

## What is real, modeled or not verified

| Topic | Status |
|---|---|
| Synthetic data | The users and events are generated. The patterns (for example referral users retaining better) were built into the generator, so the charts reflect those assumptions and not real user behaviour. |
| Amplitude project not inspectable | The Amplitude organization and charts are the author's account and are not part of this repo. The screenshots are the only evidence here, and nothing was re-run. |
| No credentials | send_to_amplitude.py reads the API key from an environment variable. The only key text in the repo is the placeholder 'paste-your-api-key-here'. |
| Two cards, one repo | The Basic and Advanced portfolio cards use the same dataset, so they share this repo. |

## Provenance and credit

- Product owner, built with AI (Claude).
- Copied on 2026-10-19 from the `projects/amplitude-strideway` folder of [bhawnamanglapm.github.io](https://github.com/bhawnamanglapm/bhawnamanglapm.github.io). The portfolio repo's commit history is not carried over, and the portfolio copy is unchanged.
- The portfolio repo is MIT-licensed. No separate licence file has been added here; that is the owner's decision.
