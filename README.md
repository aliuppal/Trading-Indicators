# V-Shape Liquidity Toolkit (TradingView / Pine Script v6)

One overlay indicator with six modules you can switch on and off:

| # | Module | What it draws |
|---|--------|---------------|
| 1 | **DOL (Draw on Liquidity)** | Dashed lines at the nearest unswept swing high/low above and below price, labelled `DOL: Swing H/L` (external) or `DOL: Internal Swing H/L`. Lines disappear once that liquidity is swept. |
| 2 | **HTF FVGs** | Fair Value Gaps from 15m / 1H / 4H (configurable), drawn on your execution chart. They don't repaint (they use closed HTF candles only), and they're removed once price closes through them or fills the gap (your choice). |
| 3 | **LRL (Low Resistance Liquidity)** | Orange dashed trendline through a run of internal lower highs (or higher lows). A close through it prints `BREAKS LRL`, meaning the path to the DOL is now low resistance. |
| 4 | **HTF PO3 candle** | The current HTF candle (plus previous ones) drawn to the right of price, with the HTF open line and `A` / `M` / `D` markers (accumulation open, manipulation wick, distribution close). |
| 5 | **V-Shape confirmation** | Price runs from a leg extreme, **sweeps a swing low/high**, then **closes back beyond the leg's origin** within *N* bars. The V gets a box and is labelled REVERSAL or CONTINUATION based on the external structure. Optional entry / SL / target boxes (target = next DOL, or a fixed RR). |
| 6 | **SMT** | Divergence between correlated markets at swing pivots (e.g. NQ makes a lower low while ES makes a higher low). The correlated symbol is picked for you for NQ/ES/MNQ/MES/YM/RTY, EURUSD/GBPUSD and BTC/ETH, or you can set your own. |

## Install
1. Open TradingView → **Pine Editor** (bottom panel).
2. Delete the template code, paste the contents of `V-Shape-Liquidity-Toolkit.pine`.
3. Click **Save**, then **Add to chart**.
4. Open the indicator **Settings** to toggle modules, change timeframes and colours.

## Suggested use
**HTF narrative first → DOL second → V-Shape confirmation last.**
Run it on a low timeframe (1m–5m) execution chart. HTF FVGs and the PO3 candle only show when the chart timeframe is lower than the HTF you selected.

## Alerts
Create an alert on the indicator and pick one of: Bullish/Bearish V-Shape, Bullish/Bearish SMT, LRL broken, Buy-side/Sell-side liquidity swept.

> This tool visualizes concepts. It is not a signal service or financial advice.
