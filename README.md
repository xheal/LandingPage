# 78 xHeal Clinics landing page (23 Oct 2026)

Build of `xHeal Clinics Landing Page v2.pdf` (Downloads) as a single static page.

- `index.html`: the whole page, CSS and JS inline. Tokens and type scale follow folder 61 (daylight clinical: #F7F8FC ground, #4764FF accent, Manrope 500/600/700 after the 23 Oct weight bump, hairlines instead of shadows, 20 px cards, 32 px media panels).
- `assets/video/`: the Provider Workspace clips from folder 76, re-encoded for the web (h264, no audio) and trimmed before their end cards.
  - `routines`, `trends`, `sharing`, `askai`: the 4:5 clips behind the "What you see with xHeal" rows, from the 2160 sources at full size (2160×2700, crf 25). In-points skip the title frames: trends 1.5 s, routines 0.8 s, ask-AI 7.0 s, 230-demos 9.5 s.
  - `bump`: the 16:9 provider bump cut, in the dark "Start small" section.
- `assets/wordmark.svg`, `assets/mark.svg`: from folder 75.
- `assets/logos/`: WHOOP, Polar and Strava wordmarks (Wikimedia Commons), MyChart site logo (media.epic.com). Apple Health, the Apple glyph and the two document icons are inline SVG.

## Where the build departs from the PDF

- The hero sits on the provider onboarding stage (night to indigo sweep, haze, grain; light tokens, centre sunk to 97 to 103 percent so the headline stays on night and the light rises under the card). Classes are `.sky`, `.sky__sweep`, `.sky__haze`, `.sky__grain` because `.stage` is the video panel.
- The beam's haze is drawn by `.bookwrap::before` behind the card, the ring by `.booking::after` on it; the oscillator writes its variables on `#bookwrap`.
- The works-with strip is a marquee of logo tiles (grey at rest, brand colour on hover, paused on hover, static wrap under reduced motion).
- The booking card carries a border beam in the transitions.dev manner: a 1.5 px ring of indigo radial blobs on the hairline, a blurred haze outside, driven by a 30 fps oscillator loop (`--w*`, `--x*`, `--y*`, `--o*`, `--hue` on `#booking`). It runs only while the card is in view and stops under reduced motion.
- "What you see with xHeal" replaces the illustrative Sarah M. card with the real provider videos. The clip is the whole section: it fits the section height so every frame is visible, and a blurred, saturated copy of the active clip's poster (`.amb`) fills the sides so the stage still reads full-bleed. The clip is aligned to the right edge; the left half holds the caption, vertically centred: section label, the current clip's title and one line, four dots that switch clips, and the demonstration-data note (the active dot is a pill that fills as the clip plays); clips advance on their own until the viewer picks one. On phones the clip shows at 4:5 with the caption below.
- Multi-select questions in the booking flow use circle checks instead of A/B/C letters.
- The booking card sits in the hero in place of the primary button (the nav pill carries "Book my free demo"; every other CTA scrolls to the card). It is a working 6-question flow plus a time-slot step and a confirmation; the beam fades once the first answer is picked. There is no backend; the submit only renders the confirmation.
- The brief's "Live in [7 days]" sentence and the whole "Patients stay in control of their data" section were removed on 23 Oct (unconfirmed claims). The two unanswered FAQ items are still dotted placeholders.
- The dark "Start small" panel spans the text column's height; the bump clip sits in it with object-fit contain on the clip's own #000E1B, so no band shows.
- Step numbers, tracked-caps eyebrows and middle dots from the PDF are not used (house rules).

## Run

`.claude/launch.json` has `clinics-landing` on port 8098. Add `?static` to the URL to skip the reveal animations (for screenshots).
