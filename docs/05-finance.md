# 05 · Finance — who pays how much for what (estimates)

Setting: western Uttar Pradesh near Delhi, one site (FPO or Krishi Vigyan Kendra) serving **1,000 farmers**.
Funding: government (state + central) in exchange for reach into low-connectivity villages, pest-surveillance data, a farmer registry and local jobs.

Legend: **[S]** = based on a published source · **[E]** = our estimate, to verify with local quotes.

## One-time setup per site

| Item | Who pays | Estimated cost | Basis |
|---|---|---|---|
| Mini PC (16 GB RAM, runs ASR + LLM) | Central government (IndiaAI Mission / Ministry of Agriculture) | ₹35,000–50,000 | [E] |
| 4-line GSM gateway | Central government | ₹25,000–40,000 | [E] |
| Battery backup (UPS) | Central government | ₹8,000–15,000 | [E] |
| Hindi voice recordings (native speaker) | Pilot budget | ₹10,000–20,000 | [E] |
| Initial advice content + expert review | Pilot budget (ICAR / agri university experts) | ₹30,000–60,000 | [E] |
| Installation and training of digital champion | Pilot budget | ₹10,000–20,000 | [E] |
| **Total one-time** | | **₹1.2–2.1 lakh** | |

## Yearly running costs per site

| Item | Who pays | Estimated cost / year | Basis |
|---|---|---|---|
| Farmer's call | Nobody | ₹0 | missed call + call-back |
| Phone lines and call minutes | UP State Agriculture Department | ₹15,000–35,000 | [S] ₹0.40–1.20/min outbound; 6 advice + 6 follow-up calls per farmer |
| Electricity | Host site (government-funded FPO/KVK) | ₹2,300–4,200 | [S] UP LT energy charge ₹7.70/kWh × 300–550 kWh |
| Digital champion (part-time, ~25–30%) | State, via FPO / extension | ₹42,000–48,000 | [S] UP skilled minimum wage ~₹13,940/month, part-time share [E] |
| Seasonal content updates + expert review | State (agri university / ICAR) | ₹40,000–60,000 | [E] |
| Server for the registration app API | State | ₹12,000–24,000 | [E] small cloud server |
| Hardware replacement reserve (3–4 yrs) | Central government | ₹20,000–30,000 | [E] hardware cost ÷ 3.5 |
| Officer call-backs | State extension service | no extra cost | existing staff, better targeted |
| **Total per year** | | **₹1.3–2.0 lakh** | |

## Per farmer
- Running cost: **₹130–200 per farmer per year** (≈ $1.5–2.5).
- Year 1 incl. setup: ₹2.5–4.1 lakh per site → ₹250–410 per farmer.
- Benchmark: PxD voice advisory ~$2–5 per farmer per year [S] — we are in or below that range.
- Scale effect: one box with 4 lines can serve more than 1,000 farmers; the fixed costs (champion, content, server) are shared, so cost per farmer falls with each additional farmer.

## Optional income
| Item | Who pays | Estimate |
|---|---|---|
| Anonymised village-level outbreak maps | Agri-businesses, input companies | negotiable; only aggregated data, never for price negotiations |
| Integration with Bharat-VISTAAR | Ministry of Agriculture | one-time project, to be scoped |

## Jobs created per site
One part-time digital champion, native-speaker voice recordings, seasonal expert review work.

## Risks and caveats
- Bulk automated calling on consumer SIMs may breach operator fair-use or TRAI rules — check before launch; a licensed cloud provider is the fallback (costs included above).
- Per-minute billing pulse rounds short calls up.
- GiveWell rated PxD's likely income effect as small — impact must be measured in the pilot.

## Pitch line
"Free for the farmer. About ₹130–200 per farmer per year for the state — below the cost of proven voice advisory services — extending Bharat-VISTAAR to villages the cloud can't reach."

## Sources
- UP tariff FY 2026-27: https://powerpeakdigest.com/uperc-retains-fy27-power-tariffs-raises-subsidy-and-expands-ev-benefits/
- UP minimum wage 2026: https://wageindicator.org/en-in/ai/work-in-india/minimum-wage/21888-uttar-pradesh/22085-shops/
- India call rates: https://edesy.in/ai-voice-assistant/compare/twilio-pricing ; https://prospeo.io/s/knowlarity-pricing-reviews-pros-and-cons
- PxD costs: https://solve.mit.edu/challenges/tiger-challenge-international/solutions/15229
