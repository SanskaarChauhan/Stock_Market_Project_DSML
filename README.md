# Indian Stock Market Analysis and Prediction

A Jupyter Notebook-based project for analyzing historical and live data of top Indian stocks (NSE-listed) using Python. It fetches data via yfinance, performs exploratory data analysis (EDA), visualizations, and builds machine learning models for stock price prediction (regression) and buy/sell signal classification. Built with pandas, scikit-learn, matplotlib, and seaborn for a complete end-to-end workflow.

This project is ideal for learning financial data analysis, time-series forecasting, and ML on real-world stock data. No API keys required—yfinance uses Yahoo Finance's public API (free, but subject to rate limits).

## Features
- **Data Fetching**: Downloads 3 years of historical OHLCV (Open, High, Low, Close, Volume) data for 15 major NSE stocks (e.g., RELIANCE.NS, TCS.NS).
- **Live Updates**: Appends the latest trading day's data to keep datasets current.
- **EDA and Visualization**: Correlation heatmaps, price plots, return distributions using seaborn and matplotlib.
- **ML Models**:
  - Regression: Linear Regression and Random Forest for predicting closing prices.
  - Classification: Logistic Regression for buy/sell signals based on features like moving averages and volatility.
- **Evaluation**: Metrics like MSE, R² for regression; accuracy and classification reports for models.
- **Modular Code**: Easy to extend with more tickers, features, or models (e.g., LSTM for time-series).

## Project Structure
```
your-project-folder/
├── README.md                 # This file
├── requirements.txt          # Python dependencies
├── stock_analysis.ipynb      # Main Jupyter notebook (imports, data fetch, EDA, models)
├── data/                     # (Optional) Sample or saved CSVs (gitignore large files)
│   ├── historical_data.csv   # Example output
│   └── updated_data/         # Per-ticker CSVs
├── .gitignore                # Ignores .env, caches, large data files
└── .env                      # (Local only) For any future API keys (gitignore'd)
```

## Requirements
- Python 3.8+ (tested on 3.10).
- Jupyter Notebook/Lab for running the notebook.
- Key libraries: pandas, numpy, yfinance, scikit-learn, matplotlib, seaborn, sqlalchemy (for potential DB integration).

Install via pip:
```bash
pip install -r requirements.txt
```

Contents of `requirements.txt` (generated via `pip freeze > requirements.txt`):
```
pandas>=1.5.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.12.0
yfinance>=0.2.0
scikit-learn>=1.3.0
sqlalchemy>=2.0.0
python-dateutil>=2.8.0  # For precise date handling
```

**Note**: No API keys needed for core functionality. If extending to paid APIs (e.g., Alpha Vantage), follow the security setup in the notebook comments.

## Setup and Usage
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter**:
   ```bash
   jupyter notebook  # Or jupyter lab for a better interface
   ```
   - Open `stock_analysis.ipynb`.

4. **Run the Notebook**:
   - **Step 1: Imports and Setup** – Loads libraries and defines tickers/date range (3 years back from today).
   - **Step 2: Fetch Historical Data** – Downloads data for all tickers into a dictionary of DataFrames.
   - **Step 3: Live Update** – Appends latest prices (run this periodically for freshness).
   - **Step 4: EDA** – Visualize prices, returns, correlations (e.g., heatmap of stock interdependencies).
   - **Step 5: Feature Engineering** – Compute moving averages, volatility, etc.
   - **Step 6: Modeling** – Train/test split, scale data, fit models, evaluate performance.
   - **Step 7: Predictions** – Generate forecasts or signals for new data.

   Example output from data fetch:
   ```
   Date range: 2022 to 2025
   Downloaded data shape: (750, 15)
   ```

   For live updates:
   ```
   ✓ Updated RELIANCE.NS with data for 2025-9-25
   Live price update completed
   ```

5. **Customization**:
   - Add more tickers: Edit the `indian_tickers` list.
   - Extend date range: Modify `timedelta(days=3*365)`.
   - Save data: Use `df.to_csv()` (but exclude large files from Git via `.gitignore`).
   - For database storage: Uncomment sqlalchemy sections to save to SQLite/PostgreSQL.

6. **Running Without Internet**:
   - Use saved CSVs in `data/` for offline EDA/models.
   - Regenerate data only when needed (yfinance handles caching somewhat).

## Example Outputs
- **Price Plot**: Line chart of closing prices for all stocks over 3 years.
- **Correlation Heatmap**: Shows relationships (e.g., banking stocks like HDFCBANK.NS and ICICIBANK.NS correlate highly).
- **Model Performance** (hypothetical):
  - Regression R²: 0.85 (Random Forest on RELIANCE.NS).
  - Classification Accuracy: 72% for buy/sell signals.

## Limitations and Notes
- **Data Source**: Relies on yfinance (Yahoo Finance)—accurate but can have gaps/delays for NSE stocks. Not financial advice; for educational use only.
- **Rate Limits**: Avoid rapid re-runs; the code includes sleeps. If blocked, wait 5-10 mins.
- **ML Caveats**: Stock prediction is challenging (markets are noisy). Models use basic features—enhance with technical indicators (e.g., RSI via TA-Lib: `pip install ta-lib`).
- **Security**: No hardcoded secrets. If adding APIs, use `.env` files and environment variables (see notebook comments).
- **Performance**: For 15 tickers, data fetch takes ~30-60 seconds. Scale carefully for more.
- **Legal**: Respect Yahoo's terms; don't scrape excessively.

## Contributing
- Fork the repo, create a branch, add features (e.g., more models like XGBoost), and submit a PR.
- Issues? Open a ticket for bugs (e.g., ticker failures) or suggestions (e.g., portfolio optimization).
- Tests: Run the notebook end-to-end; add unit tests with pytest if expanding.

## License
MIT License – Feel free to use, modify, and distribute. See [LICENSE](LICENSE) file for details (create one if missing).

## Acknowledgments
- Built with open-source tools: yfinance for data, scikit-learn for ML.
- Inspired by quantitative finance tutorials on Towards Data Science.

---

*Last Updated: September 2025*  
For questions, contact [sanskaar.17chauhan@gmail.com] or open an issue on GitHub. Happy analyzing! 📈
