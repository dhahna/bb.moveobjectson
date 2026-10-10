# Deploying to SiteGround

Every change to an `.html` file on `main` is uploaded to SiteGround automatically by `.github/workflows/deploy-siteground.yml`. Only the HTML pages are uploaded. Nothing on the server is deleted, so WordPress stays as it is.

## One-time setup

**In SiteGround** (Site Tools for bb.moveobjects.com):
1. **Devs → SSH Keys Manager → Generate.** Give it a name (e.g. `github`) and a passphrase, then create it.
2. Click the key's **⋮ menu → Private Key** and copy the whole thing, including the `-----BEGIN` and `-----END` lines.
3. On the same page, note the **SSH credentials**: hostname, username and port (the port should be 18765).
4. **Site → File Manager:** find the folder the live site's HTML files are in (likely `www/bb.moveobjects.com/public_html`). Its full path is `/home/<username>/www/bb.moveobjects.com/public_html`. Check before saving it.

**In GitHub** (repo → **Settings → Secrets and variables → Actions → New repository secret**), add:

| Name | Value |
|---|---|
| `SG_SSH_KEY` | the private key from step 2 |
| `SG_SSH_PASSPHRASE` | the passphrase from step 1 |
| `SG_HOST` | the hostname from step 3 |
| `SG_USER` | the username from step 3 |
| `SG_PATH` | the folder path from step 4, no trailing slash |

Then go to **Actions → Deploy to SiteGround → Run workflow** to test it. The run's last step fetches every page back from bb.moveobjects.com and reports "live matches" for each one. A run that only says "SiteGround secrets not set" (a yellow warning) uploaded nothing.

## Notes

- Never put the key itself in a file in this repo. It is public.
- To stop auto-deploys, disable the workflow under Actions.
