# ExchEngine — crypto rates monitor (front end)

A light, no-sign-up crypto rates monitor with charts, order books and market depth: **[www.exchengine.com](https://www.exchengine.com)**.
This repository holds the browser front end of the service as three plain HTML files. No build step, no dependencies, no tracking.

The code is light, the tools are not: 104 built-in indicators and oscillators, your own indicators in a formula language, drawing tools, order book and depth views, multi-exchange data. Heavy-metal analysis in featherweight code that still runs on Windows 7 and Android 7.

Блог о том, как всё началось (на русском): [Откуда есмь пошел мониторинг курсов](https://blog.exchengine.com/2026/10/exchengine-alternative-to-tabtrader-and-tradingview.html).

## What is in here

| File | What it is |
|---|---|
| `index-local.html` | Main page: notes (tiles) with live prices, watchlists, 22 interface languages |
| `chart-local.html` | Full-screen chart of a pair: 19 chart types, 104 built-in indicators and oscillators, drawing tools, your own indicators in a JS-like formula language, any timeframe |
| `book-local.html` | Order book, recent trades and market depth of a pair |

The files link to each other by relative names, so keep them in one folder.

## How to use it

* **On a computer:** download the three files into one folder and open `index-local.html` in a browser.
* **On Android:** put them into one folder (for example Downloads) and open `index-local.html` with Chrome.
* **From a web server:** any static hosting works; nothing is needed on the server side.

Works in browsers as old as Windows 7 / Android 7 era Chrome, and in current ones. Notes, watchlists and chart markup are stored in your browser only (`localStorage`).

## Where the data comes from

Prices, candles, order books and trades are requested from the public API of `www.exchengine.com` (read-only market data collected from the exchanges). The API has per-client rate limits, so please be gentle with it. It is provided as is, without any guarantee of availability. This repository does not contain the server side.

## Differences from the online version

These files are generated from the live site's files. Everything that cannot work from a local copy is removed or switched off.

**Removed**

* **Add shortcut** (install as an app): it needs the site's own manifest and service worker.
* **Contact form with captcha**: the server accepts it only from the site itself. The e-mail addresses stay in the Contacts window.
* **Slow-link mode** ("cheburnet penetration"): loading the page in small parts and the offline copy kept by a service worker, both built for blocked or throttled networks and both relying on the site's own server.
* **Search-engine side**: canonical links, structured data and the hidden text for crawlers are gone, and the pages are `noindex`.

**Changed**

* All links between the three pages are relative: `index-local.html` ↔ `chart-local.html` ↔ `book-local.html`.
* Market data always comes from `www.exchengine.com`, wherever you open or host the files.
* Pictures (logo, mascot) are embedded in the pages, so they appear without the network. Only the browser-tab icon is taken from `www.exchengine.com`.
* The footer says "Released under the MIT License" instead of "All rights reserved".
* Links to the site's price, chart and order-book pages (footer ticker) open the live site.

**Good to know**

* Notes, watchlists and settings live in your browser, per address. The local copy and the live site do not share them: move them with **Settings → Import / Export**.
* Some browsers keep files opened from disk apart from each other, so a setting such as the language may not carry from one page to the next. Opening the three files through any local web server avoids that.
* Everything else (exchanges, indicators, drawing tools, 22 languages, sanctions notices for MEXC and HTX) works as online.

## Feedback

Found a bug, have an idea, or something looks odd on your device? Please open an [issue](../../issues) or start a [discussion](../../discussions): browser, OS and a screenshot help a lot.
The files are regenerated from the live site, so a fix is made there and then appears here in the next update.

Building something on top of this, or need more from the data API than the shared limits allow (higher limits, stored history, order-book snapshots)? Write to collab@exchengine.com, we are glad to collaborate.

## License

The code is released under the [MIT License](LICENSE). The ExchEngine name, logos and illustrations are not covered by it, see [TRADEMARKS.md](TRADEMARKS.md).
