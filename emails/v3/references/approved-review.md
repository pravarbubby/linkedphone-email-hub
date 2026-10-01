# Final consistency review

The delivered review is live HTML with shared layout and typography. Open `day1a.html`, `day1b.html`, `day2.html`, or `receipt.html`. Earlier versions and original sending templates remain unchanged.

## Shared measured rules

- Desktop email width: 600px, 48px side padding.
- All heroes: 504 × 220px, 12px corner radius.
- Greetings: 18/28px semibold; body: 16/26px.
- Onboarding Quick Start cards: identical markup and 504 × 96px size at desktop.
- Footers: identical support/contact markup and spacing; 16/26px typography; 162px measured height. Receipt retains its appropriate Thanks signoff.
- Bottom pattern: closing paragraph, FAQ, Tomorrow, Quick Start, footer, omitting inapplicable sections.
- Instructional steps: 48px top/bottom padding, separated paragraphs and readable source text. Images stack after text on mobile.

Day 1B uses standalone generated hero and step PNGs, displayed without cropping. Other approved artwork is displayed through SVG viewports referencing the original raster mockups. No source image files were modified. These are browser design previews, not email-client-ready sending templates. Production packaging needs standalone cropped raster assets and email-safe layout. The invoice button is deliberately a nonfunctional sample action.

Build: `python3 v2/build-final-consistency.py`.
Checks: `node v2/check-final-consistency.mjs` and `python3 v2/verify-final-consistency.py`.
Desktop and 375px mobile checks passed. All 34 onboarding source blocks are present, excluding editorial formatting markers. Exact punctuation is retained in the source-driven build; verification normalizes punctuation and whitespace. Original 24 email hashes remain unchanged.

The built-in image tool also produced the final image explorations in `images/`, with their exact prompts. Those explorations are retained as references; shared HTML is the final consistency review because separately generated text/layout still drifted.

Latest refinement: Day 1B and Day 2 use equal 240px text/image columns at desktop with a 24px gap. Day 1B hero is regenerated as a spacious 3D still-life. Three standalone square UI previews replace cropped phone fragments; all card edges and notification content remain visible. Store badges have matched visible heights of 40px desktop and 36px mobile, accounting for transparent padding in the Play Store asset. All shared bottom components remain unchanged. New assets and exact built-in generation prompts are saved in images/day1b-hero-3d.* and images/day1b-step-*.
