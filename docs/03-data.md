# 03 · Data

## Shows the problem (cite source, year, country)
- [ ] Extension coverage / farmer-to-officer ratio, UP or India
- [ ] Literacy in UP, ideally by gender (Census of India / World Development Indicators)
- [ ] Phone vs smartphone ownership by gender (GSMA Mobile Gender Gap Report)
- [ ] Mobile money use by gender (Global Findex) — argues why the call must be free
- [ ] Signal coverage in the chosen district (OpenCelliD)
- [ ] Crop yields (FAOSTAT)

## Data we build with
| Purpose | Datasets | Licence to check |
|---|---|---|
| Speech | Common Voice (Hindi), FLEURS, MMS, AI4Bharat/IndicVoices + own 30–50 native recordings | yes |
| Real farmer language | Kisan Call Centre transcripts (Open Government License, India) | yes |
| Symptom table | ICAR packages of practice, extension guides | cite |
| Weather | NASA POWER, CHIRPS | open |
| Photos | Field-condition datasets for the chosen crop (PlantDoc etc.); PlantVillage only with gap noted | yes |
| Farmers and reports | **Synthetic, labelled as such** | — |

## Data the app collects
Phone number (stored protected), location rounded to ~1 km or village name, crops, field size, consent, call cases. Retention: 12 months.

## What our data does not cover (scored — state it openly)
- Dialect speech: small test set, few speakers.
- Studio photo datasets perform worse on real field photos.
- Some problems are not visible on leaves.
- Nutrient deficiency, drought stress, mixed infections mostly uncovered.
- Nearby reports and the learning loop are simulated.

## Evidence plan
- Speech word error rate: standard Hindi vs dialect.
- Symptom extraction accuracy on 30–50 native descriptions.
- Classifier vs expert table alone as confirmed cases accumulate (simulated, labelled).
- Photo model: studio vs field accuracy.
- Live demo with internet switched off.
