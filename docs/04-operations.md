# 04 · Operations (estimates for one site, 1,000 farmers)

## Call model (proposed): missed call + call-back
- Farmer rings once and hangs up → free for her.
- Box calls back from a fixed number, in order of arrival.
- Works with plain SIMs in the GSM gateway (toll-free needs a cloud provider).
- No busy signal: busy periods become a call-back list.
- Downsides: short delay; farmer must answer an incoming call; outgoing minutes cost the operator.
- Check TRAI rules for automated outbound calls before a real launch.

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
Mini PC (laptop for the demo) + 4-line GSM gateway + battery backup, at an FPO or Krishi Vigyan Kendra. Runs speech recognition, LLM, classifier, clips, database, dashboard. Electricity ~300–550 kWh/year (30–65 W, 24/7). Hardware replacement every 3–4 years. A Raspberry Pi is likely too slow for ASR + LLM.
