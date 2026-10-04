# 06 · Open points before submission

## Decisions
- [ ] **Crop vs region conflict:** app says coffee, region is western UP (no coffee). Options: switch to maize and rename app ("Kisan Helpline"), or move region south (then Hindi is not the local language)
- [ ] Call model: normal call (`tel:`) vs missed call + call-back
- [ ] Dialect for the less-supported language test

## App fixes (see `08-app.md`)
- [ ] Speaker button reads the full privacy summary on the consent screen
- [ ] Fallback audio (MP3) when the phone has no Hindi browser voice
- [ ] "View my data" in Settings
- [ ] Time frame for "Officer will call you"
- [ ] Fill [TEAM NAME AND CONTACT EMAIL], [HELPLINE NUMBER], [API BASE URL]
- [ ] Name the missing phone-number verification as a known limit

## Content and evidence
- [ ] Evidence figure in the problem statement
- [ ] Local quotes for hardware, content and recordings (largest finance estimates)
- [ ] Licences of all datasets and of KisanSLM
- [ ] Remove "SMS fallback" everywhere (users cannot read)

## Deliverables
- [ ] Update slide deck: UP, Hindi, crop, government funding, Bharat-VISTAAR, team name, costs
- [ ] Write "our take" on localizing AI (personal paragraph)
- [ ] Record 2–5 min video
- [ ] Assign owners: call flow, ASR+LLM, classifier+data, CV, app (Lovable), dashboard, recordings, video
- [ ] Add LICENSE (Apache 2.0) to the repo
