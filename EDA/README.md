# Exploratory analysis and product clustering

[Project](../README.md) · [Data methodology and figures](../docs/wiki/Data.md)

- `EDA_KJH_ver*.py` / `.ipynb`: successive exploratory analyses by Junhyuk Kwon; historical Korean notebook text is retained.
- `get_similarity.py`: product-name similarity.
- `get_cluster.py`, `utils_cluster.py`: clustering.
- `category_preprocess.py`, `utils_category.py`: category transformations.
- `merge_cluster_train.py`: training-data integration.

After cleaning names, sort products and compare within a local window rather than all pairs. Depth-limited BFS prevents excessive transitive merging. Autoencoder-compressed category/seller features and a Random Forest support a separate quality check.

Similarity-calculation time fell from **15 hours to 10 minutes**. **81 / 2,630 clusters** were flagged for inspection (**3.1%**), a triage proportion rather than measured matching accuracy.

Notebooks depend on private data and environment-specific paths; inspect configuration before execution.
