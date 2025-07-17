# 📊 Analysis of Aave V2 Wallet Credit Scoring

## 1️⃣ Overview

We scored **3497 wallets** using:
- **Rule-Based Scoring (0–1000)** using domain-driven weighted heuristics.
- **ML-Based Scoring (0–1000)** using KMeans clustering over engineered wallet features.

This analysis provides:
✅ Score distribution across bands  
✅ Behavioral insights on wallets in **lower vs. higher ranges**  
✅ Graphical interpretation for reporting and stakeholder discussions.

---

## 2️⃣ Score Distribution

### 📈 Rule-Based Score Distribution

- Majority of wallets score between **170–200**.
- Extremely few wallets exceed **250**, reflecting low transaction and engagement activity.

| Band         | Wallet Count |
|--------------|--------------|
| 0–100        | Few (bot/failed wallets) |
| 100–200      | Majority |
| 200–300      | Minority |
| 300–500      | Very few |
| 500–1000     | Rare, high engagement wallets |

---

### 📈 ML-Based Score Distribution

- Using **KMeans**, scores were clustered and mapped:
    - 200: Low activity/risky wallets
    - 400: Below average
    - 600: Moderate
    - 800: High activity
    - 1000: Very high activity

| Band         | Wallet Count |
|--------------|--------------|
| 200          | ~2300 wallets |
| 400          | ~500 wallets |
| 600          | ~400 wallets |
| 800          | ~200 wallets |
| 1000         | <10 wallets |

---

## 3️⃣ Behavioral Insights

### 🩺 Wallets in **Lower Score Bands (0–200):**
- **Characteristics:**
    - 1–2 transactions only
    - Only deposits with negligible amounts
    - No borrowing or repayment
    - Low active days (often a single day)
- **Interpretation:**
    - Likely bots, airdrop hunters, or abandoned wallets.
    - No meaningful DeFi credit activity.

---

### 🩺 Wallets in **Higher Score Bands (600–1000):**
- **Characteristics:**
    - Frequent deposits and borrows
    - Consistent repayments
    - Low liquidation rates
    - Higher borrow/deposit ratios
    - Active over extended periods (weeks to months)
- **Interpretation:**
    - Indicates **genuine DeFi users actively participating** in lending/borrowing.
    - **Lower credit risk** and potentially eligible for advanced lending protocols.

---

## 4️⃣ Visualizations

### 📊 Attached Plots

- **Rule-Based Score Histogram:** Shows dense clustering near 170–200.
- **ML Score Histogram:** Shows clear cluster band segmentation.

These visuals help stakeholders quickly understand the distribution of wallet activities and creditworthiness.

---

## 5️⃣ Recommendations

✅ Use these scores to filter wallets for:
- **Targeting reliable borrowers** in DeFi protocols.
- Flagging low-score wallets for deeper risk checks.
- Future model training using repayment and liquidation labels.

✅ Extend to **live wallet scoring** using the same pipeline for new transactions.

✅ Integrate anomaly detection or supervised models as the next enhancement step for refined credit risk management.

---


