# 02 · Solution

## Problem statement (template from the brief)
> Because of this tool, a farmer in western UP will learn the likely cause of a problem on her crop and what to do **within minutes**, by calling from her own basic phone in Hindi, instead of waiting months for an extension visit or guessing. We know because [EVIDENCE: extension coverage figure, UP/India, year].

## User journey
1. **Evening, at home:** she notices a problem and gives a **missed call** (free).
2. The system **calls back** from a fixed, familiar number with a familiar voice.
3. **Consent prompt** by voice: "This call is recorded to help you. Say yes or press 1."
4. She **describes the problem in her own words**; guided follow-ups by voice (keypad digits optional).
5. **Analysis:** symptoms + location + recent weather + nearby reports.
6. **Confident:** likely cause + pre-recorded, expert-approved advice clip.
   **Unsure:** "I'm not sure. The extension officer will call you." → officer task.
7. **Follow-up call** a few days later: "Did it spread? Say yes/no or press 1/2."
8. Optional weekly leaf photo via a family smartphone confirms or corrects the case.
9. The **officer dashboard** shows a ranked case list, map and outbreak alerts.

## Design for farmers who cannot read
- Voice-only core: no text SMS fallback, no forms.
- Keypad used only for digits, always with a voice alternative.
- Registration by voice or by the local digital champion.
- Call-back number recognisable via saved ringtone and the same opening voice.

## Architecture
| Component | Technology |
|---|---|
| Phone channel | GSM gateway (4 lines) with SIMs; cloud provider (e.g. Exotel) optional in connected areas; simulated call UI for the demo |
| Speech recognition | Whisper-small or Meta MMS (Hindi); AI4Bharat models as alternative |
| Symptom extraction | Small open LLM (e.g. Qwen2.5-1.5B quantized, llama.cpp/Ollama; KisanSLM to check), output forced into fixed JSON |
| Context data | Location from registry, weather (NASA POWER/CHIRPS, cached), nearby confirmed reports, cited symptom table |
| Classifier | Naive Bayes / gradient boosting, calibrated confidence; learns only from confirmed cases |
| Safety layer | Fixed rules: threshold → approved clip, else "unsure" + officer task |
| Voice output | Pre-recorded clips by a native Hindi speaker (ElevenLabs only for demo/video narration) |
| Photo verification | MobileNetV3/EfficientNet-Lite, quantized (~5 MB), offline on smartphone |
| Database | Registry, cases, follow-ups, consent records |
| Dashboard | Officer case queue, map, alerts (can be built with Lovable) |

**Offline mode:** the whole stack runs on a mini PC ("the box") at a farmer producer organisation or Krishi Vigyan Kendra, with a GSM gateway. The farmer's phone never needs data.

## Why AI (and not SMS, a spreadsheet or a search)
- Understands free spoken descriptions in Hindi/dialect (NLP) — SMS and search require literacy.
- Combines symptoms, weather and neighbours' reports into calibrated likelihoods that know when they're unsure (ML).
- Reads leaf photos (computer vision).
- Improves for the local area from confirmed cases.
- **Deliberately rules, not AI:** advice content and the referral decision.

## Responsible AI
- Consent on every call; voice deleted after transcription; only structured symptoms kept; village-level location.
- Nothing stored on the farmer's phone.
- "Likely" + confidence, never a definitive diagnosis; humans decide unclear cases.
- No generated advice — only approved recordings.
- Accuracy reported per language/dialect and speaker group.
- Only officer- or photo-confirmed cases retrain the model.
- Outbreak data shared only aggregated and anonymised; never usable against farmers on price.

## Positioning vs. Bharat-VISTAAR
The Ministry of Agriculture launched Bharat-VISTAAR (Feb 2026), a 24×7 AI advisory with voice assistant "Bharati" (helpline 155261). We position our tool as a **local, offline module that complements it**: works where the cloud doesn't, triages with confidence and human hand-off, and feeds village-level outbreak reports into national pest surveillance.
