# Visualizing-Data-Veracity-Challenges-in-Multi-Label-Classification

This repository contains the solution for the assignment "DA5401 A5: Visualizing Data Veracity Challenges in Multi-Label Classification". The project focuses on using non-linear dimensionality reduction techniques, specifically **t-SNE** and **Isomap**, to visually inspect the Yeast dataset for data quality issues like noisy labels, outliers, and hard-to-learn samples.

---

**Author:** Nikhil Enugu

**Roll No:** DA25M010

---

## 🎯 Objective

The primary goal of this assignment is to understand the challenges of real-world machine learning in the context of multi-label classification. By applying t-SNE and Isomap to gene expression data, this project aims to visually expose data veracity issues and understand the difficulties a classifier would face.

---

## 🔬 Methodology

The project is divided into three main parts as outlined in the assignment:

### Part A: Preprocessing and Initial Setup
1.  **Data Loading**: The Yeast dataset is loaded from an `.arff` file. The feature matrix `X` (103 features) and the multi-label target matrix `Y` (14 labels) are separated.
2.  **Dimensionality Check**: The initial dimensions of the dataset are reported as 2417 data points and 103 features.
3.  **Label Selection**: To simplify visualization, a new target variable is created for coloring. This variable represents the most frequent single-label class, the most frequent multi-label combination, and categorizes the rest as "Other".
4.  **Scaling**: Standardization is applied to the feature matrix `X` because scaling is crucial for distance-based dimensionality reduction techniques to prevent features with larger numeric ranges from dominating the results.

### Part B: t-SNE and Veracity Inspection
1.  **t-SNE Implementation**: t-SNE is applied to the scaled feature matrix to reduce it to 2 dimensions. The `perplexity` hyperparameter is experimented with (5, 10, 15, 30, 40, 50), and a final choice is justified based on the quality of the visualization.
2.  **Visualization**: A 2D scatter plot of the t-SNE coordinates is created, with points colored according to the categories created in Part A.
3.  **Veracity Inspection**: The plot is analyzed to visually identify:
    * **Noisy/Ambiguous Labels**: Points of one color embedded within a cluster of another color.
    * **Outliers**: Isolated points or small, distant clusters.
    * **Hard-to-Learn Samples**: Areas where different category colors are thoroughly mixed.

### Part C: Isomap and Manifold Learning
1.  **Isomap Implementation**: Isomap is applied to the scaled feature matrix to reduce it to 2 dimensions. The fundamental difference between Isomap (preserving global structure) and t-SNE (preserving local structure) is explained.
2.  **Visualization**: A 2D scatter plot of the Isomap coordinates is created using the same coloring scheme.
3.  **Comparison and Curvature**: The Isomap and t-SNE visualizations are compared to determine which better reveals the global structure. The concept of the data manifold is discussed, and the complexity of the manifold is related to the difficulty of classification.

---

## 📊 Results and Findings

### t-SNE Visualization & Analysis
The t-SNE plot successfully revealed distinct clusters.
* **Noisy Labels**: Were identified where points from one category were located deep within a cluster of another, suggesting potential misclassifications.
* **Outliers**: Appeared as isolated points, hypothesized to be experiments with unusual gene expression profiles.
* **Hard-to-Learn Samples**: Were found in regions where functional categories were heavily mixed, indicating that a simple classifier would struggle in these areas.

### Isomap Visualization & Analysis
The Isomap visualization provided a different perspective on the data's structure.
* **Global vs. Local Structure**: Compared to t-SNE, Isomap was better at revealing the global structure of the gene expression data.
* **Data Manifold**: The Isomap plot suggested a relatively simple and smoothly curved manifold. The classification difficulty was attributed more to the intrinsic similarity between classes rather than the geometric complexity of the manifold.
