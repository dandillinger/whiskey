# whiskey

Pages for Dan's silent auction lot at Washington Wild's **Wild Night Out**, one year
at a time. Live at https://whiskey.dandillinger.com, served by GitHub Pages from `main`.

| Path | What |
|------|------|
| `/` | Every year's lot, newest first. Built automatically |
| `/2026/` | 2026 lot page: Washington Whiskeys |
| `/2026/westland/` etc. | One page per bottle |

Pages are Markdown with front matter. GitHub Pages renders them with the layouts in
`_layouts/`, so there's no local build step. Edit, commit, push, and it redeploys
in about a minute.

**This repo is public.** Only finished page copy goes here. Drafts, research and the
brief stay in `~/Documents/wawild/writing/`.

## Each year

1. `mkdir YYYY`, then copy `_template/index.md` to `YYYY/index.md` and
   `_template/item.md` to `YYYY/<slug>.md`, one per bottle
2. Fill in the front matter: `year` on every file, `order` for the bottle sequence,
   and the event date, value and donor on the lot page
3. Write the copy under the front matter, applying `wawild/writing/HOUSESTYLE.MD`
4. At launch, delete `draft: true` from each file to drop the `noindex`
5. The QR code on that year's card points at `https://whiskey.dandillinger.com/YYYY/`

Past years stay up as they are. Don't rename a year's slugs after its card is
printed.

## Hosting runbook

Set up Sep 23–24, 2026. You only need this again if hosting breaks or DNS moves.

### Pieces

| Piece | Where | Setting |
|-------|-------|---------|
| Site | GitHub Pages, this repo, `main` branch, `/` | Legacy Jekyll build |
| Custom domain | Repo Settings → Pages, plus the `CNAME` file | `whiskey.dandillinger.com` |
| DNS | Squarespace → Domains → dandillinger.com → DNS → Custom Records | `CNAME` `whiskey` → `dandillinger.github.io` |
| HTTPS | Repo Settings → Pages → Enforce HTTPS | Let's Encrypt certificate, issued by GitHub |

Changing DNS at Squarespace requires an emailed verification code, which you have to
enter yourself.

### Order matters

**Add the DNS record before setting the custom domain in GitHub.** On Sep 23 the domain
was set first. GitHub's lookup then hit dandillinger.com's wildcard `*` A record,
which points at the Network Solutions parking IP with a 4-hour TTL, and the certificate
stuck at `authorization_created`. Three resets through the API did not clear it.

### If HTTPS is stuck (Enforce HTTPS greyed out)

1. https://github.com/dandillinger/whiskey/settings/pages → clear **Custom domain** →
   **Remove**
2. Wait 30 seconds, re-enter `whiskey.dandillinger.com` → **Save**
3. Wait for "DNS check successful"
4. When **Enforce HTTPS** is clickable, tick it. Usually within 15 minutes, up to 24 hours
5. Still greyed out after an hour: https://github.com/settings/pages → **Add a domain** →
   `dandillinger.com`. Add the TXT record it shows at Squarespace (Custom Records →
   type `TXT`), click **Verify**, then redo steps 1–4

Each remove and re-add commits to the `CNAME` file, so `git pull` before editing.

### Check

```sh
dig +short whiskey.dandillinger.com                                    # → dandillinger.github.io
gh api repos/dandillinger/whiskey/pages --jq '{status,https_enforced,cert:.https_certificate.state}'
curl -sI https://whiskey.dandillinger.com/2026/ | head -1              # → 200
curl -sI http://whiskey.dandillinger.com/2026/ | grep -i location      # → https://…
```

## DNS

`whiskey` CNAME → `dandillinger.github.io`, set in **Squarespace** DNS for
dandillinger.com. When that domain moves to Cloudflare (see maindesk
`domains/CONSOLIDATION-RUNBOOK.md`), carry this record over, and don't do the move
the week of the event.
