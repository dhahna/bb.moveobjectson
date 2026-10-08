# Design system

The look is a **90s high-school girl's notebook**: a composition notebook cover, ruled and gridded paper, and highlighter accents. The Sims 4 *Mean Girls* and *Clueless* kits are the reference points. The site should read Sims-focused first and building-focused second.

## The rule that holds everything together

**Each tool is its own notebook, and every notebook is the same notebook.** The cover/header, page background, link colours and text colours are identical in every tool. What changes is the sections *inside* a tool: each section gets its own highlighter colour pair.

## Colour

| Token | Value | Use |
|---|---|---|
| Page background | `#e6f2fb` | Very pale Sims blue, echoing the blue grid on the paper |
| Margin rule / pink accent | `#e0aabb` or `#ef6f9c` | ⚠️ Both values appear in project notes. Check the live files and settle on one. |
| Plumbob green | `#2ba355` | The dot in the wordmark; the plumbob sticker. The plumbob is always green. |
| `--plumbob` CSS token | pink | Link colour token only (the name is historical) |
| Section highlighters | 15 rotating pairs | Each pair = a light fill + a darker tint for borders |

## Type

- **Headings:** Momo Signature
- **Chips and body text:** Walter Turncoat (this replaced Verdana for body text everywhere except titles)
- **Wordmark:** Verdana bold
- Fonts are embedded as base64. No Google Fonts calls.
- **Title Case** for titles and every chip label.
- **Titles stay on one line.** Shrink the font to fit; never wrap. Watch grid children: they need `min-width: 0` or a `nowrap` title will push the container wider than the screen, and fit-to-width scripts will measure the stretched container and never shrink. This caused clipping on mobile before.

### Fonts

All of these are SIL Open Font License and safe to embed and redistribute:
Momo Signature, Walter Turncoat, Yusei Magic, Playwrite US Trad, Architects Daughter, Cedarville Cursive, Coming Soon, Gochi Hand, Hi Melody, Indie Flower, Nanum Pen Script, Protest Riot, Satisfy, Zeyada.

## Wordmark

`bb.moveobjects` in Verdana bold with a green dot (`#2ba355`) and a blinking block cursor after it. In headers it can carry a handwritten **"on"** in Momo Signature with a yellow highlighter behind it. Users who prefer reduced motion get a static cursor. There is no separate brand name: the domain is the identity. ("Build Notes" was considered and rejected.)

## Paper, borders, shadows

- Cards are ruled or gridded paper with the pink margin rule.
- Hard **3px offset shadows**, not soft blurs.
- Borders: the section heading is coloured with no fill; chip borders use the darker tint of the section colour; **fill appears only on selection.**

## Cover art

- A CSS-generated **marble** composition-notebook cover (this was chosen over a photographed cover image).
- A sticker sits *below* the title: plumbob gem only, no wordmark.

## Home page

The **bookcase** treatment (`index.html`) is the live one: three composition books on a shelf, one per tool, labelled by category:

- Inspiration · Residential → House Style Finder
- Inspiration · Commercial → Small Business & Getaway Activity Finder
- Posting → Gallery Tag Builder

Stat stickers are SVG circles so the text always fills them at any size. Don't make the shelf near-black, because the black cloth spines then read as VHS cassettes. A **locker** variant (`locker.html`) was built and not chosen.

A shared nav strip on every page links back to `https://bb.moveobjects.com`.

## Footer

Every page carries the EA disclaimer (modelled on Carl's Sims Guide), in small muted type under the byline.
