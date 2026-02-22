# Stock Analysis Plugin

A Claude Code skill for analyzing stocks using a two-layer framework:
- **Layer 1 — Fundamental Analysis**: Business model → Financial performance → Market valuation
- **Layer 2 — Technical Analysis**: Trend (clock direction) → Position (chip peaks) → Risk management

Covers US stocks (NYSE/NASDAQ) and Taiwan stocks (TWSE).

## Installation

In Claude Code, run:

```
/plugin install stock-analysis-plugin@YOUR_GITHUB_USERNAME/stock-analysis-plugin
```

## Usage

**Report mode** (auto-generate full analysis):
```
幫我分析 NVDA
幫我分析 2330
```

**Interactive mode** (guided Q&A):
```
引導我分析 AAPL
```

## Framework

Based on a stock education framework covering:

### Fundamental Screen
| Metric | Standard |
|--------|----------|
| Annual Revenue | ≥ $100M USD |
| Revenue Growth | 15–20% ideal |
| EBIT Margin | Positive required |
| Operating Cash Flow | Must be positive |
| Free Cash Flow | Ideally positive |

### Technical Screen
- **Trend**: Clock direction (2 o'clock = ideal uptrend)
- **Position**: Chip peaks (籌碼峰) as support/resistance
- **Risk**: Three Haves + One Execution (三有一執行)

## License

MIT
