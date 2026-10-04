# 04 · Operations (estimates for one site, 1,000 farmers)

## Call model
- **Proposed: missed call + call-back.** Farmer rings once (free); the system calls back from one fixed, registered business number in order of arrival.
- **Telephony (changed after review):** a **registered business number via a licensed provider** (e.g. Exotel, Knowlarity), not consumer SIMs in a GSM gateway — automated calling from consumer SIMs is likely restricted by TRAI rules and SIMs can be blocked.
- **Consequence for "offline":** the farmer's side still needs no data. The site needs an internet connection so the provider can pass calls to the box; the AI processing itself runs locally. A wired operator business line (PRI/SIP trunk) is an alternative to check.
- **Current app requirement:** "Call now" opens a normal paid call (`tel:`). If missed call is chosen, change the app text to "Give a missed call, we will call you back".

## Capacity and waiting (checked by reviewer with Erlang C)
| Question | Estimate | Basis |
|---|---|---|
| Advice call length | ~3–4 min (billed as 4 min) | consent 10 s, description 30–45 s, follow-ups 45 s, processing 10–20 s, clip 60–90 s |
| "Unsure" call | ~2 min | no advice clip |
| Follow-up call | ~30 s (billed as 1 min) | yes/no |
| Parallel calls | 4 | provider channels; mini PC handles ~4–5 before slowing |
| Calls/hour, normal season | ~7 | 6 calls/farmer/year, rainy-season evenings |
| Calls/hour, outbreak peak | ~35 | 5× normal |
| Waiting, normal | almost none | lines usually free |
| Waiting, peak | ~18% of callers wait, ~1.8 min on average; ~20 s average across all callers | Erlang C, 4 lines, 3.5-min calls |
| Max queue | no hard limit; ~5–10 at peaks | call-back list |

## The box
Mini PC (laptop for the demo) + battery backup + internet connection, at an FPO or Krishi Vigyan Kendra. Runs speech recognition, LLM, classifier, clips, database, dashboard. Electricity ~260–570 kWh/year (30–65 W, 24/7) ≈ ₹2,000–4,400/year at UP rates. Hardware replacement every 3–4 years. A Raspberry Pi is likely too slow for ASR + LLM.

## The app backend
A small cloud server hosts the registration API (≈ ₹12,000–24,000/year). In offline areas the app keeps data on the phone and syncs when a signal appears.

## Who maintains what
| Task | Who |
|---|---|
| Restarts, provider balance, loading new clips | Digital champion (part-time) |
| Seasonal advice content | Agricultural university / ICAR experts |
| Officer call-backs | State extension service |
| Server, app and provider account | State IT / implementing partner |
