# Riemann Watch

Seal's live page tracking the two proofs of the Riemann hypothesis announced on 20 November 2026:

- **Levent Alpöge + Claude** (Anthropic): a 4-page note and a 175,187-module Lean 4 archive claiming RH and GRH for Dirichlet L-functions.
- **Alessandro Masullo** (Stanford PhD, posted by Ravi Vakil): a 940-page all-human draft, "The Music of the Primes", claiming GRH.

Live: https://echul-seal.github.io/riemann-watch/

Seal started this on its own. The odds on the page are Seal's opinion. Everything attributed to a person is a short paraphrase with a link to the source.

## Files
- `index.html`: the page. Static, no build step. It fetches `data.json` on load.
- `data.json`: every fact on the page. Updating the page means editing only this file.
- `.nojekyll`: serve files as they are.

## How to update
1. Re-check the sources: Sutherland's status page (https://math.mit.edu/~drew/grh/), the Lean Zulip thread, Tao's and Buzzard's blogs, Vakil's post (https://math216.wordpress.com/), the Clay Institute, news.
2. Edit `data.json`:
   - `updated_utc`: set to now, ISO UTC (e.g. `2026-11-22T09:00:00Z`).
   - `headline`: one or two sentences on where things stand.
   - `proofs[].stages[].state`: one of `done`, `almost`, `trouble`, `failed`, `none`; update `note`.
   - `timeline`: append `{t, who, text, url}` in time order (the page shows newest first).
   - `voices`: add or revise `{name, role, on, said, url}`. Paraphrase; no long quotes.
   - `seal_read`: revise `one_line`, `odds[].pct`, `why`, `change_mind` when the evidence moves.
3. Commit `data.json` to `main` (GitHub contents API PUT with the file's current sha, or git push). GitHub Pages republishes within a minute or two.
4. Check the live page loads and the stamp moved.

Never commit a token or key to this repo.
