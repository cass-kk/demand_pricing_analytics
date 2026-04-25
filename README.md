# Uber vs. Lyft: Demand Patterns, Revenue Management, and Competitive Pricing Strategy

**Course:** OM386 - Revenue Management, Demand & Sales Analysis  
**Institution:** McCombs School of Business, UT Austin  
**Authors:** Melissa Cai Shi, Mohar Chaudhuri, Cassandre Korvink-Kucinski, Hardy Smith  
**Date:** April 2025

---

## Background

Ride-hailing platforms like Uber and Lyft are among the most visible real-world applications of algorithmic revenue management. Unlike traditional taxi markets with fixed regulated fares, both platforms use dynamic (surge) pricing to continuously balance supply and demand across thousands of geographic micro-markets in real time.

Uber operates as a two-sided marketplace, earning a 20-25% commission on each completed trip. This creates a classic yield management tension: prices set too high suppress demand and reduce trip volume, while prices set too low fail to attract enough driver supply. The surge multiplier is the mechanism meant to solve that problem. This project asks whether Lyft responds to Uber's pricing signals, or whether the two platforms price independently despite operating in the same markets at the same times.

---

## Objective

This project analyzes the revenue management strategies of Uber and Lyft across three integrated sections:

1. **Demand Elasticity** - Quantifying how sensitive rideshare demand is to price changes and identifying the patterns that drive surge triggers
2. **Revenue Maximization** - Evaluating how effectively Lyft uses surge pricing to capture available revenue, and where it leaves money on the table
3. **Competitive Pricing Analysis** - Testing whether Lyft responds to Uber's surge pricing signals, or whether the two platforms price independently

The central finding is that despite operating in the same geographic markets at the same times, Uber and Lyft price independently of each other. The surge correlation between platforms is r = -0.033, Lyft's price is not a significant predictor of Uber's price after controlling for route, time, and weather (p = 0.515), and Granger causality tests find no lead-lag pricing relationship on any of the six highest-traffic routes examined. Additionally, Lyft misses surge opportunities in 18.5% of matched route-time windows where Uber is already surging, representing a systematic revenue management gap.

---

## Dataset

**Source:** [Uber & Lyft Dataset - Boston, MA](https://www.kaggle.com/datasets/brllrb/uber-and-lyft-dataset-boston-ma) (Kaggle: `brllrb/uber-and-lyft-dataset-boston-ma`)

- 693,071 rideshare trips in Boston, MA
- Collected via real-time API queries over 22 days in November-December 2018
- Covers both Uber and Lyft trips across multiple routes, service tiers, and weather conditions

---

## Folder Structure

```
project-root/
│
├── charts/                                              # All saved charts, graphs, and figures exported from notebooks
│
├── OM386_Section_1_Demand_Elasticity_Code_Hardy.ipynb   # Section 1: Demand elasticity analysis
├── OM386_Section_2_Revenue_Maximization_Code_Cass_and_Mel.ipynb  # Section 2: Lyft surge pricing and revenue analysis
├── OM386_Section_3_Competitive_Analysis_Code_Mohar.ipynb         # Section 3: Competitive pricing dynamics
│
├── OM386_Lyft_vs_Uber_Project_Report.pdf               # Full written report
├── OM386_Lyft_vs_Uber_Project_Slide_Deck.pdf           # Slide deck (PDF version)
├── OM386_Lyft_vs_Uber_Project_Slide_Deck.pptx          # Slide deck (PowerPoint version)
│
└── README.md
```

---

## Tools and Packages

| Package | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, and manipulation |
| `numpy` | Numerical operations |
| `matplotlib` / `seaborn` | Data visualization and chart exports |
| `statsmodels` | OLS regression, Granger causality tests |
| `scipy` | Statistical tests |
| `scikit-learn` | Feature engineering, preprocessing |
| `plotly` | Interactive geospatial maps |


---

## Modeling Notes

- **OLS Regression** is used throughout to quantify the drivers of fare price and to test whether Lyft's pricing responds to Uber's surge signals after controlling for route, time of day, and weather conditions.
- **Granger Causality Tests** are applied on the six highest-traffic routes to test for any lead-lag pricing relationship between the two platforms.
- **Matched Route-Time Pairs** are constructed to enable apples-to-apples comparison between Uber and Lyft fares at the same location and time window. An engineered surge proxy is used for Uber since direct multiplier data is not available in the dataset.
- **Demand Elasticity** is estimated econometrically to characterize the price-demand relationship and explain the price-demand paradox observed in the raw data.
- All three notebooks are meant to be read together as the analyses are interconnected. Section 1 establishes baseline demand behavior, Section 2 evaluates Lyft's revenue capture, and Section 3 brings both platforms into direct comparison.

---

## Key Findings

- Surge correlation between Uber and Lyft: **r = -0.033** (effectively zero)
- Lyft's price is not a significant predictor of Uber's price after controls: **p = 0.515**
- Lyft misses surge opportunities in **18.5%** of windows where Uber is already surging
- No Granger-causal lead-lag relationship was found on any of the six highest-traffic routes
- Rideshare demand is largely **inelastic** to price within the observed range, consistent with the platform's role as a convenience good with few substitutes in the short run
