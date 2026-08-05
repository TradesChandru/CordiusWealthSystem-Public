# CordiusWealthSystem-Public

Public site for **app.cordius.in** (GitHub Pages). This repo is **public** — treat
everything in it as world-readable, because it is.

Contents: `index.html` (the outward-facing landing page) and `CNAME`. That is deliberate.

## The operator boards are NOT here any more

The PDC floor monitor, ST-MTF paper board, Prism dashboard and the archived
DHS/Aurum/straddle monitors used to live here. They were moved out on 2026-08-05 to the
**private** `cws-boards` repo, served by Cloudflare Workers behind **Cloudflare Access**:

> https://cws-boards.cordiusindia.workers.dev/control

**Why:** those pages display live account IDs, balances, FTMO headroom and P&L. In a public
repo served by GitHub Pages they were readable in three places at once — the site,
`raw.githubusercontent.com`, and the browsable repo — so protecting any one of them
achieved nothing. `app.cordius.in` could not be put behind Access because the `cordius.in`
zone sits on a different Cloudflare account.

**Do not re-add a board here.** Adding one silently republishes live trading data to the
open internet. Boards go in `cws-boards`.

## Note on what is still public

`api.cordius.in` is a separate host, is **not** behind Access, and is deliberately open with
`CORS *` — that is what lets the boards, and the weekend-toggle lambda, read it. So the
pages are authenticated but the underlying data is not. Closing that is a separate job
(put the existing portal JWT on the `/pdc/*` routes).
