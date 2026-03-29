# Meridian — Outputs

This repo contains the output of a 6-agent AI pipeline I built for VC market intelligence. The topic for this run was **AI Agents** the pipeline scraped real data, analysed it, wrote a report, had another agent tear it apart, and then synthesized a final version.

Here's what each file is.

---

## The Files

| File | Produced by | What's in it |
|------|------------|-------------|
| `m1_youtube_raw.json` | **M1 — YouTube Collector** | Raw YouTube comments scraped from ~70 videos across 10 search queries. Filtered down to ~200 "signal" comments — ones where people express real frustrations, needs, or opinions about AI agents. |
| `m1b_rss_raw.json` | **M1b — RSS Collector** | ~60 articles pulled from TechCrunch, Hacker News, and AVC RSS feeds. Title, summary, date, and source for each. This gives the media/industry perspective. |
| `m2_analysis.json` | **M2 — Market Analyst** | An LLM agent read both raw files and extracted structured intelligence: emerging trends, unmet demand signals, market shifts, and contrarian signals. Also compares what practitioners say (YouTube) vs what media covers (RSS) — they often disagree. |
| `m3_draft_report.md` | **M3 — Draft Writer** | First-draft intelligence report. Has an exec summary, a signal table with 17 rows, 3 key investment themes, and an opportunity synthesis. Reads like a VC research memo. |
| `m3b_challenge.md` | **M3b — Devil's Advocate** | A skeptical "senior partner" agent challenges every single claim from the draft. Tests each one for novelty, evidence strength, source bias, base rates, and counter-evidence. Assigns HIGH/MEDIUM/LOW confidence. Verdict: only 3 out of 17 claims survive scrutiny. |
| `meridian_report.md` | **M4 — Final Editor** | The final report. Merges the draft with the challenge — claims that held up stay in, weak ones get downgraded. Adds a confidence column and a methodology note. This is the actual deliverable. |

---

## How the agents work together

```
  M1 (YouTube Scraper)  +  M1b (RSS Fetcher)
           │                      │
           └──────────┬───────────┘
                      ▼
              M2 (Market Analyst)
                      │
                      ▼
              M3 (Draft Writer)
                      │
                      ▼
             M3b (Devil's Advocate)    ← adversarial layer
                      │
                      ▼
              M4 (Final Editor)
                      │
                      ▼
              meridian_report.md       ← the output that matters
```

The key design choice is M3b — instead of just generating a report and shipping it, a separate agent actively tries to disprove every finding. Only what survives makes it into the final version.

---

**Run date:** March 29, 2026  
**Topic:** AI Agents market landscape
