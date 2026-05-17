
---

## D. Dataset-Specific Instance

### Instance: Dutch Retail Sales Index
**Date applied:** 2026-05-17
**Stakeholder:** Dutch Retail Category Manager – responsible for long-term trend planning and seasonal inventory strategy at a national retail chain.

---

#### A – Snapshot (filled)

- **Source:** Dutch Retail Sales Index – public time-series dataset (CBS / public statistics)
- **Shape:** 425 rows × 5 columns (after date parsing: time_decimal, sales_index, year, month, date)
- **Raw columns:** unnamed index, time_decimal (float), sales_index (int)
- **Date range:** May 1960 → September 1995
- **Missing values:** 0 across all columns
- **Duplicate rows:** 0
- **Sales index range:** min 12, max 131, mean ~63
- **Quality issues detected:**
  - Time stored as decimal year (e.g. 1960.333 = April 1960) — not a standard datetime format
  - Required manual conversion: year extracted via int(), month via ((decimal - year) * 12).round() + 1
  - Month values clipped to range 1–12 as a safety check
  - ⚠ This is a human intervention point — Claude Code did not handle this automatically

---

#### B – Questions (filled)

1. What is the long-term growth trend of the Dutch retail sales index, and are there identifiable growth phases?
2. What is the typical seasonal pattern within a year — which months consistently peak and whi
cat >> /Users/rebekaolar/ai-eda-playbook/PLAYBOOK.md << 'ENDOFFILE'

---

## D. Dataset-Specific Instance

### Instance: Dutch Retail Sales Index
**Date applied:** 2026-05-17
**Stakeholder:** Dutch Retail Category Manager – responsible for long-term trend planning and seasonal inventory strategy at a national retail chain.

---

#### A – Snapshot (filled)

- **Source:** Dutch Retail Sales Index – public time-series dataset (CBS / public statistics)
- **Shape:** 425 rows × 5 columns (after date parsing: time_decimal, sales_index, year, month, date)
- **Raw columns:** unnamed index, time_decimal (float), sales_index (int)
- **Date range:** May 1960 → September 1995
- **Missing values:** 0 across all columns
- **Duplicate rows:** 0
- **Sales index range:** min 12, max 131, mean ~63
- **Quality issues detected:**
  - Time stored as decimal year (e.g. 1960.333 = April 1960) — not a standard datetime format
  - Required manual conversion: year extracted via int(), month via ((decimal - year) * 12).round() + 1
  - Month values clipped to range 1–12 as a safety check
  - ⚠ This is a human intervention point — Claude Code did not handle this automatically

---

#### B – Questions (filled)

1. What is the long-term growth trend of the Dutch retail sales index, and are there identifiable growth phases?
2. What is the typical seasonal pattern within a year — which months consistently peak and which dip?
3. Which decade showed the strongest average index growth, and which was weakest?
4. Are there years with anomalously low or high annual average index values compared to the long-term trend?
5. What is the year-on-year % change pattern, and has volatility increased or decreased over time?

---

#### C – Answers (filled)

**Q1 – Long-term trend:**
The index grew strongly from 1960 to ~1980 (index rose from ~14 to ~86), followed by a plateau through the 1980s, then modest renewed growth into the 1990s. No 2008 crisis is visible — dataset ends in 1995. Chart: data/q1_trend.png.

**Q2 – Seasonal pattern:**
December is consistently the peak month (holiday spending). February is the annual trough. This pattern is stable across all decades in the dataset — reliable for inventory planning.

**Q3 – Decade growth:**
- 1960s avg: ~21.8 (baseline)
- 1970s avg: ~57.0 → **+161.7% strongest decade**
- 1980s avg: ~85.6 → +50.2%
- 1990s avg: ~106.1 → +24.0% **weakest growth rate**

**Q4 – Anomalous years:**
No years exceeded z-score > 2 when measured against the full-series mean. Caveat: z-score on a non-stationary trending series is misleading — early years appear "low" simply due to the upward trend, not because they are anomalies. Detrending would be needed for rigorous outlier detection.

**Q5 – YoY volatility:**
Growth was most volatile in the 1960s–70s (rapid expansion phase). Volatility stabilised after ~1983. The 10-year rolling standard deviation of YoY % change shows a clear downward trend from ~15% in the 1970s to ~5% by the 1990s. Chart: data/q5_yoy.png.

