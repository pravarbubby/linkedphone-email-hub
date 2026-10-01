# LinkedPhone email audit and redesign

20 September 2026 · 6 onboarding emails · 18 transactional emails

## Design conclusion

The original collection used the brand’s colors but did not reproduce the product’s visual hierarchy. A 600 × 400 placeholder dominated every message, including authentication emails. Repeated centered tiles made every detail equally important. There was little distinction between an educational email, a receipt, and an urgent account event. The result was consistent at a code level, but weak as communication.

The revised direction follows the eight Figma exploration screenshots supplied during this task: centered branding, an open white/black page, a headline integrated with an onboarding hero, lavender/slate information panels, large mobile step imagery, and a complete left-aligned support and administrative footer. The latest user references supersede the first redesign’s enclosing card and small mobile thumbnails.

## Evidence reviewed

- All 24 original generated HTML files, the shared source components, layout, tokens, and content modules.
- All 21 supplied PNG screen references in a contact sheet, with detailed inspection of the Inbox and Review Your Plan screens; all 21 corresponding SVGs inspected for dimensions and paint usage. The dominant source paints are #171A2B, #DFE1F8, #5C5D71, #EFF0FE, #444658 and #3356FF.
- `Design System/refs/Primitives.png`, `Tokens.png`, reviewed `data/colors-current.json`, and the catalog’s semantic tokens, WB typography, and individual icon variants. Supplied exports remain unchanged.
- All six onboarding content pages in `html Emails - Pravar.pdf`; page 4’s embedded image was extracted and visually read because its copy is absent from PDF text extraction.
- The eight light/dark desktop/phone Figma explorations supplied in the conversation.
- [LinkedPhone’s website](https://www.linkedphone.com/), including its product imagery, understated surfaces, dark ink, and blue actions.
- [Airbnb, Trello, and Zapier welcome-email examples in Postmark’s research](https://postmarkapp.com/blog/welcome-email-templates-best-practices): useful historical examples of hierarchy and onboarding pacing, not a claim about those brands’ current email programs. Airbnb and Trello demonstrate a recognizable branded opening; Zapier demonstrates the value of readable, direct copy.
- [Notion invitation example](https://reallygoodemails.com/emails/really-good-emails-has-invited-you-to-website-overview/mobile): a compact, task-focused transaction with little visual distraction.
- [Litmus email design guidance](https://www.litmus.com/blog/email-design-best-practices) and [hybrid/responsive layout guidance](https://www.litmus.com/blog/understanding-responsive-and-hybrid-email-design): a modular structure, readable copy, and robust responsive behavior.

## Problems and resolutions

| Original problem | Reader impact | Resolution |
|---|---|---|
| Same 400px blank hero on every template | The reader scrolls before seeing the purpose, even for an OTP | Hero artwork belongs to onboarding; transactional messages start with a small source-system icon and the event |
| Large generic container around every message | Makes the collection feel like a dashboard card rather than an email | Open page on white in light mode and black in dark mode |
| All account values given equal visual weight | Hard to identify the number, plan, or important dates | One summary panel with a clear primary value, separators, and paired supporting values |
| Step previews fixed to 96px on mobile | Imagery looks incidental and disconnected | Copy first, full-width image panel below on phones; full-width previews after copy at both sizes |
| Low-information placeholders repeated throughout | Decoration consumes space without helping comprehension | Product-screen compositions where suitable; explicit schematic illustrations where exact screens are unavailable |
| A collection of disconnected pale boxes | No reading rhythm | Consistent step panels, separate Q&A notes, and a distinct next-day callout |
| Fake app badges and social initials | Visibly unfinished brand treatment | Official Apple/Google badges; social initials removed |
| Footer lacked the requested structure | Incomplete administrative and support context | Support icons and links, separated team sign-off, recipient notice, company-address merge field, preferences and privacy links |
| Overlarge spacing and some table padding | Inconsistent gaps across renderers | Shared 4px-based spacing, padding on table cells, and deliberate section intervals |
| Raw merge tags overflowed at narrow widths | Horizontal scrolling and clipped layouts | Fixed table layout where needed, wrapping dynamic values, boxed button widths, and narrow-width checks |
| Copy did not match the PDF | Approved meaning and onboarding sequence changed | Direct PDF-backed content data with a 74-paragraph comparison |

## Copy preservation

`src/content/onboarding-copy.json` records the PDF paragraphs. `scripts/extract-copy.py` extracts the searchable text; the welcome paragraph is transcribed from the embedded image. `scripts/verify-copy.py` compares every paragraph against the generated HTML, ignoring layout whitespace and bullet markers, while preserving wording and punctuation.

Specific corrections include the welcome introduction, the complete Day 3 explanation, the missing final clause in Day 4’s shared-context section, and the correct next-day message on Days 1b–4. The original PDF’s `Thank you..` punctuation is retained. Editorial `//` comments, numbering syntax, and labels such as `Callout:` are not customer-facing copy. Names and example account values use merge fields.

The visible onboarding hero titles reuse source preheaders for 1a/1b and subjects for the other days. “Want to go further?” and the fuller footer follow the newly supplied Figma direction. The Quick Start supporting sentence remains the approved PDF sentence. Extra onboarding action labels added by the old templates were removed; the official app badges and Quick Start link remain actionable.

The PDF contains a list of transactional email titles, not approved message bodies. Those existing drafted bodies are preserved. They are clearly labeled as drafts in the gallery. Their policy, timing, pricing, file-support and lifecycle claims have not been independently approved by a product owner.

## Template-by-template treatment

| Email | Final visual treatment |
|---|---|
| Onboarding 1a — welcome | Integrated welcome hero; one account summary; reference-style Quick Start and footer |
| Onboarding 1b — first call | Single-call-screen hero; official app badges; three numbered panels with full-width mobile artwork |
| Onboarding Day 2 — greetings | Audio illustration; three greeting panels; distinct quoted examples and Q&A |
| Onboarding Day 3 — Auto Attendant | Schematic routing hero; three setup panels; Q&A and corrected next-day message |
| Onboarding Day 4 — team | Shared-inbox/team composition; three collaboration panels; two Q&As |
| Onboarding Day 5 — features | Product overview; three named feature groups with divided feature rows |
| Transactional 01 — quick-start tips | Compact branded opening and five instructional panels |
| Transactional 02 — trial started | Status message and the same account-summary component as onboarding 1a |
| Transactional 03 — team invitation | Team icon, business/role details, invitation action |
| Transactional 04 — 10DLC | Warning, readable requirements, registration action |
| Transactional 05 — toll-free | Same compliance hierarchy with its existing distinct copy |
| Transactional 06 — porting | Request details, progress steps, service-retention warning |
| Transactional 07 — unsupported MMS | Error state, attachment facts, supported-format list |
| Transactional 08 — assigned ticket | Ticket icon, structured facts, latest-note panel |
| Transactional 09 — receipt | Payment icon, prominent amount, separated invoice details and totals |
| Transactional 10 — subscription updated | Success state and readable before/after plan details |
| Transactional 11 — voicemail | Caller facts, transcript panel, recording action |
| Transactional 12 — payment failed | Error state, amount/retry facts, payment action |
| Transactional 13 — canceled | Effective date, account details, existing recovery action |
| Transactional 14 — goodbye | Quiet text-led account closure without decorative hero imagery |
| Transactional 15 — text alert | Sender facts and a distinct message panel |
| Transactional 16 — OTP | No hero; large selectable code and expiry note |
| Transactional 17 — password reset | Primary action before expiry/security notices, making “link above” accurate |
| Transactional 18 — verify email | Prominent confirmation action and old/new email comparison |

## Responsive and dark-mode decisions

One responsive HTML per email serves both breakpoints. Desktop uses a 600px maximum layout. Phones use the viewport with 20px content gutters. Instructional images become full-width inside their step panel. Instructional panels now use the same left-aligned number/title row and full-width copy/visual composition at both sizes. The account summary retains a compact two-column supporting grid at phone sizes, as in the supplied references. Buttons expand to the available width. Very narrow screens stack store badges to avoid overflow.

The dark palette uses black page backgrounds, slate/lavender panels, white primary text, cool secondary text, and lighter blue actions. Artwork backgrounds and icons have explicit dark variants. Actual product screenshots remain the supplied light-mode artwork; they are not presented as newly invented dark UI screenshots. Hero headings, instructions, account data, links, and security codes remain live HTML text.

## Second visual refinement

The initial browser checks verified HTML bounds but missed clipping inside rasterized icon assets. This pass addresses that distinction explicitly. FAQs now have labelled questions and answers on an open page, separated by rules; tomorrow notes use calendar markers and a solid divider. Step titles and numbers share a left-aligned row. Permission points are clear separated rows, and greeting scripts use a live-text quotation treatment with a quiet waveform strip instead of repeated miniature audio cards. The logo and onboarding hero remain centered as in the references; editorial content is consistently left-aligned.

## Icon and illustration refinement

All 16 exported pictograms resolve by exact name to the design-system Light style. This is the icon's stroke style, not the email color theme; light and dark color variants use semantic primary ink. `assets/icon-manifest.json` records names and source paths. The original SVG exports contained nested frame masks that visibly cut expanded strokes (especially the clock). Email exports remove these masks while preserving all source path geometry and adding an optical margin. All 32 light/dark icon exports have transparent outer pixel boundaries. Missing names stop the build instead of silently selecting another icon. The resource-card arrow and audio play control also use the source set. SVG exports are retained in `assets/icons/`; the emails use raster exports for compatibility.

Instructional illustrations distinguish permissions, business hours, greeting waveforms, phone menus, business information, team directories, replies, and porting progress. They are schematic previews, not claims about shipped screen layouts. Mobile greeting and routing heroes have dedicated compositions, keeping their labels intact and readable. Full-width step imagery remains consistent across all instructional messages.

## Validation and limits

The baseline browser render found five overflow cases: OTP at 375px and 320px; welcome, first-call, and trial-confirmation at 320px. The finished collection is checked with `scripts/capture.mjs`, which saves the final result summary to `tmp/audit/final/results.json` and review PNGs to `output/previews/`.

The completed run includes **432 browser renders with zero detected horizontal overflows, clipped text, broken images, or gallery script errors**. It includes 320, 375, 414, 480, 481, 600, 680 and 1024px viewport widths; intermediate boundaries are checked in both themes. All 24 structural checks and all 74 approved paragraph comparisons pass. The 96 standard desktop/mobile review PNGs are exported separately.

Checks cover all templates with desktop/phone light/dark sample data, narrow raw merge tags, long names/emails, and images hidden. The gallery is checked for script errors and theme/template switching. `qa.mjs` checks document structure, table roles, image metadata, and shared closing variants. `verify-tokens.mjs` checks the token palette. HTML remains below the Gmail clipping threshold.

These are Chromium render checks and structural checks, not a claim of verified Gmail, Apple Mail, or Outlook delivery. Outlook Windows may square rounded corners; some clients alter dark colors or do not honor dark-image swapping. Run the final sending-platform/client test before deployment.

## Handoff details

- `emails/index.html`: self-contained local review gallery with desktop/phone views, light/dark controls, and sample/merge-tag display.
- `emails/onboarding/` and `emails/transactional/`: the 24 responsive templates. Do not hand-edit generated HTML; edit the source and rebuild.
- `output/previews/`: desktop and phone PNG exports for both themes.
- `assets/artwork-manifest.json`: provenance for product artwork and schematic illustrations. Some step art is intentionally illustrative pending final screenshots.
- `{{company_address}}`: left configurable. The Google LLC address from the reference is a layout placeholder, not a LinkedPhone address. Recipient information remains dynamic through `{{email}}`.
- Store links were corrected against the published [Apple listing](https://apps.apple.com/us/app/linkedphone-pro-business-line/id1304985788) and [Google Play listing](https://play.google.com/store/apps/details?id=com.admin.linkedphone).
- Sending still requires hosted HTTPS image URLs, real merge values, and verification of the existing app/help routes in the sending environment. Nothing has been sent or published.
