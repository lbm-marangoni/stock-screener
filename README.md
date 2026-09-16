# Equity Screening Utility

A lightweight Python tool for filtering a universe of stocks using selected valuation, profitability and leverage metrics as an initial step in the equity research process.

The project is intentionally simple: its purpose is not to produce an investment recommendation, but to reduce a broad list of companies into a smaller set that may deserve deeper fundamental research.

---

## Why I Built It

Equity research often begins with a large universe of companies.

Reviewing every company manually is inefficient, so this project was built to automate the first screening layer and help answer a narrower question:

> Which companies meet a selected set of financial criteria and may be worth researching further?

The screener is therefore used as a **research filter**, not as a substitute for fundamental analysis, valuation or investment judgment.

---

## Research Workflow

```text
Stock Universe
     ↓
Financial Data
     ↓
Initial Screening
     ↓
Shortlist
     ↓
Fundamental Research
     ↓
Valuation
     ↓
Investment Thesis
```

The project operates only in the first stages of this process.

A company passing the screen should not be interpreted as an investment opportunity by itself.

---

## Metrics

The current version retrieves selected metrics through `yfinance`, including:

| Metric | Purpose |
|---|---|
| P/E | Basic valuation reference |
| Forward P/E | Forward-looking valuation reference |
| PEG Ratio | Valuation relative to expected growth |
| ROE | Profitability |
| Dividend Yield | Shareholder distribution reference |
| Debt / Equity | Leverage |
| Market Capitalization | Company size |
| 52-Week High / Low | Price context |

The criteria can be changed according to the research objective.

---

## Example

```python
tickers = [
    "AAPL",
    "MSFT",
    "GOOGL",
    "AMZN",
    "META",
    "TSLA",
    "NVDA",
    "JPM",
    "V",
    "WMT"
]

results = [screen_stock(ticker) for ticker in tickers]
df = pd.DataFrame(results)

screened = df[
    (df["P/E Ratio"] < 30) &
    (df["P/E Ratio"] > 0) &
    (df["Dividend Yield"] > 1) &
    (df["ROE"] > 15)
]
```

The thresholds above are only an example.

Different sectors, market environments and investment strategies require different screening criteria.

---

## What the Project Does

The workflow consists of three main steps:

**1. Data collection**

Retrieves selected fundamental and market metrics for each ticker.

**2. Screening**

Applies user-defined conditions to the dataset.

**3. Shortlisting**

Returns the companies that meet the selected criteria for further research.

---

## Technology

- Python
- Pandas
- yFinance
- Jupyter Notebook

Technology is used here as a simple research tool rather than as the investment thesis itself.

---

## Project Structure

```text
stock-screener/
├── README.md
├── requirements.txt
└── Stock Screener.ipynb
```

---

## Running the Project

Clone the repository:

```bash
git clone https://github.com/lbm-marangoni/stock-screener
cd stock-screener
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Then run:

```text
Stock Screener.ipynb
```

Edit the ticker universe and screening criteria according to the research objective.

---

## Limitations

This project is intentionally a first-stage screening utility.

Its current limitations include:

- dependence on third-party data from `yfinance`
- limited accounting normalization
- no sector-specific screening logic
- no historical fundamental database
- no valuation model
- no qualitative company analysis
- no investment recommendation

These limitations are important because financial ratios should be interpreted in context rather than used mechanically.

---

## Role in My Investment Process

This project represents the **idea-generation / filtering layer** of a broader investment research process.

It complements deeper work focused on:

- financial statement analysis
- business and industry analysis
- valuation
- investment thesis development
- portfolio context
- monitoring and review

For a broader example of how I structure those different stages, see:

**[SBWAA — Investment Research & Portfolio Decision-Support System](https://github.com/lbm-marangoni/sbwaa)**

---

## Author

**Lucas Marangoni**

Economics @ FAAP  
Performance & Insights @ Bradesco  
Research @ FAAP Finance

Asset Management • Equity Research • Investment Analysis

[LinkedIn](https://www.linkedin.com/in/lbm-marangoni)

---

## Disclaimer

This repository is an educational and research project.

The outputs of the screener should not be interpreted as investment recommendations or financial advice.
