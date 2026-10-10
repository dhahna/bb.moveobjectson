# Contributing

This is a crowd-sourced project. Corrections and additions are the whole point.

## Ways to help

No GitHub account? Email **bb@moveobjects.com** instead; everything below works by email too.

- **Fix a glossary entry or tip.** Open an issue titled `Glossary: <term>` or `Tip: <topic>` with the correction and, if you have one, a source.
- **Fill a gap.** Anywhere a tool says something is missing, that's an open invitation.
- **Report a bug.** Say which tool, what you clicked, what you expected and what happened. A screenshot helps.
- **Suggest a mod or tool** for the builder recommendations list (planned). Include the creator, a link, and whether it adds objects (some builders post `#nocc` and can't use those).

## Credit

Accepted corrections go in with your name or handle, however you'd like to be credited.

## Ground rules for code changes

- Each tool stays a **single self-contained HTML file**: fonts and images embedded as base64, no CDNs, no analytics, no network calls.
- Keep the shared notebook design system consistent (see [docs/design-system.md](docs/design-system.md)).
- Don't add another creator's content or assets without their permission and credit.
- Test on mobile as well as desktop. Titles must never clip or wrap.
