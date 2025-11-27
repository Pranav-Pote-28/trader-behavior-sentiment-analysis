# trader-behavior-sentiment-analysis
# 🚀 Trader Behavior Insights — Bitcoin Sentiment vs Hyperliquid Trader Performance  


This project analyzes how **Bitcoin market sentiment** (Fear–Greed Index) impacts **trader performance** on the Hyperliquid exchange.  
It uses **211,000+ trades**, combined with daily sentiment data, and explores:

- Trader behavior across market sentiment regimes  
- PnL patterns, volatility, win rates  
- Statistical tests  
- Predictive modeling (Logistic Regression & Random Forest)  
- Feature importance explaining *what drives profitable trades*  

---

# 📂 **1. Project Structure**

```
├── trader-behavior-sentiment-analysis.ipynb   # Full analysis (EDA, ML, insights)
├── README.md         # This file
```

---

# 📊 **2. Summary of Steps**

1. **Data Loading & Cleaning**  
   - Standardized timestamps  
   - Created trade_date  
   - Cleaned sentiment labels  
   - Handled missing sentiment days

2. **Merging Datasets**  
   Merged Hyperliquid trades with Fear–Greed sentiment by calendar date.

3. **Feature Engineering**  
   - `notional` = execution price × token size  
   - `direction_num` = +1 (buy/long), –1 (sell/short)  
   - `pnl_positive` = profitable trade flag  
   - Encoded sentiment buckets  
   - Scaled FG numeric score

4. **Daily & Account-Level Aggregations**  
   - Win rate  
   - Total PnL  
   - Avg PnL  
   - Trades per day  
   - Sentiment per day  

5. **EDA Visualizations**  
   - Trade size vs sentiment  
   - PnL distribution  
   - Buy/Sell behavior  
   - Daily trend analysis  

6. **Statistical Analysis**  
   - Win rate & PnL across sentiment  
   - T-test (Greed vs Fear)  
   - Correlation analysis  

7. **Predictive Modeling**  
   - Logistic Regression  
   - Random Forest  
   - Feature Importance  

---

# 📈 **3. Key Insights**

## 🟦 Win Rate by Sentiment

| Sentiment        | Win Rate |
|------------------|----------|
| **Extreme Greed** | **49%** |
| **Greed**         | **44%** |
| **Fear**          | **41%** |
| **Neutral**       | **32%** |

> **Performance improves sharply during Greed and Extreme Greed.  
Neutral markets are the hardest to trade due to low volatility.**

---

## 🟥 Average PnL by Sentiment

| Sentiment        | Avg PnL |
|------------------|---------|
| **Greed**         | **87.89** |
| **Fear**          | **50.05** |
| **Extreme Greed** | **25.41** |
| Neutral           | 22.23 |

> **Greed yields the highest profits**.  
Fear yields high volatility — big wins and big losses.

---

## 🧪 Statistical Significance (Greed vs Fear)

- **T-statistic:** 5.80  
- **P-value:** 6.49e-09  

> The difference in PnL between Greed and Fear is **highly significant**.

---

## 📉 Correlation (Sentiment vs PnL)

```
corr = 0.011
```

> Sentiment affects environment (volatility), not individual trade-level outcomes.

---

# 🤖 **4. Machine Learning Results**

## **Logistic Regression**
- Accuracy: **89%**
- Recall (Profitable trades): **100%**
- Precision (Loss trades): **100%**

> Excellent linear separation.  
Highly reliable for risk filtering (flagging bad trades).

---

## **Random Forest**
- Accuracy: **86%**
- **ROC AUC: 0.94**

> Outstanding ranking ability for scoring profitable trades.  
> Useful for trade-selection models.

---

# 🔍 **5. Feature Importance (Random Forest)**

| Feature         | Importance |
|----------------|------------|
| **direction_num** | **0.638** |
| **notional**       | **0.329** |
| **fg_value**       | 0.019 |
| **sentiment_code** | 0.012 |

### Interpretation:
- **Direction** (buy vs sell) is the strongest predictor of PnL  
- **Trade size** heavily influences outcomes  
- **Sentiment adds contextual but limited predictive power**

---

# 🧠 **6. Final Conclusion**

Market sentiment significantly affects **trade behavior and profitability**:

- Traders win more during **Greed** & **Extreme Greed**  
- **Fear** introduces high volatility → large dispersion of outcomes  
- **Neutral** markets are the worst for profitability  
- **Direction & trade size** dominate PnL more than sentiment  
- Simple ML models can predict profits with **89% accuracy** and **0.94 AUC**

These insights can help design:

- sentiment-aware trading strategies  
- improved risk filters  
- volatility-adjusted position sizing  
- predictive models for trade selection  

---

# 🙌 Thank You  
For reviewing this submission.  
I look forward to the opportunity to discuss these insights further.

