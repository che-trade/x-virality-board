# cheTrade X Virality Board

Public GitHub Pages dashboard for [@chetrade_](https://x.com/chetrade_).
Live URL (once published): https://che-trade.github.io/x-virality-board/

Static site, no build step, no API keys:

- `index.html` – single-file board (inline CSS + JS), adapted from the
  `board/` starter in [monkeyteamvip/x-virality-score](https://github.com/monkeyteamvip/x-virality-score).
- `data.json` – everything the page shows. The page fetches `./data.json` at load.
- `.nojekyll` – tells GitHub Pages to serve the files as-is.

## What it shows

1. **X Score / Board Target**: hit count and total views from each watchlist account's best post vs targets (12 hits, 100K views).
2. **7-day rank**: each account's best and total views in the sampled week.
3. **Charts**: top hit views and best views per account.
4. **Leaderboards**: rolling week (hits ≥5K, best / total). The month board fills in once daily digests start.
5. **Watchlist**: 25 accounts with followers, posts per 7 days (`~` means estimated), median views, median engagement, niche and a best-post link.
6. **Best post per account**: ranked cards. ★ means 10K+ views.
7. **All posts that already hit**: every sampled original with 5K+ views, ranked by views. Shows the top 30, with a toggle to show all.
8. **Keywords & patterns**: tickers, words and phrases mined from the text of the hit posts, with how many posts contain each.
9. **Drafts / Outside radar**: empty ("none yet") until real drafts or outsider scrapes exist.

Times are shown in Europe/Brussels.

## Refresh

On the box: `python3 /workspace/xvirality/build_board_data.py` rebuilds `data.json`
from `config/watchlist.json`, `watchlist_candidates.json` and `raw/posts_by_handle.json`.
Then upload `index.html` + `data.json` (+ `.nojekyll`) to the `main` branch root of `che-trade/x-virality-board`
and enable Pages (Deploy from branch → `main` / root).

## Preview locally

```bash
python3 -m http.server 8765   # in this folder, then open http://127.0.0.1:8765/
```

Opening `index.html` straight from disk with `file://` blocks the `data.json` fetch.

## Notes

- Views are X impression counts from a read-only scrape. Accounts that post a lot are sampled (about their latest 25 posts), so their totals cover only the sampled posts.
- Not affiliated with X Corp. Posts belong to their authors.
