The Pricing Analytics Toolkit
A 3-week applied pricing analytics project built around real-world pricing analyst problems: how to react to competitor price moves, how to time and size markdowns, and how to evaluate the tradeoff between price, volume, and margin.
The project is built in three modules on top of the Walmart Recruiting Store Sales Forecasting dataset (Kaggle, 2010-2012):

Module 1, Competitive Repricing Simulator: A rule-based engine that reacts to competitor price moves (simulated, layered on real Walmart sales as the base), with margin floor protection.
Module 2, Markdown & Promotion Optimization: Uses Walmart's real markdown event data to model discount timing and depth around major holidays.
Module 3, Price-Volume-Margin Dashboard: An interactive view of how price changes ripple through volume and margin, built for business decision-making, not just modeling.

Each module includes documented assumptions, since some inputs (unit price, competitor pricing, margin) aren't present in the raw dataset and are reasonably derived or simulated, clearly flagged throughout the code and writeups.
Built and documented day by day, Monday-Friday, over 3 weeks. Full writeup and findings for each module linked below.

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
