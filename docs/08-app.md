# 08 · Registration app ("Coffee Helpline" — working name)

Mobile-first web app (PWA) for smallholder farmers in India. A family member helps register once; afterwards the farmer calls the helpline from a basic phone and the app shows the answers given.

## Requirements (summary)
- **Language:** Hindi default, small English switch; short everyday words.
- **Ease of use:** one question per screen, big icon + one sentence, buttons ≥56 px, text ≥18 px, high contrast, speaker button (browser Hindi voice, hidden if unavailable), progress dots, Back button, no raw error codes, screen-reader labels, keyboard support.
- **Screens:** Welcome · Phone number (+91, 10 digits) · Location (button; fallback village name; round to 2 decimals) · Crop tiles (Coffee, Maize, Beans, Other; multi-select) · Field size (±0.5 acre) · Consent (checkbox, Save disabled until ticked) · Done (helpline number, "Call now") · Home (past calls, badges "Answer given"/"Officer will call you", pull-to-refresh) · Settings (change details, privacy policy, "Delete my data").
- **Lightweight/offline:** fast on slow 3G; only small SVG icons; no web fonts, maps, analytics, trackers or cookies; installable PWA; offline save with automatic sync; last call list cached.
- **Backend (existing API, base URL in one constant, header `ngrok-skip-browser-warning: true`):**
  - `POST /api/farmers` {phone, lat, lon, place, crops, area_acres, consent} → {token}
  - `GET /api/farmers/me/cases` (Bearer token) → [{id, created_at, status, result_title, advice_text, weather_summary}], status `answered` | `in_review`
  - `PUT /api/farmers/me` · `DELETE /api/farmers/me` (then clear storage, back to Welcome)

## Privacy summary (consent screen, Hindi)
We save phone number, village area, crops, field size · used only for crop advice · no selling, no ads · delete anytime.

## Full privacy policy (key points)
Student prototype by [TEAM NAME AND CONTACT EMAIL] · saves phone, village area, crops, field size, described problems · voice turned into text and deleted unless the farmer presses 1 · visible only to helpline team and officer; phone number stored protected · village area sent to a weather service (no name/number) · deleted after 12 months · see/change/delete in the app or press 9 on a call · advice is likely, not certain; officer calls if unsure; farmer decides.

## Review notes — to fix
1. **Coffee vs UP conflict:** coffee isn't grown in western UP; rename (e.g. "Kisan Helpline") and lead with maize/beans, or change region.
2. **Phone storage:** token and advice history are stored on the phone — update the "nothing on the phone" claim in pitch and policy.
3. **Call model:** `tel:` = paid call; if missed call + call-back is chosen, change wording and privacy text.
4. **Low literacy:** speaker button must read the whole privacy summary; registration with family/champion help.
5. **No number verification:** anyone can register any number — name as known limit or match caller ID on first call.
6. **Hindi voice missing** on many cheap Android phones → cache short pre-recorded MP3s as fallback.
7. **Weather lookup** is server-side; offline mode uses cached weather.
8. **Less-supported language** remains a call-side test (dialect), shown in the video.
9. Small fixes: "View my data" in Settings; time frame for officer call-back; fill placeholders.
