# whiskey

Pages for the **Washington Whiskeys** silent auction lot at Washington Wild's Wild
Night Out, Wed 9/30/2026. One page per bottle, plus the lot page.

Live at https://whiskey.dandillinger.com, served by GitHub Pages from `main`.

| Path | Page |
|------|------|
| `/` | The lot: three bottles, three watersheds |
| `/westland/` | Westland American Single Malt, Seattle |
| `/woodinville/` | Woodinville 6 Year Straight Bourbon, Woodinville and Quincy |
| `/dry-fly/` | Dry Fly Triticale Whiskey, Spokane |

Plain HTML, no build step. Edit a page, commit, push; Pages redeploys in about a minute.

**This repo is public.** Only finished page copy goes here. Drafts, research and the
brief stay in `~/Documents/wawild/writing/washington-whiskeys-auction-card/`.

## Launch checklist

- [ ] Copy final for all three pages, with the house style applied (`wawild/writing/HOUSESTYLE.MD`)
- [ ] Remove `<meta name="robots" content="noindex">` from every page
- [ ] QR code on the auction card points at `https://whiskey.dandillinger.com/`

## DNS

`whiskey` CNAME → `dandillinger.github.io`, set in **Squarespace** DNS for
dandillinger.com. When that domain moves to Cloudflare (see maindesk
`domains/CONSOLIDATION-RUNBOOK.md`), carry this record over, and don't do the move
the week of the event.
