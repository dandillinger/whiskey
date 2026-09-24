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

## DNS

`whiskey` CNAME → `dandillinger.github.io`, set in **Squarespace** DNS for
dandillinger.com. When that domain moves to Cloudflare (see maindesk
`domains/CONSOLIDATION-RUNBOOK.md`), carry this record over, and don't do the move
the week of the event.
