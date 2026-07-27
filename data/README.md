# Dataset Setup

The raw datasets are not included in this repository because of their size and distribution requirements.

## Road Accident Data

The project uses a UK road-accident SQLite database based on the STATS19 schema for 2017–2019, with accident, vehicle, casualty and LSOA tables.

Place the database/data files under:

```text
data/raw/
```

## Social Network Data

The network-analysis section uses a Facebook combined friendship graph.

Place the graph data under:

```text
data/raw/
```

Before running the notebook, check the data-loading cells and update filenames to match the copies you have locally. Run Jupyter from the repository root so relative paths can be used consistently.
