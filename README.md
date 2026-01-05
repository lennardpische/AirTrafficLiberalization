# Air Traffic Liberalization and Consumer Welfare
### A Volume-Based Analysis of the 2018 U.S.-Brazil Open Skies Agreement

![Status](https://img.shields.io/badge/Status-Completed-success) ![R](https://img.shields.io/badge/Made%20with-R-blue)

## 📄 Abstract
This project evaluates the impact of the 2018 Open Skies Agreement (OSA) between the United States and Brazil on international passenger volumes. Using a **Segmented Difference-in-Differences (DiD)** design on route-level data from 2015 to 2020, the study identifies whether liberalization led to an increase in passenger flows, interpreting this volume increase as a proxy for consumer welfare.

The analysis specifically isolates the policy shock from concurrent macroeconomic events, notably the **2019 Brazilian economic recession**, to provide a robust estimate of the agreement's short-run effects.

## 🔍 Key Findings
* **Modest Policy Effect:** The regression yields a positive but statistically insignificant treatment coefficient of **0.008**, suggesting a roughly **0.8% increase** in passenger traffic attributable to the Open Skies Agreement in the short run.
* **Recessionary Dampening:** The interaction term for the 2019 Brazilian recession is negative (**-0.091**) and statistically significant at the 5% level. This indicates that worsening macroeconomic conditions substantially eroded the initial gains from liberalization.
* **Visual Evidence:** Graphical analysis reveals parallel pre-treatment trends between U.S.-Brazil routes and the control group (U.S.-Rest of World), with a slight divergence appearing mid-2018 before widening due to the 2019 economic downturn.

## 🛠 Methodology
### Data Sources
* **Flight Data:** U.S. Bureau of Transportation Statistics (BTS) **T-100 International Segment Data** (Monthly passenger counts, 2015–2020).
* **Macro Controls:** **CEPII 2022 Gravity Dataset** (GDP and Population).
* **Geography:** `rnaturalearth` package for hemisphere classification (to control for seasonality).

### Empirical Strategy
The study employs a **Segmented Difference-in-Differences (DiD)** model:

$$ \ln(\text{Passengers})_{it} = \alpha + \beta_1 \text{TREAT} + \beta_2 \text{TREAT-RECESSION} + \text{Controls} + \text{FE} + \epsilon_{it} $$

* **Treatment Group:** U.S.-Brazil routes (Post-March 2018).
* **Control Group:** U.S. routes to the rest of the world.
* **Fixed Effects:** Country-Pair, Month-Year, and Hemisphere-by-Month (to account for inverted seasonality in the Southern Hemisphere).
* **Robustness:** Standard errors clustered at the country-pair level; Pandemic period (Post-March 2020) excluded to avoid structural breaks.

## 💻 Tech Stack
* **Language:** R (RMarkdown)
* **Key Libraries:** * `fixest`: For high-dimensional fixed effects estimation.
    * `tidyverse`: Data manipulation and cleaning.
    * `rnaturalearth`: Geospatial data for seasonality controls.
    * `modelsummary` & `ggplot2`: Tables and visualizations.

## 📂 Repository Structure
```text
├── Final Paper EC970.Rmd          # Source code for data cleaning, regression, and visualization
├── AirTrafficLiberalization.pdf   # Final research paper with full econometric analysis
└── README.md                      # Project documentation
