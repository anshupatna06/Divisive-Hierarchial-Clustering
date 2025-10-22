# Divisive-Hierarchial-Clustering
"ML models implemented from scratch using NumPy and Pandas only"

# 🧩 Divisive Hierarchical Clustering — From Scratch

This project implements **Divisive Hierarchical Clustering (Top-Down Hierarchical Clustering)** from scratch, with visualization using a dendrogram (for hierarchical structure).

---

## 📘 Overview

**Divisive Hierarchical Clustering (DIANA)** is a **top-down** clustering algorithm.  
It begins with **all data points in one cluster**, and recursively **splits clusters** until the desired number of clusters `k` is reached.

---

## ⚙️ Algorithm Workflow

1. **Start with all data points** in one cluster.
2. **Select the cluster with the largest variance** (the one with most internal dissimilarity).
3. **Split it into two subclusters** using a 2-means algorithm.
4. **Repeat** the splitting process until the target number of clusters `k` is reached.

---

## 🧮 Mathematical Formulation

### 1️⃣ Cluster Variance

To decide which cluster to split next, we compute the **mean variance** of each cluster:

$$\[\sigma^2(C) = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{x})^2\]$$

where  
- $$\( C \) $$= current cluster  
- $$\( n \)$$ = number of points in the cluster  
- $$\( x_i \)$$ = feature vector of data point \( i \)  
- $$\( \bar{x} \)$$ = mean vector of cluster \( C \)

We choose the cluster \( C^* \) with **maximum variance**:

$$\[C^* = \arg\max_{C} \sigma^2(C)\]$$

---

### 2️⃣ 2-Means Split

The selected cluster \( C^* \) is split using **K-Means (k = 2)**:

$$\[\text{minimize } J = \sum_{i=1}^{n} \sum_{j=1}^{2} r_{ij} \| x_i - \mu_j \|^2\]$$

where  
- $$\( \mu_j \) = centroid of cluster \( j \)$$  
- $$\( r_{ij} = 1 \)$$ if $$\( x_i \)$$ belongs to cluster $$\( j \)$$, else $$\( 0 \)$$

This produces two new clusters $$\( C_1 \)$$ and $$\( C_2 \)$$.

---

### 3️⃣ Iteration Rule

After splitting, the algorithm updates the cluster list:

$$\[\text{Clusters} = (\text{Clusters} - \{ C^* \}) \cup \{ C_1, C_2 \}\]$$

and repeats until the desired number of clusters `k` is obtained.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Input: Dataset X, number of clusters k Initialize clusters = [X]

while len(clusters) < k: Select cluster with maximum variance Apply 2-means to split it into two parts Replace old cluster with two new clusters
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
🧠 Key Points

Top-Down Approach (opposite of Agglomerative)

Uses variance to select cluster for splitting

Uses K-Means internally to perform binary splits

Dendrogram provides hierarchical view (for interpretation only)

Works well for moderate-sized datasets


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📚 Dependencies
pip install numpy pandas matplotlib scikit-learn scipy
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
🧩 Example Output

5 clusters created

Dendrogram showing cluster relationships

Variance-based splitting decisions


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🧑‍💻 Author

Implemented from scratch by Anshu Pandey
Guided learning through practical implementation of ML algorithms.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
🌟 Next Step

Next model → DBSCAN (Density-Based Spatial Clustering) from scratch.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
