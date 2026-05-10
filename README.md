#  TMDB Movies Dataset — Analysis & Recommendation System

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Data Mining](https://img.shields.io/badge/Data_Mining-Academic_Project-58a6ff?style=for-the-badge)
![Records](https://img.shields.io/badge/Records-1.1M+-3fb950?style=for-the-badge)
![NLP](https://img.shields.io/badge/NLP-TF--IDF-d2a8ff?style=for-the-badge)

> Academic data mining project applying EDA, NLP, association rules, and clustering techniques to the Full TMDB Movies Dataset.

---

## Table of Contents

- [Problem Definition](#-problem-definition)
- [Dataset Description](#-dataset-description)
- [Objectives](#-objectives)
- [Techniques Applied](#-data-mining-techniques-applied)
- [Project Structure](#-project-structure)
- [Results Overview](#-results-overview)

---

##  Problem Definition

The film industry generates massive amounts of structured and unstructured data. Analyzing this information can reveal patterns related to **genre trends**, **popularity**, **revenue distribution**, and **audience preferences**.

This project applies data mining techniques to a large-scale movie dataset in order to extract knowledge and build a **movie recommendation system**.

---

## Dataset Description

**Source:** Datadruids (2026). *Full TMDB Movies Dataset*. HuggingFace.
🔗 [huggingface.co/datasets/ada-datadruids/full_tmdb_movies_dataset](https://huggingface.co/datasets/ada-datadruids/full_tmdb_movies_dataset)

**Processed version used for clustering:** pauguzman (2026). *TMDB Minería de Datos Processed*. HuggingFace.
🔗 [huggingface.co/datasets/pauguzman/tmdb_mineria_datos_processed](https://huggingface.co/datasets/pauguzman/tmdb_mineria_datos_processed)

### At a Glance

| Attribute | Value |
|-----------|-------|
| Total Records | 1,142,342 movies |
| Attributes | 24 columns |
| Dataset Year | 2026 |

### Variable Types

| Type | Variables |
|------|-----------|
| **Numerical** | `budget`, `revenue`, `runtime`, `vote_count`, `popularity` |
| **Categorical** | `genres`, `original_language` |
| **Textual** | `overview`, `keywords` |

---

## Objectives

1. **Exploratory Data Analysis** — Understand patterns and distributions across the dataset.
2. **Preprocessing & Cleaning** — Handle large-scale structured and unstructured data.
3. **Feature Engineering** — Extract meaningful features from textual attributes using NLP.
4. **Association Rules** — Discover frequent genre co-occurrence patterns.
5. **Clustering** — Group movies into meaningful segments using multiple algorithms.
6. **Recommendation System** — Develop a content-based movie recommendation model.

---

##  Data Mining Techniques Applied

| Category | Techniques |
|----------|------------|
| **Preprocessing** | Missing value handling, data cleaning, normalization |
| **Feature Engineering** | Variable transformation, encoding, PCA (5 components, 93.6% variance) |
| **NLP / Text Mining** | TF-IDF vectorization |
| **Association Rules** | Apriori, FP-Growth — genre co-occurrence patterns |
| **Clustering** | K-Means, Agglomerative Hierarchical (Ward) |
| **Similarity** | Euclidean distance in PCA space — cluster-based recommendation |

---

## Project Structure

## Project Structure

```text
├── Associacion.ipynb             # Association rules: Apriori & FP-Growth
├── K_Means_Clustering.ipynb      # K-Means: elbow method, optimal k, cluster profiles
├── Hierarchical_Clustering.ipynb # Agglomerative clustering: Ward linkage, dendrogram
└── README.md
```

## Results Overview

### Association Rules
Genre co-occurrence patterns were mined from 116,929 movies using **Apriori** and **FP-Growth**. The most significant rules revealed strong associations between genres such as Action→Adventure and Drama→Romance, with FP-Growth achieving faster execution times on the full binary genre matrix.

### Clustering
All three clustering algorithms were applied on **PC1–PC5** (93.6% of explained variance). The optimal number of clusters **k=4** was determined via the elbow method and Silhouette analysis on K-Means.

**K-Means** was run on the full 116,929-movie dataset and identified four distinct groups. **Hierarchical Clustering** (Ward linkage) was applied to a representative sample of 85,000 movies (72.7% of the catalog) — the largest feasible size given the O(n²) memory complexity of agglomerative methods. *

The four clusters recovered consistently across algorithms represent:

| Cluster | Profile | Key Signal |
|---------|---------|------------|
| **Modern Blockbusters** | High-popularity recent films | Avg popularity 101.55, avg year 2010 |
| **Obscure Classic Cinema** | Old, low-visibility catalog | Avg year 1973, avg popularity 3.31 |
| **Critically Acclaimed** | High-rated, moderate reach | Highest avg rating 7.53 |
| **Contemporary Mainstream** | Largest group, average metrics | 45.8% of sample, avg year 2011 |

**Internal validation metrics (85k sample):**

| Metric | K-Means | Hierarchical |
|--------|---------|--------------|
| Silhouette ↑ | **0.4091** | 0.3025 |
| Davies-Bouldin ↓ | **1.0245** | 1.1719 |
| Calinski-Harabasz ↑ | **27,475** | 24,531 |

---

<p align="center">
  <sub>Academic Data Mining Project &nbsp;·&nbsp; TMDB Movies Dataset &nbsp;·&nbsp; For educational use only</sub>
</p>