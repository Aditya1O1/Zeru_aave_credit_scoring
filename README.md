# Zeru_aave_credit_scoring

# 🪙 Aave V2 Wallet Credit Scoring

## 🚩 Problem Statement

Build a **robust machine learning model** that assigns a **credit score (0–1000)** to wallets on **Aave V2** using **historical transaction behavior**:
- Higher scores indicate **reliable, responsible DeFi usage**.
- Lower scores reflect **risky, bot-like, or exploitative behavior**.

---

## 📂 Data

- Provided: **100K transaction-level JSON data** (Deposit, Borrow, Repay, RedeemUnderlying, LiquidationCall).
- Loaded and preprocessed into a Pandas DataFrame (35 columns).

---

## 🛠️ Methodology

### 1️⃣ **Feature Engineering**
For each `userWallet`, we computed:
- **Action Counts:** deposits, borrows, repays, redeems, liquidations.
- **Total USD Amounts:** total deposit, borrow, repay, redeem, liquidation.
- **Ratios:**
    - `repay_borrow_ratio = total_repay_usd / (total_borrow_usd + 1)`
    - `liquidation_rate = total_liquidation_usd / (total_borrow_usd + 1)`
    - `borrow_deposit_ratio = total_borrow_usd / (total_deposit_usd + 1)`
- **Active Days:** Number of unique days with transactions.

Normalized using **MinMaxScaler** for consistent clustering.

---

### 2️⃣ **Rule-Based Scoring**
Using engineered features, we designed a **weighted rule-based formula**:
- + Deposits, Borrows, Repays
- - Liquidation Rate
- + Repay/Borrow Ratio
- + Borrow/Deposit Ratio
- + Active Days

Scaled to **0–1000** for interpretability.

---

### 3️⃣ **Machine Learning: KMeans Clustering**
- Applied **KMeans (n_clusters=5)** on scaled features.
- Mapped clusters to score bands:
    - **200:** Low activity/risky
    - **400:** Below average
    - **600:** Moderate activity
    - **800:** High activity
    - **1000:** Very high activity

The final `ml_score` complements the rule-based score while capturing cluster-based patterns for better wallet segmentation.

---

## 🖥️ Processing Flow

1. **Data Loading:** Read JSON data, normalize structures.
2. **Feature Engineering:** Calculate wallet-level aggregates and ratios.
3. **Rule-Based Scoring:** Compute a transparent credit score per wallet.
4. **KMeans Clustering:** Assign ML-based credit scores.
5. **Visualization:** Generate score distribution plots.
6. **Export Results:** Save `wallet_features.csv` for operational use.

---

## 📊 Deliverables

- `aave_credit_scoring_colab.ipynb`: Clean, documented Colab notebook with full pipeline.
- `wallet_features.csv`: Wallet-wise scores (`rule_based_score`, `ml_score`).
- `README.md`: Full method, architecture, and processing details.
- `analysis.md`: Deep analysis on scored wallets with insights and plots.

---

## 🚀 Usage Instructions

1️⃣ Clone the repo and open the notebook in **Google Colab**.  
2️⃣ Upload the provided JSON file.  
3️⃣ Run all cells to:
- Generate wallet scores.
- Visualize distributions.
- Export results for your analysis or integration.

---

## 🩺 Future Improvements

✅ Add anomaly detection for suspicious wallet patterns.  
✅ Use supervised ML if labeled default/liquidation outcomes are provided.  
✅ Build dashboards for live wallet monitoring.

---




