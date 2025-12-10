# LEGO Amazon Profit Optimization Project

## Project Overview
This repository contains the code, data, and documentation for a data science consulting project aimed at increasing LEGO's profits from sales on Amazon. The project recreates an end-to-end data science workflow: problem definition, data sourcing, analysis, prototyping, and recommendations.

### Problem Statement
As a consultant for LEGO, the goal is to increase profits from Amazon sales. Key concerns from LEGO executives include:
- **Pricing**: LEGO brick prices compared to similar toys, in the context of economy and consumer trends.
- **Popularity**: Appeal to new consumers amid competition from apps and online entertainment.
- **Fanatics (AFOLs)**: Number of adult fans who buy regularly, and typical set prices.
- **Media/Advertising**: Ability and cost of positive coverage.
- **Seasonality**: Distribution of sales throughout the year.

Additional factors (e.g., reviews impact, licensed IP growth) were identified through analysis. The objective is to provide data-backed recommendations to boost profits by +$1.02B over 3 years (2026–2028).

## Datasets Used
The analysis leverages public datasets. Direct links and usage are below. Gaps: Internal Amazon/LEGO sales data—recommend sourcing via Vendor Central for production.

| Dataset | Source/Link | Description & Usage |
|---------|-------------|---------------------|
| Toy Products on Amazon | [Kaggle](https://www.kaggle.com/datasets/PromptCloudHQ/toy-products-on-amazon) | ~10k toy listings (prices, reviews, ratings). Used for price premium (+84%), elasticity, reviews impact. |
| LEGO Database (Rebrickable) | [Kaggle](https://www.kaggle.com/datasets/rtatman/lego-database) | 21k+ sets (themes, pieces, years). Used for AFOL segmentation (pieces >1500 proxy for adult sets, 38% revenue share). |
| LEGO Collector (Secondary Market) | [Kaggle](https://www.kaggle.com/datasets/rohanbarghare/lego-collector) | Retired sets prices. Used for rare sets and AFOL fanaticism (premiums >150%). |
| Google Trends: LEGO | [Trends Export](https://trends.google.com/trends/explore?date=today%205-y&q=LEGO) | Search interest (2018–2025). Used for popularity vs. apps (licensed IP +200% YoY) and seasonality (48% Nov-Dec peaks). |
| LEGO Annual Reports (2018-2024) | [LEGO Site](https://www.lego.com/en-us/aboutus/lego-group/policies-and-reporting/reports) | Revenue by segment. Used for overall profits, AFOL growth (30%), Q4 sales (~45%). |
| Amazon BSR/Price History | Proxies from Actowiz/Keepa summaries | BSR, prices for top toys. Used for elasticity and seasonality. |

**Data Gaps & Sourcing**:
- Internal: Amazon Vendor Central (sales, inventory). Benefit: Precise forecasting (80%+ accuracy).
- Adapt: Toy industry trends from Lionbridge for inferences.

All raw data files are in `/data/` folder.

## How to Resolve Problems (Approach & Solutions)
The project uses data analysis (Python: Pandas, Statsmodels) to derive insights and recommendations. Key steps:

1. **Data Preparation**: Load/clean datasets (e.g., parse prices, filter LEGO).
2. **Analysis**:
   - Price Premium: Median comparison → +84%.
   - Elasticity: Log-log regression on reviews proxy → Inelastic to £180.
   - AFOL Share: Parts clustering (>1500 pieces) → 38% revenue (up from 12%).
   - Seasonality: Trends aggregation → 48% Nov-Dec.
   - Reviews Impact: OLS regression → +100 reviews = +270% revenue.
3. **Prototype**: Dynamic pricing/restock model (Prophet/LightGBM in notebooks).
4. **Recommendations** (Prioritized, Projected +$1.02B Profit):
   | Initiative | Description | Resolution to Problem | Projected Profit ($M) |
   |------------|-------------|-----------------------|-----------------------|
   | LEGO Insiders Early Access | 24h early bundles on Amazon. | Boosts limited sets sales, engages fanatics. | 340 |
   | Expand Adult Sets | 40 new 18+ SKUs/year (Icons, UCS). | Targets AFOLs (38% revenue, high AOV). | 280 |
   | Shoulder-Season Events | 6 hype events with deals. | Evens seasonality (shifts 12-18% demand). | 190 |
   | Review-Seeding Program | Vine + automation. | Improves rankings/conversions (+270% revenue). | 115 |
   | Predictive Pricing Engine | Python prototype for optimal pricing/restock. | Addresses pricing elasticity, prevents stockouts. | 95 |

**Development Plan**:
- **Tech Stack**: Python (Pandas, Prophet, LightGBM), Streamlit for dashboard.
- **Management**: Agile (bi-weekly demos), team: 3 engineers + 1 DS.
- **Prototype to Production**: Integrate with Amazon SP-API, deploy on AWS ($1.8M/3yr).

## Repository Structure
- `/data/`: Raw datasets (CSVs).
- `/notebooks/`: Jupyter notebooks for analysis (e.g., Price_Premium_Analysis.ipynb).
- `/output_charts/`: Generated figures (PNG).
- `/report/`: Full report PDF, presentation PPTX.
- `requirements.txt`: Dependencies (pandas, matplotlib, etc.).
- `README.md`: This file.

## Setup & Running
1. Clone repo: `git clone <repo-url>`.
2. Install deps: `pip install -r requirements.txt`.
3. Run notebooks: `jupyter notebook`.
4. Generate figures: Execute cells in order.

For questions, open an issue.
