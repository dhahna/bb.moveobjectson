# CLAUDE.md: handoff for anyone (human or AI) working on this repo

Read this first, then `docs/design-system.md` and `docs/roadmap.md`.

## Who and what

- **Owner:** Dana Hahn, EA ID **@dhahna**. A Sims 4 gallery builder since 2020 (building-focused, 3k+ uploads, plays on Mac).
- **Project:** bb.moveobjects, a free, open-source site of Sims 4 building tools and a "START HERE" front door for newer builders. Live at **bb.moveobjects.com**.
- **Authorship:** Dana built these tools herself, using Claude as a tool. The knowledge in them is entirely hers. **Never describe the tools as commissioned**, and never invent first-person anecdotes, motivations or "things I wish I'd known" in her voice. If copy needs her voice and you don't have her words, leave a clearly marked placeholder and ask.

## Hard rules

1. **Single self-contained HTML per tool.** Base64 fonts and images, no CDNs, no analytics, no network calls. They must work when downloaded and opened offline.
2. **Public builds contain no personal data.** No performance figures, no projected-download readouts, no "weaker choice" chip colouring, and no hardcoded handle (the public Tag Builder has an EA ID field instead). Dana keeps a separate personal build with her export data. It does not belong in this repo.
3. **Crowd-sourced honesty.** Where something is missing or unverified, say so plainly and invite corrections. Don't present guesses as fact. Glossary entries written by AI that Dana hasn't reviewed must be flagged as unreviewed.
4. **Attribute everything.** Tips are tagged by source (measured from data / a contributor's / Dana's). Contributors get named credit.
5. **EA disclaimer on every page.** Not affiliated with EA or Maxis.
6. **Design consistency.** Follow `docs/design-system.md`. Every tool is the same notebook; only the sections inside a tool change highlighter colour.
7. Titles and chip labels in **Title Case**; titles never wrap (shrink instead), including on mobile.

## Repo layout (target)

```
index.html                          bookcase home page (live)
sims-tag-builder-public.html        Gallery Tag Builder
sims4-house-style-finder.html       House Style Finder
sims-business-activity-finder.html  Small Business & Getaway Activity Finder
docs/design-system.md
docs/roadmap.md
AUDIT.md                            consistency / mobile / content audit (Oct 2026)
```

Files sit at the root because that's how the live site is laid out: the pages link to each other by bare filename and to `https://bb.moveobjects.com/<file>`. Keep the names; renaming breaks live links. These are the Sep 16 2026 versions from Dana's computer. **Don't rebuild a tool from scratch.** Edit the file that's here.

## Tool notes

### Gallery Tag Builder
- Build scope is chosen first: Lot, Room or Shell. Dana's own build order is Shell → Rooms → Lot.
- Generates gallery titles, a description and hashtags from chip selections.
- The description ends with the marker **`[[bb.moveobjects.com]]`** (changed from `[[bb.moveobjects on]]`). It still matches gallery searches for `bb.moveobjects` and credits the tool. Trade-off noted: the old form also told builders "MOO was used"; `#moo` in the tags now carries that.
- CC line: "No CC, no mods." or "No CC, no mods, no packs." depending on selections.
- **500-character description cap** (EA's limit): meter with progress bar, green/amber/red states, a visible ✂ marker showing which tags will be truncated, a "no spaces between tags" toggle to save characters, click-to-remove for individual tags with a restore row.
- The description is editable; manual edits survive chip changes. The field is not re-rendered while the user is typing (that would make the caret jump). Paste strips formatting. **Clear all** resets edits too.
- Tag counter lives in the sticky sidebar next to Clear all and reads zero until the first manual selection.
- Pack counts stay out of titles (the "only show what I own" filter handles that). Pack *names* may appear in titles.
- Chip *ordering* is still derived from Dana's own gallery export, even though the numbers are stripped. Whether to say so on the site is undecided.
- Description logic avoids repeating itself: a structure doesn't restate the lot's phrase and a use doesn't restate the room (see `dropEchoes`).

### House Style Finder
- Tabs; colours scoped to content sections, not whole tabs.
- A definition card answers "what is that?" before showing filtered results, with a path back to the style card.
- About 180 glossary entries; 117 of them were AI-drafted and are **flagged unreviewed**. Missing entries prompt for crowd-sourced contributions.
- Build tips are limited to base-game techniques.
- A `CONTRIBUTE` config object at the top of the injected script holds the correction-form URL so it can be swapped with a one-line edit. It points at GitHub issues on this repo for now (`https://github.com/dhahna/bb.moveobjectson/issues/new`); a WPForms page is the long-term plan. The same link sits in every tool's footer under "Send us the wording".

### Small Business & Getaway Activity Finder
- Which activities are available as Club Activity, Small Business Customer/Employee, or Getaway activity, by pack. Built around Businesses & Hobbies.
- Reference source: konanhurry's activity master spreadsheet (from the *Club & Business Activity Expanded* mod). Credit konanhurry wherever that data is used.

## Gallery knowledge worth building into tools and guides

These are Dana's working methods. Label them as one builder's methods.
- "Post" means save to My Library first; upload to the gallery later.
- One build can be posted under several gallery categories (a great room under Career/Misc, Living Room and Kitchen).
- Temporarily wall off an open-plan great room to post the kitchen and living room separately under their own categories.
- Space those uploads out to appear repeatedly in "Newly Added".
- My Library (the Tray folder) is stored locally, not on EA's servers, so builds can be lost when you switch computers. Back it up.
- My Library's "Newest" sort uses a date stored inside each `.trayitem`, not the file's date.
- EA's gallery search endpoint caps results at 500, which limits any export or stats tool.
- Follower counts have been inaccessible through the gallery since March 2026.

## Deployment

- Hosted on SiteGround (static HTML at `bb.moveobjects.com`; WordPress is also installed there). `moveobjects.com` redirects to it.
- SiteGround's file manager extracts a zip into a folder named after the zip. That caused a 403 once. Upload files, or extract and then move them.
- Search indexing has been discouraged during the build. Turning it on is Dana's call.
- An SFTP client (Cyberduck or Transmit) is planned but not set up.
- Possible future: GitHub Pages as a mirror or deploy source. Ask before changing where the live site comes from.

## Tone

Not cheesy, not salesy. Plain and direct, written by a builder who worked it out the hard way and is handing over the map. No "unlock your creativity", no exclamation-point enthusiasm.

## Working style

- Dana wants real opinions and initiative, not just agreement, while respecting that she knows Sims building best.
- Don't invent names, brands or copy. Ask.
- Show work in progress early; she'll redirect.
