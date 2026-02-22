---
name: stock-analysis
description: Use when the user asks to analyze a stock, evaluate whether a company is worth investing in, or requests stock selection guidance. Triggers on stock tickers, company names with investment/analysis intent, or phrases like '分析股票', '值不值得買', '幫我看'. Covers US and Taiwan stocks.
---

# Stock Analysis Framework

## Overview

A two-layer framework: **fundamentals determine strategy** (worth investing in?), **technicals determine tactics** (when and how to trade).

> "基本面不可以用來做交易。" — Fundamentals screen candidates. Technicals execute trades.

## Two Modes

- **Report mode**: User says "幫我分析 [股票]" → run full analysis, output structured report
- **Interactive mode**: User says "引導我分析 [股票]" → guide through each layer with questions, output report at end

---

## Step 1: Gather Data

When given only a ticker or name, use WebSearch to find:

| Data needed | Search query template |
|-------------|----------------------|
| Business description | `[ticker] business model what does it do` |
| Revenue + growth | `[ticker] annual revenue growth 2022 2023 2024` |
| EBIT / operating margin | `[ticker] EBIT margin operating profit margin` |
| Cash flow | `[ticker] operating cash flow free cash flow` |
| Valuation multiples | `[ticker] P/E P/S P/B valuation` |
| Price trend | `[ticker] stock price chart trend 2024 2025` |

---

## Layer 1: Fundamental Analysis

### 1A. Business Model Screen — Pass/Fail Gate

**Ask: Can you explain this business clearly in 5 minutes?**
→ If no: **STOP. Do not analyze further.** Incomprehensible businesses = unacceptable risk.

**Moat checklist** (score 0–4):
- [ ] Undifferentiated product — all users get the same product (e.g., Google Search)
- [ ] Widest possible user base — billions of users or most enterprises are potential customers
- [ ] Free pricing — no government/regulatory price caps
- [ ] Market monopoly — dominant position in its category

Score interpretation: 4/4 = exceptional, 3/4 = strong, 2/4 = decent, 1/4 or 0/4 = weak

### 1B. Financial Performance

| Metric | Standard | Red Flag |
|--------|----------|----------|
| Annual Revenue | ≥ $100M USD | < $100M = pre-scale, fragile |
| Revenue Growth | 15–20% ideal | < 10% = stalling; > 50% = may not sustain |
| EBIT Margin | Positive; compare within same industry only | Negative = structural loss, broken model |
| Operating Cash Flow | **Must be positive** | Negative = not actually earning money |
| Free Cash Flow | Ideally positive | Negative = limited strategic flexibility |

**Industry comparison rule:** EBIT margin is only meaningful within the same sector. Google's 32% vs Walmart's 4% are incomparable — different models. But Walmart 4% vs Costco 3.7% is a valid comparison.

**Free cash flow** = operating cash flow minus capex. This is the real money the business generates — used for expansion, R&D, acquisitions, dividends, or buybacks. Prioritize companies with strong FCF.

**Story-only stock warning:** If EBIT is negative AND debt > revenue AND no FCF → no matter how compelling the narrative, avoid. The story must eventually show up in the numbers.

### 1C. Market Valuation

- Compare P/S, P/E, P/B to sector peers
- Higher valuation = market has high expectations (not necessarily wrong)
- Lower valuation = market is skeptical (not necessarily cheap)
- Goal: understand what the market expects, not to find "cheap" stocks

**Fundamental conclusion logic:**
```
All metrics pass? → Proceed to Layer 2
Any red flag? → Note concern, weigh severity
Multiple red flags? → Recommend avoid
```

---

## Layer 2: Technical Analysis

### 2A. Trend — Clock Direction (時鐘方向)

Visualize the price trend angle as a clock hand:

| Clock direction | Market sentiment | Action |
|----------------|-----------------|--------|
| 1–2 o'clock ↗️ (steep) | Strongly bullish, high momentum | Can enter; watch for overextension |
| **2 o'clock ↗ (moderate)** | **Bullish, sustainable — TARGET** | **Ideal entry zone** |
| 3 o'clock → (flat) | Sideways, hesitation, no consensus | Wait |
| 4 o'clock ↘ | Bearish, market unconvinced | Avoid |
| 5–6 o'clock ↙⬇️ | Strongly bearish, high fear | Avoid entirely |

**Key rule:** Price trend and fundamentals must move in the SAME direction. If fundamentals are strong but price is in 4–6 o'clock direction → **do not buy.** The chart contains information you don't have yet. Respect it.

**Best setup:** 2 o'clock price trend + improving fundamentals = market consensus + mutual confirmation = easiest trades.

### 2B. Position — Chip Distribution (籌碼分佈)

**Chip peaks (籌碼峰):** Price levels with large historical volume concentration = where many investors bought = market consensus price.

- Larger chip peak = stronger consensus = stronger support or resistance
- In an uptrend: price pulls back to chip peak → **support zone → potential buy point**
- In a downtrend: price bounces to chip peak → **resistance zone → potential sell point**

