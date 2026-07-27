# UK Road Accident Analytics

An end-to-end data mining project analysing UK road accidents from **2017–2019**, with additional social-network analysis demonstrating graph-mining techniques.

Developed as part of the MSc Artificial Intelligence & Data Science programme, the project combines exploratory analysis, association-rule mining, clustering, dimensionality reduction, time-series forecasting and network analysis.

## Project Overview

The main analysis uses UK road-accident data based on the STATS19 schema. The project investigates:

- temporal accident patterns;
- pedestrian and motorcycle risk;
- environmental accident conditions;
- accident segmentation in the Humber region;
- weekly and daily accident forecasting;
- graph structure and community detection using a Facebook friendship network.

## Road Accident Data

The accident data were supplied in a SQLite database with four principal tables: `accident`, `vehicle`, `casualty` and `lsoa`. After merging and preprocessing, the main 2019 analytical dataset contained approximately **153,000 rows and 95 columns**.

The raw database is not included in this repository. See [`data/README.md`](data/README.md).

## Data Preparation

Key preparation steps included joining accident, vehicle, casualty and LSOA information; deriving temporal features; treating special values as missing where appropriate; validating relational identifiers; constructing cleaned driver/vehicle variables; and standardising numeric features before clustering.

## Exploratory Findings

### Temporal Patterns
Road accidents showed clear commuting-related peaks, particularly around **08:00** and **17:00**. Fridays recorded the highest overall collision volume, while Sundays recorded the lowest.

### Pedestrian Casualties
The 2019 pedestrian subset contained **21,770 records**. Slight injuries dominated, but the analysis also identified nearly 6,000 serious injuries and 509 fatalities.

### Motorcycle Accidents
Motorcycles were grouped by engine capacity. Larger motorcycles showed stronger afternoon/evening accident patterns, while smaller motorcycles contributed more to the morning commuting peak.

## Association Rule Mining

The Apriori algorithm was used to explore frequent combinations of weather, lighting, road-surface condition, urban/rural context, speed-limit bands and casualty severity. Minimum support was **0.02** and confidence **0.30**.

## Clustering: Humber Region

K-Means clustering was applied to accidents in Hull, East Riding and the wider Humberside area. After standardisation, values of `k` from 2–6 were assessed, with **k = 3** providing a useful balance between simplicity and fit. PCA was used to visualise the clusters in two dimensions.

## Time-Series Forecasting

Seasonal Holt-Winters exponential smoothing was used to forecast accident counts.

### Weekly Police-Force Forecasts

| Police Force | MAE | RMSE |
|---|---:|---:|
| Metropolitan Police | 66.2 | 84.3 |
| West Yorkshire Police | 13.2 | 16.5 |
| Humberside Police | **7.8** | **10.2** |

### High-Risk Hull LSOAs

The 30 highest-risk Hull LSOAs from Q1 2019 were used to create a daily accident series. A weekly-seasonal Holt-Winters model forecasting July 2019 achieved approximately **MAE 0.87 accidents/day** and **RMSE 1.10**.

## Social Network Analysis

The second part analyses a Facebook friendship graph containing **4,039 nodes** and **88,234 undirected edges**, with an average degree of approximately **43.7** and density around **0.01**.

The analysis includes degree distribution, edge betweenness centrality, Louvain community detection and Girvan-Newman community detection. Louvain detected **16 communities** in the full graph.

## Technologies

**Python • Pandas • NumPy • SQLite • Matplotlib • Scikit-learn • Statsmodels • mlxtend • NetworkX • PCA • K-Means • Apriori • Holt-Winters**

## Repository Structure

```text
uk-road-accident-analytics/
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
├── notebooks/
│   └── uk_road_accident_analytics.ipynb
├── data/
│   └── README.md
└── results/
    └── figures/
```

## Installation

```bash
git clone https://github.com/Ape-programmer/uk-road-accident-analytics.git
cd uk-road-accident-analytics
python -m venv .venv
pip install -r requirements.txt
```

Place the required datasets according to `data/README.md`, then start Jupyter from the repository root.

## Key Takeaways

- UK road accidents display strong temporal structure linked to commuting patterns.
- Pedestrians and motorcyclists show distinct risk profiles.
- Association-rule mining reveals recurring combinations of accident conditions, although these relationships are not causal.
- K-Means and PCA provide an exploratory view of different accident contexts in the Humber region.
- Seasonal forecasting captured useful weekly and daily accident patterns.
- Graph analysis identified hubs, bridge edges and community structure in a large social network.

## Limitations

- Association rules describe co-occurrence rather than causation.
- K-Means assumes relatively simple cluster geometry and is sensitive to feature scaling.
- Forecasting results depend on the historical period and may not generalise to structural changes in road use.
- Absolute forecast errors are affected by differences in accident volume between police-force areas.
- The Facebook analysis is a separate demonstration of network-mining methods rather than part of the road-safety dataset.

## Future Improvements

Potential extensions include SARIMA/Prophet forecasting comparisons, geospatial hotspot mapping, interactive dashboards, advanced clustering, severity prediction models, graph embeddings and deployment of forecasting results through a lightweight application.

## Author

**Abiola Peace Emmanuel**  
MSc Artificial Intelligence & Data Science  
GitHub: **Ape-programmer**
