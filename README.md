# Bank Marketing Campaign Analysis

Exploratory Data Analysis (EDA) project for the **Statistical Learning and Data
Analysis** course — Assignment 1.

## Goal

Perform a complete EDA on the [Bank Marketing dataset](data/bank.csv), a
record of 45,211 direct-marketing phone contacts made by a Portuguese bank to
sell a term-deposit product, covering:

1. Data loading & cleaning
2. Univariate data description
3. Bivariate and multivariate description
4. Principal Component Analysis and clustering
5. Summary and interpretation

## Repository structure

```
.
├── data/
│   └── bank.csv                                  # raw dataset (";"-delimited)
├── notebooks/
│   └── BankMarketingCampaignAnalysis.ipynb        # full analysis, code + plots + commentary
├── reports/
│   └── BankMarketingCampaignAnalysis.html         # static HTML export of the notebook
└── presentation/
    └── BankMarketingCampaignAnalysis_Presentation.pptx  # short exam-dissertation deck
```

## Key findings

- **Prior contact history is the strongest signal in the data.** Customers
  with a successful previous campaign (`poutcome = success`) subscribe at
  64.7%, versus 9.2% for customers never previously contacted.
- **Campaign timing was misaligned with receptiveness.** May, the busiest
  contact month, had the lowest subscription rate (6.7%); March, September,
  October and December — far less used — converted at over 40%.
- **Call `duration` correlates strongly with subscription but cannot be used
  predictively**, since its value is only known after the call takes place
  (data leakage).
- **PCA** needs 26 of 42 encoded components to reach 80% of variance; the
  first two components represent a *contact-history* axis and a
  *socio-professional/seasonal* axis respectively.
- **K-Means (k=2)** clustering on the PCA-reduced features rediscovers the
  contact-history split in a fully unsupervised way: a "never contacted"
  segment (82% of customers, 9.2% subscription) and a "previously contacted"
  segment (18%, 23.1% subscription).
- The target is strongly **imbalanced** (88.3% "no" vs. 11.7% "yes"), an
  important consideration for any future predictive model.

## Running the notebook

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn jupyter
jupyter notebook notebooks/BankMarketingCampaignAnalysis.ipynb
```

The notebook expects `bank.csv` in its own working directory — copy it from
`data/` alongside the notebook, or adjust the read path.

## Dataset source

UCI Machine Learning Repository — [Bank Marketing Data
Set](https://archive.ics.uci.edu/dataset/222/bank+marketing) (Moro, S.,
Cortez, P., and Rita, P., 2014).