**Entry rule:** Wait for price to pull back to an important chip peak during a 2 o'clock uptrend.

### 2C. Risk Management — Three Haves + One Execution (三有一執行)

Every trade must have:
1. **Expectations (預期)** — why you're entering, what you expect to happen
2. **Bottom line (底線)** — your stop-loss price, defined BEFORE entering. Chip peak support is a natural reference.
3. **Plan (計劃)** — written entry and exit criteria
4. **Execute accordingly (依計行事)** — when price breaks your bottom line, EXIT. No exceptions.

**The cardinal error:** Holding through your stop-loss because "the market is wrong, my fundamentals are right." Charts incorporate information you don't have access to. When chart contradicts thesis → respect the chart, exit, reassess.

---

## Combined Decision Logic

```
Can explain the business in 5 min?
  NO → Stop. Don't invest.
  YES ↓

Financial health:
  EBIT negative? → Avoid (broken model)
  Revenue < $100M? → Avoid (pre-scale)
  Operating cash flow negative? → Avoid
  All clear ↓

Valuation vs. peers: note high/medium/low expectation

Trend direction?
  4–6 o'clock → Observe. Do not buy. Wait for reversal.
  3 o'clock → Wait. Revisit when trend forms.
  2 o'clock ↓

Price near chip peak support on pullback?
  YES → Consider entry. Set stop below chip peak.
  NO → Wait for next pullback to chip peak.
```

---

## Output Format

Use this structure for the final report (both modes). Follow the Apple Badge Label style exactly — no emojis, clean labels, structured layout.

```
# [TICKER] — [Company Name]
*[YYYY-MM-DD]*

---

**BUSINESS**
[One sentence: what it does, who it serves (2B/2C)]
Moat Score: [X] / 4 — [Strong / Decent / Weak]

---

**FINANCIAL HEALTH**

| Metric         | Value            | Status   |
|----------------|------------------|----------|
| Revenue        | [amount]         | [PASS] / [WATCH] / [FAIL] |
| Revenue Growth | [%] YoY          | [PASS] / [WATCH] / [FAIL] |
| EBIT Margin    | [%]              | [PASS] / [WATCH] / [FAIL] |
| Operating CF   | Positive/Negative| [PASS] / [WATCH] / [FAIL] |
| Free CF        | [amount]         | [PASS] / [WATCH] / [FAIL] |

**VALUATION**
P/E [x]x  ·  P/S [x]x  ·  P/B [x]x
Market expectation: [Premium / Fair / Discounted] — [vs. peer context]

---

**TECHNICAL**

| | |
|--|--|
| Trend | [X o'clock] — [description] |
| Alignment | [Aligned / Diverging] — [brief reason] |
| Key Support | [price range]  ·  [price range] |

---

**VERDICT**

`[AVOID / OBSERVE / WATCH / ENTRY]`

[2–3 sentences of reasoning.]
Stop-loss: [chip peak support level or key price]
```

**Status badge rules:**
- `[PASS]` — metric meets standard
- `[WATCH]` — below ideal but not disqualifying
- `[FAIL]` — red flag, disqualifying condition

**Verdict badge rules:**
- `AVOID` — fundamental red flags, do not invest
- `OBSERVE` — fundamentals OK but technicals not ready
- `WATCH` — technicals forming, monitor for entry setup
- `ENTRY` — fundamentals pass + 2 o'clock trend + at chip peak support

---

## Step 3: Save Report

After generating the analysis report, **always save it to a file automatically** — do not ask the user for confirmation.

**Default save path:** `./reports/TICKER-YYYY-MM-DD.md` (relative to current working directory)

**Path override:** If the user specifies a path in the command, use that instead.
- "幫我分析 NVDA" → `./reports/NVDA-2026-02-23.md`
- "幫我分析 NVDA，存到 ~/Desktop" → `~/Desktop/NVDA-2026-02-23.md`
- "幫我分析 NVDA，存到 D:/stocks" → `D:/stocks/NVDA-2026-02-23.md`

**Steps:**
1. Create `./reports/` directory if it doesn't exist (`mkdir -p ./reports`)
2. Write the full report content to the file using the Write tool
3. Tell the user: "報告已存到 `[path]`"

**Report file content** = the full Output Format report starting from `# [TICKER] — [Company Name]`.

---

## Common Mistakes

| Mistake | Correction |
|---------|-----------|
| Buying a great business with 5–6 o'clock trend | Wait for trend reversal first |
| Comparing EBIT margins across industries | Only compare within same sector |
| Ignoring story stocks with negative EBIT | Financials must confirm the story |
| Holding through stop-loss "because fundamentals are good" | Charts know things you don't — respect the stop |
| Chasing price above chip peaks | Wait for pullback to chip peak support |
| Entering without a defined stop-loss | Always set bottom line before entering |
