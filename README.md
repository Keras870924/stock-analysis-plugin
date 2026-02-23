# Stock Analysis Plugin

A Claude Code skill for analyzing US and Taiwan stocks using a structured two-layer framework — combining fundamental screening with technical timing.

Reports are generated in a bilingual (Chinese/English) Apple-style format and automatically saved as Markdown files.

---

## Installation

In Claude Code, run:

```
/plugin marketplace add Keras870924/stock-analysis-plugin
```

---

## Usage

### Report Mode
Provide a ticker and Claude auto-generates a full analysis report:

```
幫我分析 NVDA
幫我分析 AAPL
幫我分析 4958
幫我分析 2330
```

### Interactive Mode
Claude guides you through each layer with questions:

```
引導我分析 GOOGL
```

### Custom Save Path
By default reports are saved to `./reports/TICKER-YYYY-MM-DD.md`. Override with:

```
幫我分析 NVDA，存到 ~/Desktop
幫我分析 AAPL，存到 D:/stocks
```

---

## Analysis Framework

### Layer 1 — Fundamental Analysis 基本面分析

**Step 1: Business Model Screen**
- Can you explain the business in 5 minutes? (Pass/Fail gate)
- Moat score (0–4): Undifferentiated product · Widest users · Free pricing · Market monopoly

**Step 2: Financial Health**

| Metric 指標 | Standard 標準 | Red Flag 紅旗 |
|-------------|--------------|--------------|
| Annual Revenue 年收入 | ≥ $100M USD | < $100M = pre-scale |
| Revenue Growth 收入成長 | 15–20% ideal | < 10% = stalling |
| EBIT Margin 營業利潤率 | Positive; same-industry only | Negative = broken model |
| Operating Cash Flow 營運現金流 | Must be positive | Negative = not earning |
| Free Cash Flow 自由現金流 | Ideally positive | Negative = no flexibility |

**Step 3: Valuation**
- P/E · P/S · P/B vs. sector peers
- Goal: understand market expectations, not hunt for "cheap"

---

### Layer 2 — Technical Analysis 技術面分析

**Trend — Clock Direction 時鐘方向**

| Direction | Sentiment | Action |
|-----------|-----------|--------|
| 2 o'clock ↗ | Bullish, sustainable | Ideal entry zone |
| 3 o'clock → | Sideways, hesitation | Wait |
| 4–6 o'clock ↘ | Bearish | Avoid |

**Position — Chip Peaks 籌碼峰**
- High-volume price clusters = market consensus = support/resistance
- Entry: pullback to chip peak during 2 o'clock uptrend

**Risk Management — 三有一執行**
1. Have expectations 有預期
2. Have a stop-loss 有底線
3. Have a plan 有計劃
4. Execute accordingly 依計行事

---

## Report Format

Reports use a bilingual Apple Badge Label style:

```
# AAPL — Apple Inc.
分析日期 Analysis Date：2026-02-23

BUSINESS  商業模式
[Business model table with moat checklist]

FINANCIAL HEALTH  財務健康
[4-column table: Metric | Value | Status | Explanation]
  Status: [PASS] [WATCH] [FAIL]

VALUATION  市場估值
[P/E · P/S · P/B with peer context]

TECHNICAL  技術面
[Trend · Alignment · Support levels with explanations]

VERDICT  操作結論
`AVOID` / `OBSERVE` / `WATCH` / `ENTRY`
[3–4 sentence reasoning + stop-loss reference]
```

---

## Supported Markets

- US stocks: NYSE, NASDAQ (e.g. AAPL, NVDA, GOOGL)
- Taiwan stocks: TWSE (e.g. 2330, 4958, 2454)

---

## License

MIT — see [LICENSE](LICENSE)
