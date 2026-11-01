# V-Shape Liquidity Toolkit (TradingView / Pine Script v6)

One overlay indicator with seven modules you can switch on and off:

| # | Module | What it draws |
|---|--------|---------------|
| 1 | **DOL (Draw on Liquidity)** | Dashed lines at the nearest unswept swing high/low above and below price, labelled `DOL: Swing H/L` (external) or `DOL: Internal Swing H/L`. Lines disappear once that liquidity is swept. |
| 2 | **HTF FVGs** | Fair Value Gaps from 15m / 1H / 4H (configurable), drawn on your execution chart. They don't repaint (they use closed HTF candles only), and they're removed once price closes through them or fills the gap (your choice). |
| 3 | **LRL (Low Resistance Liquidity)** | Orange dashed trendline through a run of internal lower highs (or higher lows). A close through it prints `BREAKS LRL`, meaning the path to the DOL is now low resistance. |
| 4 | **HTF PO3 candle** | The current HTF candle (plus previous ones) drawn to the right of price, with the HTF open line and `A` / `M` / `D` markers (accumulation open, manipulation wick, distribution close). |
| 5 | **V-Shape confirmation** | Price runs from a leg extreme, **sweeps a swing low/high**, then **closes back beyond the leg's origin** within *N* bars. The V gets a box and is labelled REVERSAL or CONTINUATION based on the external structure. Optional entry / SL / target boxes (target = next DOL, or a fixed RR). |
| 6 | **SMT** | Divergence between correlated markets at swing pivots (e.g. NQ makes a lower low while ES makes a higher low). The correlated symbol is picked for you for NQ/ES/MNQ/MES/YM/RTY, EURUSD/GBPUSD and BTC/ETH, or you can set your own. |
| 7 | **Sessions & previous day** | Shades the **Asia** (20:00–00:00 NY) and **London** (02:00–05:00 NY) session ranges. Each session high/low (`ASIA H/L`, `LONDON H/L`) and the **previous day high/low** (`PDH` / `PDL`) is extended right until price sweeps it, then fades or is deleted. Session times and timezone are editable. |

## Install
1. Open TradingView → **Pine Editor** (bottom panel).
2. Delete the template code, paste the contents of `V-Shape-Liquidity-Toolkit.pine`.
3. Click **Save**, then **Add to chart**.
4. Open the indicator **Settings** to toggle modules, change timeframes and colours.

## Suggested use
**HTF narrative first → DOL second → V-Shape confirmation last.**
Run it on a low timeframe (1m–5m) execution chart. HTF FVGs and the PO3 candle only show when the chart timeframe is lower than the HTF you selected.

## Alerts
Create an alert on the indicator and pick one of: Bullish/Bearish V-Shape, Bullish/Bearish SMT, LRL broken, Buy-side/Sell-side liquidity swept, Session high/low swept, PDH/PDL swept.

> This tool visualizes concepts. It is not a signal service or financial advice.

---

# HTF FVG Scalper (`HTF-FVG-IFVG-Scalper.pine`)

A second, separate indicator built for **NQ1! / MNQ1! scalping**.

| Feature | Details |
|---|---|
| **HTF FVGs** | 5m, 15m, 30m, 1H, 2H, 4H and Daily, each with its **own on/off switch and colour**. They don't repaint. When price trades into one, the box turns solid and is labelled **TAPPED**. |
| **Asia / London** | The session high and low are drawn as lines until swept (Asia 20:00–00:00, London 02:00–05:00 NY; editable). |
| **PDH / PDL** | Previous day high and low lines, starting at the actual high/low candle and extended until swept. |
| **DOL** | Dashed lines at the nearest untaken swing high/low (`DOL: Swing H`, `DOL: Internal Swing L`). The status panel shows the next DOL above and below price, counting swings, PDH/PDL and Asia/London levels. |
| **LRL** | Trendline through a run of lower highs or higher lows. A close through it prints `BREAKS LRL`. |
| **Displacement** | Large-bodied candles (body ≥ 1.5× ATR and ≥ 60% of the range) are marked with triangles, with optional candle colouring. |
| **V-Shape IFVG entry** | On the entry timeframe (**1m / 2m / 3m / 5m**): an FVG forms, then within *N* bars a candle **closes through it** (inversion), optionally with displacement. The IFVG zone is boxed and labelled. |
| **Brackets** | Entry (inversion close), SL (leg extreme + buffer) and TP (the **next DOL** in the trade direction, or an R multiple). They're **only drawn if an HTF FVG in the same direction was tapped** within the last *N* bars. SMT in the same direction can also be required. |
| **SMT** | Divergence against the **symbol you choose** in settings (default `CME_MINI:ES1!`; use `CME_MINI:MES1!` for MNQ). |
| **Status panel** | Shows the entry TF, the last bullish/bearish HTF tap, the SMT state and the bracket mode. |
| **Alerts** | Long/short setup (the message includes entry, SL and TP/DOL), any IFVG, HTF FVG tapped, SMT, session high/low swept, PDH/PDL swept, LRL broken. |

**Chart:** use a **1-minute** chart so every entry timeframe works. If the entry TF is set lower than the chart TF, the chart TF is used and the panel shows a ⚠ warning.
