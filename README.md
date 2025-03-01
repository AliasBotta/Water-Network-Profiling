# Node Profiling in a Water Distribution Network

Welcome to the repository dedicated to the **profiling of nodes in a simulated water distribution network**, developed during the *Fundamentals of Data Science* course as part of our Bachelor's program. This project was created by **Alessandro Botta**, **Alex Di Corrado**, **Riccardo Schiera**, **Luca Buccheri**, and **Giampiero Fuschi**, leveraging Data Science techniques, particularly **PCA** and **k-means clustering**, to extract valuable insights from a water network simulation dataset.

---

## Table of Contents
- [Project Objectives](#project-objectives)
- [Repository Structure](#repository-structure)
- [Dataset Description](#dataset-description)
- [Methodological Approach](#methodological-approach)
  - [Data Pre-Processing](#data-pre-processing)
  - [PCA (Principal Component Analysis)](#pca-principal-component-analysis)
  - [K-Means Clustering](#k-means-clustering)
- [Tools and Frameworks Used](#tools-and-frameworks-used)
- [Key Strengths and Conclusions](#key-strengths-and-conclusions)

---

## Project Objectives
The main goal is to **profile the nodes** of a simulated water network, identifying how they can be grouped based on shared characteristics (such as location, demand, pressure, etc.). This project focuses on:
1. Data analysis and dimensionality reduction through **PCA**.
2. Node segmentation using **k-means clustering**.
3. Interpreting results to identify patterns that could be useful for real-world water network management.

---

## Repository Structure

```bash
.
├── dataset
│   └── 1M_one_res_small_no_leaks_rand_bd_merged.csv
├── docs
│   ├── Assignment.pdf
│   └── Report.pdf
├── README.md
└── src
    └── main.ipynb
```

- **dataset**: Contains the CSV file with raw data from the water network simulation.
- **docs**: Includes supporting materials and our detailed report explaining each project phase and the obtained results.
- **README.md**: This main documentation file.
- **src**: Contains the `main.ipynb` notebook, where the entire analysis pipeline (pre-processing, PCA, clustering, and visualization) is executed.

---

## Dataset Description
The dataset represents the hourly evolution (from hour 0 to 671) of multiple nodes in a simulated water distribution network. Each row contains information such as:
- **nodeID**: Unique node identifier;
- **base demand**, **demand value**: Expected and actual water demand;
- **head value**, **pressure value**: Physical metrics representing water potential energy and pressure;
- **x pos**, **y pos**: Spatial coordinates of the node;
- Other characteristics, such as *tot network demand*, which describes the overall demand of the entire network.

By aggregating data per node, we reduced the original dataset to a single average entry for each node (83 nodes in total), simplifying the subsequent analysis.

---

## Methodological Approach

### Data Pre-Processing
1. **Data Cleaning**: Removal of irrelevant attributes (e.g., leak-related attributes, which were null since no leaks were present in this simulation).
2. **Aggregation**: Computation of the hourly average for each node to obtain a more manageable dataset.
3. **Normalization**: Application of *StandardScaler* (Z-score) to numerical variables to standardize their ranges, facilitating the subsequent analysis.

### PCA (Principal Component Analysis)
**PCA** was used to:
- Reduce the dataset’s dimensionality.
- Identify *principal components* that explain most of the variance in the data.
- Simplify visualization and reveal hidden patterns.

Using libraries like *scikit-learn*, we computed and visualized principal components (in 2D and 3D). The analysis showed that **2 or 3 principal components** retained most of the original data information, aiding interpretation.

### K-Means Clustering
After dimensionality reduction, we applied the **k-means clustering** algorithm to segment nodes into homogeneous groups through the following steps:
1. **Choosing the optimal number of clusters (k)** using the *Elbow Method* and *Silhouette Score*.
2. **Initialization and Assignment**: Each data point (node) is assigned to the nearest centroid, forming clusters.
3. **Iterative centroid updates** until stabilization of the clustering.

Final results revealed that nodes clustered based on physical attributes (location, pressure) and demand characteristics (base demand, demand value), offering insights for informed network management.

---

## Tools and Frameworks Used
- **Python 3**: Primary development language.
- **Jupyter Notebook**: For documenting and executing code interactively (`main.ipynb`).
- **pandas**: For data manipulation (cleaning, aggregation, and merging datasets).
- **NumPy**: For numerical and algebraic operations.
- **scikit-learn**: For implementing *StandardScaler*, *PCA*, and *k-means clustering*.
- **Matplotlib**: For visualizing results, including 2D/3D plots of PCA and clustering.

These frameworks, when used together, create an effective and modular *analysis pipeline*, from data ingestion to final interpretation.

---

## Key Strengths and Conclusions
- **Modularity**: The project follows a well-defined pipeline (pre-processing → dimensionality reduction → clustering), making it easily extendable or modifiable.
- **Analytical Clarity**: PCA enhances understanding of the main patterns in the data, simplifying subsequent clustering steps.
- **Scalability**: The code is designed to be easily adapted to larger datasets or those with different characteristics.
- **Transparency**: Each step is documented and supported by graphical visualizations, ensuring reproducibility of results.

In conclusion, the combination of dimensionality reduction and clustering proved effective in identifying similarities and differences among nodes in a simulated water network, offering a flexible approach applicable to *data-driven water management* scenarios.
