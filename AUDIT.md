# Audit: October 2026

Scope: `index.html` and the three tools (Sep 16 2026 versions), checked against `docs/design-system.md` and `CLAUDE.md`. Each page was rendered in Chromium at 375px (phone) and 1280px (desktop), and the source was read for fonts, tokens, network calls and copy. **Nothing has been changed yet.** Items are ranked by how much they matter to a visitor.

## What's already right

- **No network calls, no tracking, no JavaScript errors** on any page. Everything is self-contained, as intended.
- Momo Signature and Walter Turncoat are embedded and load on every page.
- The pink margin rule is `#ef6f9c` everywhere.
- The home page is clean at both widths: no overflow, the title stays on one line, and the EA disclaimer is present.
- The public Tag Builder has no performance readouts and no "weaker choice" colouring.

## Fix first

### 1. All three tools scroll sideways on phones
At 375px each tool is wider than the screen: the Tag Builder is 534px wide, the House Style Finder 483px and the Activity Finder 464px. The cover title is cut off ("Gallery Tag B…") and the intro text runs off the edge. This is the same bug fixed on the home page (a `nowrap` title inside a grid child without `min-width: 0`), and it was never carried over to the tools. Most gallery builders will open these on a phone, so this matters most.
**Fix:** port the home page's title-fit and `min-width: 0` fix into the shared cover/plate CSS of all three tools.

### 2. The EA disclaimer is missing from all three tools
Only the home page has it. The project rule is "on every page", and the tools are the pages people will share and land on directly.
**Fix:** copy the home page footer disclaimer into each tool's footer.

### 3. Corrections have nowhere to go
The crowd-sourcing promise is central to the site, but:
- Only the House Style Finder has a "Send us the wording" prompt. The Tag Builder and Activity Finder have none.
- That prompt's `CONTRIBUTE.url` is blank, and its `mailto:` has **no recipient address**, so clicking it opens an email to nobody.

**Fix:** decide where corrections go (GitHub issues on this repo cost nothing and work today; a WPForms form is the long-term plan). Then fill `CONTRIBUTE.url` and add the same prompt to the other two tools.

## Fix next

### 4. The tools don't match the home page's type
The home page uses Walter Turncoat for body text. All three tools still use **Verdana** for body text, and in the Tag Builder even the **chips** are Verdana, which breaks the "Walter Turncoat chips" rule. Next to the home page, the tools look like a different site.
**Fix:** point the tools' body and chip styles at the same `--body` token the home page uses. *Your call:* Walter Turncoat is harder to read in long paragraphs, so you might keep Verdana for long glossary definitions only.

### 5. The Activity Finder title wraps to two lines on phones
"Small Business & Getaway Activity Finder" breaks onto two lines at 375px, which breaks the one-line title rule. This is fixed by the same change as #1, but at that length it will shrink quite small. A shorter cover title ("Activity Finder", matching the nav label) would read better.

### 6. Your gallery numbers are in the Tag Builder's source code
Nothing is shown on screen, but a code comment reads *"spaced follow-ups median 258 downloads against 74 same-day"*, and the chip ordering and weights come from your export. Anyone can read them with "view source", both here and on the live site.
**Fix:** delete the comment. Then decide whether the site says that the ordering comes from your upload history. That was already an open question, and saying so is the honest choice.

## Polish

### 7. Inconsistent bylines
The home page says "Made by dhahna" and the tools say "Built by @dhahna". The Tag Builder has no byline at all. Pick one form.

### 8. Small tap targets
Each tool has 1–4 controls under 24px tall, mostly checkboxes such as the "no spaces between tags" toggle. They're fiddly on a phone. Making the whole label clickable with some padding fixes it.

### 9. Page titles (browser tabs and search results) are inconsistent
- Home: "bb.moveobjects — Sims 4 building tools by dhahna"
- "Sims 4 Gallery Tag Builder"
- "Sims 4 House Style Finder — 50 US Architectural Styles & Build/Buy Picks"
- "Sims 4 Small Business & Getaway Activity Finder — Businesses & Hobbies + Adventure Awaits"

Suggested pattern: `<Tool name> · bb.moveobjects`. The long ones help search, so keep them only if you want search traffic.

## Suggested order

1 → 2 → 3 in one pass (a shared footer and cover fix across three files), then 4 and 5 together, then 6. The rest is polish.
