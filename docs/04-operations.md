# 04 · Operations (estimates for one site, 1,000 farmers)

## Call model — open decision
- **Proposed: missed call + call-back.** Farmer rings once (free), box calls back from a fixed number in order of arrival. Works with plain SIMs; no busy signal.
- **Current app requirement:** "Call now" opens a normal paid call (`tel:` link). If missed call is chosen, change the app text to "Give a missed call, we will call you back".
- Check TRAI rules and operator fair-use before automated calling on SIMs; licensed cloud provider as fallback.

## Capacity and waiting
| Question | Estimate | Basis |
|---|---|---|
| Advice call length | ~3–4 min | consent 10 s, description 30–45 s, follow-ups 45 s, processing 10–20 s, clip 60–90 s |
| "Unsure" call | ~2 min | no advice clip |
| Follow-up call | ~30 s | yes/no |
| Parallel calls | 4 | 4-line gateway; mini PC handles ~4–5 before slowing |
| Calls/hour, normal season | ~7 | 6 calls/farmer/year, rainy-season evenings |
| Calls/hour, outbreak peak | ~35 | 5× normal |
| Waiting, normal | almost none | lines usually free |
| Waiting, peak | ~20 s average; ~2 min for the ~1 in 6 who wait | queueing estimate, 4 lines, 3.5-min calls |
| Max queue | no hard limit; ~5–10 at peaks | call-back list |

## The box
Mini PC (laptop for the demo) + 4-line GSM gateway + battery backup, at an FPO or Krishi Vigyan Kendra. Runs speech recognition, LLM, classifier, clips, database, dashboard. Electricity ~300–550 kWh/year (30–65 W, 24/7) ≈ ₹2,300–4,200/year at UP rates. Hardware replacement every 3–4 years. A Raspberry Pi is likely too slow for ASR + LLM.

## The app backend
A small cloud server hosts the registration API (≈ ₹12,000–24,000/year). In offline areas the app keeps data on the phone and syncs when a signal appears; the core call works regardless.

## Who maintains what
| Task | Who |
|---|---|
| Restarts, SIM balance, loading new clips | Digital champion (part-time) |
| Seasonal advice content | Agricultural university / ICAR experts |
| Officer call-backs | State extension service |
| Server and app updates | State IT / implementing partner |
