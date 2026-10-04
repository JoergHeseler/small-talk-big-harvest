# Small Talk Big Harvest — Voice Crop Advisor

Hack-Nation × World Bank "Small AI for Development" Hackathon (3–4 Oct 2026) · **Agriculture track**

A farmer gives a missed call from her basic phone, describes the problem on her crop **by voice in Hindi**, and hears the likely cause and an expert-approved advice clip. Unsure cases go to a human extension officer. A small Hindi-first registration app (PWA) lets a family member register the farmer once and shows the history of answers.

## Status of key decisions

| Topic | Status | Decision |
|---|---|---|
| Team name | Decided | Small Talk Big Harvest |
| Product name | Working name | Voice Crop Advisor; registration app: "Coffee Helpline" |
| Track | Decided | Agriculture (Annex B) |
| Region | Decided | Uttar Pradesh (UP), India, near Delhi |
| Main language | Decided | Hindi (app: Hindi default, English switch) |
| Less-supported test language | Proposed | Local dialect (e.g. Khari Boli or Braj) |
| Users | Decided | Many farmers cannot read or write → voice-only core; app registration with family help |
| Payer | Decided | Government (state + central) |
| Cost | Estimated | ₹130–200 per farmer per year running; ₹1.2–2.1 lakh setup per site |
| Registration app | Decided | Mobile-first PWA, offline-capable, existing API (see `docs/08-app.md`) |
| Crop | **Open — conflict** | App says coffee; coffee is not grown in western UP (proposed: maize, or rename app "Kisan Helpline") |
| Call model | **Open** | App requirements use a normal call (`tel:`); proposed: missed call + call-back |

## Contents

- `docs/01-challenge.md` — what the brief requires, deliverables, judging
- `docs/02-solution.md` — user, journey, architecture, why AI, guardrails
- `docs/03-data.md` — datasets, gaps, evidence plan
- `docs/04-operations.md` — call model, call length, capacity, waiting times
- `docs/05-finance.md` — who pays how much for what (estimated costs)
- `docs/06-open-points.md` — what is still missing before submission
- `docs/07-sources.md` — sources and benchmarks
- `docs/08-app.md` — registration app requirements and review notes

All cost and capacity figures are **estimates** to be verified in a pilot.
