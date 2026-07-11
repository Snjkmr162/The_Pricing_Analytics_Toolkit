## 🏷️The Pricing Analytics Toolkit

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-orange)
![Data](https://img.shields.io/badge/Data-Walmart%20Kaggle-green)

A 3-week applied pricing analytics project built around real-world pricing analyst problems: how to react to competitor price moves, how to time and size markdowns, and how to evaluate the tradeoff between price, volume, and margin.
The project is built in three modules on top of the Walmart Recruiting Store Sales Forecasting dataset (Kaggle, 2010-2012):

Module 1, Competitive Repricing Simulator: A rule-based engine that reacts to competitor price moves (simulated, layered on real Walmart sales as the base), with margin floor protection.
Module 2, Markdown & Promotion Optimization: Uses Walmart's real markdown event data to model discount timing and depth around major holidays.
Module 3, Price-Volume-Margin Dashboard: An interactive view of how price changes ripple through volume and margin, built for business decision-making, not just modeling.

Each module includes documented assumptions, since some inputs (unit price, competitor pricing, margin) aren't present in the raw dataset and are reasonably derived or simulated, clearly flagged throughout the code and writeups.
Built and documented day by day, Monday-Friday, over 3 weeks.

Project Structure
```
pricing-analytics-toolkit/
│
├── data/                                        # Raw + processed data (gitignored where large/licensed)
│   └── README.md                                # Instructions to download Walmart dataset via Kaggle API
│
├── notebooks/                                   # Colab/Jupyter notebooks, one folder per module
│   ├── week1_repricing/
│   │   └── week1_repricing_simulator.ipynb
│   ├── week2_markdown/
│   │   └── week2_markdown_optimization.ipynb
│   └── week3_dashboard/
│       └── week3_price_volume_margin.ipynb
│
├── src/                                         # Reusable Python scripts (core logic, importable)
│   ├── week1_repricing_simulator.py
│   ├── week2_markdown_optimization.py
│   └── week3_dashboard_builder.py
│
├── outputs/                                     # Generated charts, CSVs, and dashboard exports
│   ├── week1/
│   ├── week2/
│   └── week3/
│
└── README.md
```
## 🔍 Key Findings

📦 Week 1 - Competitive Repricing
A naive rule-based engine triggered unnecessary repricings 79.9% of weeks on average
Adding a 10% minimum gap threshold reduced that to 41.7%, a 38.1% reduction
Trigger rates varied from 3.5% to 99% across departments, confirming no universal rule fits all
Key insight: repricing rules need a minimum gap threshold, not just a margin floor


🏷️ Week 2 - Markdown Optimization
Markdown lift ranged from 0.9% to 31.1% across departments on the same dataset
Low markdown spend returned $4.48 per dollar vs $0.63 for very high spend (7x difference in ROI)
Optimized timing (discounting at week -1, pre-event) outperformed all strategies at +4.7% vs baseline
Key insight: sales consistently peaked the week BEFORE the markdown event, not during it


📊 Week 3 - Price-Volume-Margin Dashboard
A +5% price increase produced +$188 margin gain (conservative demand) vs -$2,954 loss (aggressive demand)
That $1,571/week swing annualizes to $80,000+ on one department from one wrong elasticity assumption
Key insight: price decisions made without an elasticity view are guesses dressed up as strategy


 ## 🛠️ Tools and Tech

- Python (pandas, numpy, matplotlib)
- Google Colab
- Walmart Recruiting Store Sales Forecasting dataset (Kaggle, 2010-2012)
- Modeling: rule-based engines, price elasticity simulation, markdown decay analysis

## Documented Assumptions

Since the Walmart dataset does not include unit price, competitor pricing, or margin data,
the following assumptions are applied consistently across all three modules:

- **Price**: derived as an inverse proxy of normalized weekly sales, anchored to a $50 base ($40-$60 range)
- **Volume**: implied units = Weekly Sales / derived price
- **Competitor price** (Week 1): simulated as a mean-reverting random walk around own price (1.5% weekly volatility, seed=42)
- **COGS**: 60% of price (40% gross margin assumption, standard retail benchmark)
- **Elasticity** (Week 3): modeled across a range of -0.5 to -2.5, since true elasticity cannot be calculated from this dataset

All assumptions are clearly flagged in each notebook and src file.

