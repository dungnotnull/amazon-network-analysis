# Amazon Co-Purchasing Network Analysis

**Comprehensive network analysis** of the Amazon product co-purchasing graph (March 02, 2003) using graph theory, centrality measures, community detection, and information diffusion modeling.

## Overview

This project performs an in-depth structural and functional analysis of the Amazon co-purchasing network -- a directed graph where nodes represent products and edges represent frequent co-purchasing relationships. The analysis covers topological properties, centrality distributions, community structure, network robustness, and epidemiological simulations.

The dataset contains **262,111 nodes** and **1,234,877 edges** from the Stanford Network Analysis Project (SNAP).

## Dataset

- **Source**: Stanford Network Analysis Project (SNAP) -- Amazon product co-purchasing network, March 02 2003
- **Nodes**: 262,111 (products)
- **Edges**: 1,234,877 (co-purchasing relationships)
- **Type**: Directed graph
- **Format**: Edge list (tab-separated: `FromNodeId  ToNodeId`)

## Analysis Pipeline

### 1. Power Law Degree Distribution
Analysis of whether node degrees follow a power law distribution, a hallmark of scale-free networks. Both in-degree and out-degree distributions are examined on log-log plots.

![Power Law](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/01_power_law.png)

### 2. Centrality Analysis
Computation and comparison of multiple centrality measures to identify the most influential products:

- **Degree Centrality**: Direct co-purchasing connections
- **PageRank**: Recursive importance score based on incoming links
- **Betweenness Centrality**: Bridge role in connecting different product segments

![Centrality Distribution](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/02_centrality_distribution.png)

### 3. Degree Correlation (Assortativity)
Examination of whether high-degree nodes tend to connect to other high-degree nodes (assortative) or low-degree nodes (disassortative). This reveals the network's mixing pattern and structural organization.

![Degree Correlation](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/03_degree_correlation.png)

### 4. Node Similarity Heatmap
Computation of similarity scores between products based on shared neighbors (Jaccard similarity or cosine similarity), visualized as a heatmap to identify product clusters and substitution patterns.

![Similarity Heatmap](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/04_similarity_heatmap.png)

### 5. Community Detection
Identification of product communities using two algorithms:
- **Louvain Community Detection**: Fast modularity-based clustering
- **Walktrap Community Detection**: Random walk-based clustering

Community labels are assigned to each product, revealing natural product categories and market segments.

![Community Detection](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/05_community_detection.png)

### 6. Network Visualization (Gephi)
High-quality visualizations using Gephi force-directed layout algorithms:
- **Full network** (262K nodes): SVG export showing overall topology
- **Top 1000 nodes**: Filtered view showing the most connected products with community coloring

![Top 1000 Visualization](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/amazon_gephi_top1000.png)

### 7. Network Robustness Analysis
Evaluation of network resilience under two attack scenarios:
- **Random failures**: Random node removal -- tests inherent fault tolerance
- **Targeted attacks**: Sequential removal of highest-degree nodes -- tests vulnerability to strategic disruption

![Robustness](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/07_robustness.png)

### 8. SIR Epidemic Model Simulation
Simulation of information/product adoption spreading using the Susceptible-Infected-Recovered (SIR) model:
- Models how products or trends propagate through the co-purchasing network
- Examines infection curves under different transmission rates
- Identifies conditions for viral spread vs. containment

![SIR Simulation](Amazon%20Network%20Analysis%20Resources-20260524T133643Z-3-001/Amazon%20Network%20Analysis%20Resources/08_sir_simulation.png)

## Outputs

| File | Description |
|------|-------------|
| `amazon_full_analysis.csv` | Complete per-node metrics (degree, PageRank, betweenness, community, rank) for all 262,111 analyzed nodes |
| `Top500_Metrics.csv` | Metrics for the top 500 most important products |
| `amazon_gephi_full.gexf` | Full network export for Gephi visualization |
| `amazon_gephi_full.svg` | Full network force-directed layout |
| `amazon_gephi_top1000.gexf` | Top 1000 nodes for Gephi visualization |
| `amazon_gephi_top1000.svg` | Top 1000 interactive/large visualization |

## Project Structure

```
amazon-network-analysis/
|-- Amazon_Network_Analysis_v2.ipynb        # Main analysis notebook
|-- Amazon Network Analysis Resources/
|   |-- Amazon0302.txt                      # Raw dataset (edge list)
|   |-- amazon_full_analysis.csv            # Per-node metrics
|   |-- 01_power_law.png                    # Power law distribution
|   |-- 02_centrality_distribution.png      # Centrality distributions
|   |-- 03_degree_correlation.png           # Degree correlation
|   |-- 04_similarity_heatmap.png           # Node similarity
|   |-- 05_community_detection.png          # Community structure
|   |-- 06_network_visualization.png        # Network visualization
|   |-- 07_robustness.png                   # Robustness analysis
|   |-- 08_sir_simulation.png               # SIR simulation
|   |-- amazon_gephi_full.gexf              # Full network (Gephi)
|   |-- amazon_gephi_full.svg               # Full network visual
|   |-- amazon_gephi_top1000.gexf           # Top 1000 (Gephi)
|   |-- amazon_gephi_top1000.png            # Top 1000 visual
|   |-- amazon_gephi_top1000.svg            # Top 1000 vector
|-- README.md
```

## Key Findings

- **Scale-free topology**: The degree distribution follows a power law, indicating a hub-dominated structure where a few products act as super-connectors
- **Disassortative mixing**: High-degree products tend to connect to low-degree products, typical of e-commerce networks where popular items connect to many niche products
- **Clear community structure**: Louvain and Walktrap algorithms reveal distinct product categories matching real-world market segments
- **Robust-yet-fragile**: The network is highly resilient to random failures but vulnerable to targeted attacks on hub nodes
- **Epidemic threshold**: SIR simulations show information/product adoption can rapidly spread above a critical transmission rate

## Requirements

```txt
networkx>=3.0
pandas
numpy
matplotlib
seaborn
igraph  (or python-igraph)
scipy
jupyter
```

```bash
pip install networkx pandas numpy matplotlib seaborn python-igraph scipy jupyter
```

## Usage

```bash
jupyter notebook Amazon_Network_Analysis_v2.ipynb
```

## Tools Used

- **NetworkX & igraph**: Graph construction and analysis
- **Gephi**: High-quality network visualization
- **Python**: pandas, numpy, scipy, matplotlib, seaborn
- **Stanford SNAP**: Original dataset source

## License

Dataset from Stanford Network Analysis Project (SNAP). Analysis code for academic and research purposes.
