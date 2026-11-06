# TAO · BTC · AUD Calculator

Mobile-first dark converter for **TAO ↔ AUD**, **BTC ↔ AUD**, and **sats ↔ AUD**.

- Live rates from [CoinGecko simple/price](https://api.coingecko.com/api/v3/simple/price?ids=bittensor,bitcoin&vs_currencies=aud,btc) (`bittensor`, `bitcoin` vs `aud` + `btc`)
- Fallback book baseline: **1 TAO = A$326.13** if offline
- **1 BTC = 100,000,000 sats**
- Optional **24% tax reserve** (AUD field shows net when enabled)
- Local-only persistence (`localStorage`) — no accounts, no wallets
- PWA shell: `manifest.webmanifest` + `sw.js` (offline UI; prices still need network)

## Public URL

GitHub Pages (after deploy):

`https://superuserdoakasudo.github.io/tao-btc-aud-calculator/`

## Wrap as an Android WebView app (for Claude / CapCut-style packaging)

Minimal Android activity:

1. Create an empty Android app (minSdk 24+).
2. `AndroidManifest.xml`: add `INTERNET` permission; set `usesCleartextTraffic="false"`.
3. Layout: full-screen `WebView`.
4. In `MainActivity`:

```kotlin
webView.settings.javaScriptEnabled = true
webView.settings.domStorageEnabled = true
webView.settings.cacheMode = WebSettings.LOAD_DEFAULT
webView.webViewClient = WebViewClient()
webView.loadUrl("https://superuserdoakasudo.github.io/tao-btc-aud-calculator/")
```

5. Optional: enable `setDomStorageEnabled(true)` so tax/tab preferences persist inside the WebView.
6. Do **not** inject Java bridges or load `file://` — use the HTTPS URL above so CoinGecko CORS works.

No private keys, seed phrases, or wallet addresses belong in this app.

## Local test

```bash
python3 -m http.server 8765 --directory .
# open http://127.0.0.1:8765/
```

## License

Public domain / CC0 — use freely.
