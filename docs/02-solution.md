# 02 · Solution

## Problem statement (template from the brief)
> Because of this tool, a farmer in western UP will learn the likely cause of a problem on her crop and what to do **within minutes**, by calling from her own basic phone in Hindi, instead of waiting months for an extension visit or guessing. We know because [EVIDENCE: extension coverage figure, UP/India, year].

## Two parts
1. **Voice helpline (core, offline-capable):** the farmer calls from a basic phone and talks in Hindi.
2. **Registration app (companion PWA):** a family member registers the farmer once on a smartphone; the app later shows past answers and can read them aloud. See `08-app.md`.

## User journey
1. **Once:** a family member or the digital champion registers the farmer in the app (phone number, village area, crops, field size, consent).
2. **Evening, at home:** she notices a problem and calls (proposed: missed call → free).
3. The system answers or **calls back** from a fixed, familiar number with a familiar voice.
4. **Consent prompt** by voice: "This call is recorded to help you. Say yes or press 1."
5. She **describes the problem in her own words**; guided follow-ups by voice (keypad digits optional).
6. **Analysis:** symptoms + location + recent weather + nearby reports.
7. **Confident:** likely cause + pre-recorded, expert-approved advice clip → app badge "Answer given".
   **Unsure:** "I'm not sure. The extension officer will call you." → officer task → app badge "Officer will call you".
8. **Follow-up call** a few days later: "Did it spread? Say yes/no or press 1/2."
9. Optional: the family reads or listens to the advice again in the app; weekly leaf photo confirms or corrects the case.
10. The **officer dashboard** shows a ranked case list, map and outbreak alerts.

## Design for farmers who cannot read
- Voice-only core: no text SMS fallback, no forms on the call.
- Keypad used only for digits, always with a voice alternative.
- App: one question per screen, big icons, speaker button, large buttons; registration with family help.
- Call-back number recognisable via saved ringtone and the same opening voice.

## Architecture
| Component | Technology |
|---|---|
| Phone channel | Registered business number via licensed provider (e.g. Exotel), 4 channels; simulated call UI for the demo |
| Speech recognition | Whisper-small or Meta MMS (Hindi); AI4Bharat models as alternative |
| Symptom extraction | Small open LLM (e.g. Qwen2.5-1.5B quantized, llama.cpp/Ollama; KisanSLM to check), output forced into fixed JSON |
| Context data | Location from registry, weather (NASA POWER/CHIRPS, cached), nearby confirmed reports, cited symptom table |
| Classifier | Naive Bayes / gradient boosting, calibrated confidence; learns only from confirmed cases |
| Safety layer | Fixed rules: threshold → approved clip, else "unsure" + officer task |
| Voice output | Pre-recorded clips by a native Hindi speaker (ElevenLabs only for demo/video narration) |
| Photo verification | MobileNetV3/EfficientNet-Lite, quantized (~5 MB), offline on smartphone |
| Backend API | `/api/farmers`, `/api/farmers/me`, `/api/farmers/me/cases` (token-based, no login) |
| Registration app | Hindi-first PWA (can be built with Lovable), offline storage, read-aloud |
| Officer dashboard | Case queue, map, alerts |

**Offline mode:** the AI stack runs locally on a mini PC ("the box") at a farmer producer organisation or Krishi Vigyan Kendra. The farmer's phone never needs data; the site needs a connection to the telephony provider.

## Why AI (and not SMS, a spreadsheet or a search)
- Understands free spoken descriptions in Hindi/dialect (NLP) — SMS and search require literacy.
- Combines symptoms, weather and neighbours' reports into calibrated likelihoods that know when they're unsure (ML).
- Reads leaf photos (computer vision).
- Improves for the local area from confirmed cases.
- **Deliberately rules, not AI:** advice content and the referral decision.

## Responsible AI
- Consent on every call and in the app (checkbox, read aloud); press 1 to allow keeping the recording, press 9 to delete everything.
- Voice recording deleted after transcription unless the farmer agrees; only structured symptoms kept.
- Location rounded to 2 decimals (~1 km) — village area, not the house.
- Phone stores only the app token and the advice history; "Delete my data" clears both. (Earlier claim "nothing stored on the phone" no longer holds.)
- "Likely" + confidence, never a definitive diagnosis; humans decide unclear cases.
- No generated advice — only approved recordings/texts.
- Accuracy reported per language/dialect and speaker group.
- Only officer- or photo-confirmed cases retrain the model.
- Data deleted after 12 months; outbreak data shared only aggregated, never usable against farmers on price.

## Positioning vs. Bharat-VISTAAR
The Ministry of Agriculture launched Bharat-VISTAAR (Feb 2026), a 24×7 AI advisory with voice assistant "Bharati" (helpline 155261). We position our tool as a **local, offline module that complements it**: works where the cloud doesn't, triages with confidence and human hand-off, and feeds village-level outbreak reports into national pest surveillance.
