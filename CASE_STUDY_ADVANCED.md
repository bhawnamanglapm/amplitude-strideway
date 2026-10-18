# Amplitude Analytics — Strideway (Advanced)

*⭐⭐⭐⭐ Built · funnels, retention, cohorts, a real bug fixed*

> Exported from the portfolio page on 2026-10-19. The live page is the canonical version: https://bhawnamanglapm.github.io/travel-tech-more.html#case-amplitude-strideway-advanced

- Full 6-step monetization funnel
- Retention curve segmented by channel
- Real conversion-window bug found and fixed
- Hit a real Starter-plan limit on cohorts

**Tools used:** Amplitude (Funnel analysis, Retention analysis, Cohorts), the Amplitude Chart API (used to diagnose the bug below).

### Why Advanced, Not Just Basic

Segmentation charts prove I can read a single metric; this half proves I can trace a user journey end to end — funnel conversion, retention over time, and cohort definition, the exact Amplitude patterns behind most growth/monetization dashboards. Same Strideway dataset as the Basic case study (T32).

### A Real Amplitude Bug, Found and Fixed

The first funnel I built — Sign Up → Complete Onboarding → Log Workout → View Paywall → Start Free Trial → Upgrade to Premium — came back showing only **19% conversion** from onboarding to a first logged workout. That looked wrong: nearly every onboarded user in this dataset eventually logs a workout. I checked directly against the raw dataset and confirmed it — **92.5%** of onboarded users eventually log at least one workout, nowhere near 19%.

The cause, found by pulling the chart's real definition through Amplitude's own API rather than guessing: Amplitude funnels default to a **1-day conversion window** between each step (`conversionSeconds: 86400`). Since many users in this dataset don't log their first workout until well after onboarding — they open the app sporadically over weeks, not daily — a 1-day window was silently dropping every conversion that happened even slightly later than that, while still reporting a clean-looking, plausible percentage. Widening the window to 90 days fixed it exactly: Log Workout jumped to **68.97% (2,069 of 2,236)**, matching the raw dataset precisely.

### Key Findings

- **Full funnel, corrected**: Sign Up 3,000 → Complete Onboarding 74.53% → Log Workout 68.97% → View Paywall 11.97% → Start Free Trial 5.9% → Upgrade to Premium 1.63% (49 users) — a realistic, multi-week monetization path, not a same-day one.
- **Retention by channel is the clearest chart in the whole project**: at Day 30, Referral-acquired users retain around 46%, Organic around 36%, Paid Social around 22%, and Influencer around 9% — a roughly 5x spread between the best and worst channel, purely from acquisition source.
- **Cohort creation hit a real plan limit**: dynamic (auto-recalculating) cohorts require a paid Amplitude plan; the Starter tier blocked saving one. The definition itself — "users who performed Upgrade to Premium, count ≥ 1" — was correct; only persisting it as a live cohort was gated. A genuine, worth-knowing constraint of the free tier, not a mistake.

### What This Means, Applied

The retention chart changes the decision quite a bit: I wouldn't automatically scale Influencer just because it brings users in. I'd treat Referral as the stronger quality channel if its retained-user curve is consistently better. As PM, I'd shift more acquisition effort toward Referral, while keeping Influencer as a controlled acquisition experiment. For Influencer, I'd dig into which creators, audiences, and landing experiences are producing retained users rather than judging the channel only on acquisition volume. I'd also set up a cohort comparison for Influencer vs. Referral — same signup period, same retention window, ideally normalized by plan — to make sure the difference isn't caused by audience mix. The goal wouldn't be "kill Influencer"; it would be optimize for retained customers, not just acquired customers. If Referral continues to show stronger retention, I'd increase investment there and use Influencer selectively where creators can demonstrate comparable downstream retention.

### Before / After: the funnel-window fix

[image: Amplitude funnel chart before the fix: Sign Up 100%, Complete Onboarding 74.53%, Log Workout only 19% (570 users), View Paywall 0.3%, Start Free Trial 0.13%, Upgrade to Premium 0% — the 1-day conversion window silently dropping real conversions] [image: Amplitude funnel chart after widening the conversion window to 90 days: Sign Up 100%, Complete Onboarding 74.53%, Log Workout 68.97% (2,069 users), View Paywall 11.97%, Start Free Trial 5.9%, Upgrade to Premium 1.63% — matching the raw dataset exactly] [image: Amplitude retention chart: Daily retention from Sign Up to Open App by signup channel over 30 days — Referral (purple) highest around 46% by Day 30, Organic (blue) around 36%, Paid Social (green) around 22%, Influencer (teal) lowest around 9%] [image: Amplitude retention chart builder, full browser view: Starting event Sign Up, return event Open App, Measured as 'Return On or After' — the actual configuration panel behind the retention-by-channel chart, not just its output] [image: Amplitude New Cohort screen: users who performed Upgrade to Premium, count >= 1 time, during Last 90 days — a correct definition that could not be saved on the free Starter plan (dynamic cohorts are a paid feature)]

All 5 screenshots are real captures from my own live Amplitude project — including the broken funnel and the retention chart's builder panel, left in on purpose to show the actual process rather than only clean, cropped results.

### Quick recall

| Section | Summary |
|---|---|
| **Problem** | The Basic case study proves I can read a single metric; it doesn't prove I can trace a full user journey — funnel conversion, retention over time, cohort definition — the Amplitude patterns behind most real growth/monetization dashboards. |
| **Research steps** | Built the 6-step funnel → the first result (19% onboarding→workout conversion) looked implausible against the raw dataset (92.5% actually convert) → pulled the chart's real definition through Amplitude's own Chart API instead of guessing → found the default 1-day conversion window was silently dropping late conversions → widened it to 90 days and confirmed the fix matched the raw data exactly (68.97%) → built the retention-by-channel chart and attempted to save a cohort, which hit a real Starter-plan limit. |
| **Solution** | The corrected funnel, a retention-by-channel chart, and a verified cohort definition — plus the "What This Means, Applied" recommendation above: shift acquisition investment toward Referral, use Influencer as a controlled experiment, and normalize any channel comparison by plan before trusting it. |
| **Conclusion** | The real finding isn't the funnel percentages themselves — it's that a tool's default setting (a 1-day conversion window) can silently produce a clean, plausible, and completely wrong number, and the only way to catch that is checking a surprising result against the raw data instead of trusting the chart. |

Guide[practice guide →](https://bhawnamanglapm.github.io/projects/amplitude-strideway/AMPLITUDE_GUIDE.md) BackBasic: event segmentation (T32) →
