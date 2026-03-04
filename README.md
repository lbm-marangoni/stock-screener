# 🔷 Stock Screener
> Filter stocks based on key fundamental metrics to identify investment opportunities

A Python-based stock screener that pulls real-time fundamental data for a list of tickers and filters them against customizable criteria — automating the first layer of any equity research process.

---

## 📌 What It Does

1. **Data Extraction** — Fetches key fundamental metrics for any list of tickers via `yfinance`: P/E, Forward P/E, PEG Ratio, ROE, Dividend Yield, Debt/Equity, 52-week range
2. **Screening** — Applies user-defined filters to identify stocks that meet specific investment criteria
3. **Output** — Returns a clean, ranked DataFrame with only the stocks that pass the screen

---

## 💡 Why I Built This

Manually checking fundamentals stock by stock is slow and inconsistent. This screener automates the filtering layer — letting you scan a broad universe of stocks and surface only the ones worth researching further. It's the starting point before any deep-dive valuation.

---

## ⚙️ How It Works

```python
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'META', 'TSLA', 'NVDA', 'JPM', 'V', 'WMT']

# Screen each stock and collect metrics
results = [screen_stock(ticker) for ticker in tickers]
df = pd.DataFrame(results)

# Apply criteria: P/E < 30, Dividend Yield > 1%, ROE > 15%
screened = df[
    (df['P/E Ratio'] < 30) &
    (df['P/E Ratio'] > 0) &
    (df['Dividend Yield'] > 1) &
    (df['ROE'] > 15)
]
```

Criteria are fully customizable — adjust the thresholds to match any investment strategy.

---

## 📊 Metrics Extracted

| Metric | Description |
|---|---|
| P/E Ratio | Trailing price-to-earnings |
| Forward P/E | Forward-looking P/E estimate |
| PEG Ratio | P/E adjusted for growth |
| Dividend Yield | Annual dividend as % of price |
| ROE | Return on equity (%) |
| Debt/Equity | Leverage indicator |
| 52W High/Low | Price range over last 52 weeks |

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![yFinance](https://img.shields.io/badge/yFinance-6C63FF?style=for-the-badge&logo=yahoo&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📁 Project Structure

```
📁 stock-screener
├── README.md
├── requirements.txt
└── screener.ipynb      ← main notebook
```

---

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/lbm-marangoni/stock-screener
cd stock-screener
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Run the notebook `screener.ipynb` and edit the `tickers` list and screening criteria as needed

---


*Built by [Lucas Marangoni](https://www.linkedin.com/in/lbm-marangoni) — Economics student at FAAP | Quant Finance & Portfolio Management*

