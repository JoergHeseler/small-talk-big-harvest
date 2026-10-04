# 05 · Finance — who pays how much for what (estimates)

Setting: western Uttar Pradesh near Delhi, one site (FPO or Krishi Vigyan Kendra) serving **1,000 farmers**.
Funding: government (state + central) in exchange for reach into low-connectivity villages, pest-surveillance data, a farmer registry and local jobs.

Legend: **[S]** = based on a published source · **[E]** = our estimate, to verify with local quotes.

## Telephony assumption (changed after review)
Automated calling from ordinary consumer SIM cards is likely restricted by TRAI rules and operator terms, and such SIMs can be blocked. We therefore budget for a **registered business calling number through a licensed provider** (e.g. Exotel, Knowlarity). The per-minute rates below are already business-provider rates. The GSM gateway is removed from the budget.

## One-time setup per site

| Item | Who pays | Estimated cost | Basis |
|---|---|---|---|
| Mini PC (16 GB RAM, runs ASR + LLM) | Central government (IndiaAI Mission / Ministry of Agriculture) | ₹35,000–50,000 | [E] |
| Battery backup (UPS) | Central government | ₹8,000–15,000 | [E] |
| Business number setup with provider | Pilot budget | ₹5,000–15,000 | [E] |
| Hindi voice recordings (native speaker) | Pilot budget | ₹10,000–20,000 | [E] |
| Initial advice content + expert review | Pilot budget (ICAR / agri university experts) | ₹30,000–60,000 | [E] |
| Installation and training of digital champion | Pilot budget | ₹10,000–20,000 | [E] |
| **Total one-time** | | **₹1.0–1.8 lakh** | |

## Yearly running costs per site (full cost)

| Item | Who pays | Estimated cost / year | Basis |
|---|---|---|---|
| Farmer's call | Nobody | ₹0 | missed call + call-back |
| Call minutes, **rounded up to full minutes** | UP State Agriculture Department | ₹12,000–36,000 | [S] ₹0.40–1.20/min; 3.5-min call billed as 4 min, follow-up as 1 min; 6 + 6 calls per farmer |
| Business number rental + platform fees | UP State Agriculture Department | ₹10,000–30,000 | [E] provider quote needed |
| Internet connection at the site (needed for cloud telephony) | Host site | ₹6,000–12,000 | [E] |
| Electricity | Host site (government-funded FPO/KVK) | ₹2,000–4,400 | [S] ₹7.70/kWh × 260–570 kWh |
| Digital champion (part-time, ~25–30%) | State, via FPO / extension | ₹42,000–48,000 | [S] UP skilled minimum wage ~₹13,940/month; part-time share [E] |
| Seasonal content updates + expert review | State (agri university / ICAR) | ₹40,000–60,000 | [E] |
| Server for the registration app API | State | ₹12,000–24,000 | [E] |
| Hardware replacement reserve (3–4 yrs) | Central government | ₹12,000–19,000 | [E] PC + UPS ÷ 3.5 |
| Officer call-backs | State extension service | no extra cost | existing staff, better targeted |
| **Total per year** | | **₹1.4–2.3 lakh** | |

## Full cost per farmer
| | Per farmer per year |
|---|---|
| Running cost (base case) | **₹140–235** (≈ $1.6–2.8) |
| Year 1 incl. setup | ₹235–415 |
| Sensitivity: **full-time** champion at UP skilled minimum wage (₹1.67 lakh/yr) | ₹260–350 (≈ $3–4) |
| Call minutes only (for reference) | ₹12–36 |

**Where the money goes:** people (champion + expert content) are about 60% of running costs; call minutes are only about 10–15%.

**Comparison with PxD:** PxD reports a **total** cost of about $2–5 per farmer per year for voice advisory [S]. Our **full** cost (base case and full-time sensitivity) lies in or below that range. Caveat: PxD's figure comes from programmes with millions of farmers; our single-site figure has fewer economies of scale but no national call-centre staff.

**Scale effect:** with more farmers per site, champion, content and server costs are shared, so the cost per farmer falls.

## Optional income
| Item | Who pays | Estimate |
|---|---|---|
| Anonymised village-level outbreak maps | Agri-businesses, input companies | negotiable; only aggregated data, never for price negotiations |
| Integration with Bharat-VISTAAR | Ministry of Agriculture | one-time project, to be scoped |

## Jobs created per site
One part-time digital champion, native-speaker voice recordings, seasonal expert review work.

## Risks
| Risk | Impact | Our response |
|---|---|---|
| **TRAI / operator rules on automated calls** | Consumer SIMs can be blocked; a registered business number adds ₹10,000–30,000/yr and needs internet at the site | Budgeted above; get a provider quote and check registration requirements |
| Billing pulse | Short calls billed as full minutes | Already included (rounded figures) |
| Internet outage at the site | Calls can't connect via cloud provider | Farmer side still needs no data; officer fallback; offline AI processing continues once the call is up |
| Small income effect | GiveWell rated PxD's likely income effect as small | Measure impact in the pilot |

## Pitch line
"Free for the farmer. About ₹140–235 per farmer per year in full cost to the state — in line with proven voice advisory services — extending Bharat-VISTAAR to villages where farmers have no data."

## Sources
- UP tariff FY 2026-27: https://powerpeakdigest.com/uperc-retains-fy27-power-tariffs-raises-subsidy-and-expands-ev-benefits/
- UP minimum wage 2026: https://wageindicator.org/en-in/ai/work-in-india/minimum-wage/21888-uttar-pradesh/22085-shops/
- India call rates: https://edesy.in/ai-voice-assistant/compare/twilio-pricing ; https://prospeo.io/s/knowlarity-pricing-reviews-pros-and-cons
- Billing pulse: https://www.cloudtalk.io/blog/exotel-pricing/
- PxD costs: https://solve.mit.edu/challenges/tiger-challenge-international/solutions/15229
