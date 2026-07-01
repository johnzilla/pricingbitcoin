# pricingbitcoin

A single-page **BIP-110 mandatory-signaling countdown** for Bitcoin, live at
[pricingbitcoin.com](https://pricingbitcoin.com).

It shows, straight from the chain:

- **Current block height** — from [mempool.space](https://mempool.space) (falls back to blockchain.info)
- **Blocks remaining** until block **961,632**, when BIP-110 mandatory signaling begins, plus a rough time estimate at 10 min/block
- **Miner signaling** — the share of recent blocks setting version **bit 4**, computed client-side, shown against the **55%** activation threshold
- **BTC price** in several currencies — from [CoinGecko](https://www.coingecko.com)

## About BIP-110

BIP-110 enforces mandatory signaling (bit 4) during the retarget period starting at
block 961,632. Activation requires 55% of blocks in a difficulty period to signal.
See the [BIP text](https://github.com/bitcoin/bips/blob/master/bip-0110.mediawiki)
and [bip110.org](https://bip110.org) for details.

> Note: the block-height countdown is honest chain data. The signaling percentage is
> sampled from the most recent ~45 blocks (a live estimate), not the full retarget window.

## Running locally

It's a static site — serve the folder with any static server, e.g.:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

A service worker (`sw.js`) caches the app shell for offline load; the site is an
installable PWA.

## Files

- `index.html` — the whole app (markup, styles, script)
- `sw.js` — service worker (app-shell cache)
- `manifest.json` — PWA manifest
- `icon-*.png` — PWA icons
- `CNAME` — GitHub Pages custom domain
