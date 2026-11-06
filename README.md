# TAO · BTC · Fiat → AUD Calculator

Mobile-first dark converter:

| Tab | Converts |
|-----|----------|
| **TAO** | Bittensor ↔ AUD (+ optional 24% tax reserve for reward planning) |
| **BTC** | Bitcoin ↔ AUD |
| **Sats** | Satoshis ↔ AUD (`1 BTC = 100,000,000 sats`) |
| **USD** | US dollar ↔ AUD |
| **EUR** | Euro ↔ AUD |

## Rate sources

- **Crypto:** [CoinGecko](https://api.coingecko.com/api/v3/simple/price?ids=bittensor,bitcoin&vs_currencies=aud,btc) — `bittensor`, `bitcoin` vs `aud` + `btc`
- **Fiat:** [Frankfurter](https://api.frankfurter.dev/v1/latest?from=EUR&to=AUD,USD) — ECB daily eurofxref rates (`EUR→AUD`, `EUR→USD`; USD/AUD via EUR cross)
- Independent fetches; offline falls back to **Cached reference** (TAO A$326.13, BTC A$114,344, EUR A$1.77, USD A$1.52)

Tax reserve applies **only on the TAO tab** (subnet reward planning). Fiat tabs are plain FX.

## Public URL

https://superuserdoakasudo.github.io/tao-btc-aud-calculator/

## Android WebView wrap

```kotlin
webView.settings.javaScriptEnabled = true
webView.settings.domStorageEnabled = true
webView.webViewClient = WebViewClient()
webView.loadUrl("https://superuserdoakasudo.github.io/tao-btc-aud-calculator/")
```

Needs `INTERNET`. Prefer the HTTPS URL (not `file://`) so CoinGecko + Frankfurter CORS work. No wallets / seeds.

## Local test

```bash
python3 -m http.server 8765 --directory .
```

## License

CC0 / public domain.
