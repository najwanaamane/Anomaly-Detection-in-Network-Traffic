# Anomaly-Detection-in-Network-Traffic
Unsupervised and supervised techniques for detecting anomalies in network traffic using on unlabeled data


---


## Overview

This project focuses on detecting anomalies in network traffic using clustering techniques (K-means and hierarchical clustering) on unlabeled data. The KDD Cup 1999 dataset is utilized to identify abnormal traffic patterns and distinguish them from normal behavior. The approach involves:

1. Clustering the data using K-means and hierarchical clustering.
2. Using attack labels as ground truth to evaluate clustering performance.
3. Employing SVM with hierarchical clustering results to detect new anomalies.

## Project Structure

- **Dataset**: KDD Cup 1999
- **Clustering Algorithms**: K-means and hierarchical clustering
- **Evaluation**: Ground truth labels from the dataset
- **Anomaly Detection**: Support Vector Machine (SVM)

## Dataset Description

The KDD Cup 1999 dataset contains approximately 4.9 million network connections, each represented by 38 features. These features include the number of bytes sent, connection attempts, TCP errors, etc. The dataset is commonly used for network security analysis.

## Anomaly Types

The dataset includes 22 different types of attacks categorized into four main groups:

1. **Denial of Service (DOS)**: Attacks that make resources too busy or full to handle legitimate requests.
2. **User to Root (U2R)**: Attacks where an attacker gains root access from a normal user account.
3. **Remote to Local (R2L)**: Attacks where an attacker without an account exploits vulnerabilities to gain local access.
4. **Probing (PROBE)**: Attacks aimed at gathering information about the network.

## Methodology

### K-means Clustering

1. **Data Preprocessing**:
    - Only numerical features are used.
    - Data normalization is applied to standardize feature values.

2. **Implementation**:
    - The K-means algorithm is applied using various values of `k`.
    - The sum of squared errors (WSSSE) is used to evaluate the clustering performance.

3. **Choosing `k`**:
    - The best `k` is chosen based on the minimum WSSSE value.
    - Iterative approach to find optimal `k`.

4. **Anomaly Detection**:
    - Anomalies are identified by measuring the distance of data points to their nearest cluster centroids.
    - Points with distances exceeding a certain threshold are considered anomalies.

#### Results

- **Optimal `k`**: Determined through the elbow method, balancing within-cluster sum of squares.
- **Cluster Performance**: Achieved a notable separation of normal and anomalous traffic.
- **Anomaly Detection**: Detected a significant number of anomalies with high precision.

### Hierarchical Clustering

1. **Data Preprocessing**:
    - Similar to K-means, focusing on numerical features and data normalization.

2. **Implementation**:
    - Construction of a distance matrix.
    - Application of different linkage methods (single, complete, average).

3. **Evaluation**:
    - Dendrograms are used to visualize cluster formation.
    - Identifying isolated clusters or outliers for anomaly detection.

#### Results

- **Linkage Methods**: Complete linkage provided the best separation of anomalies.
- **Cluster Visualization**: Dendrograms clearly showed distinct clusters of normal and anomalous traffic.
- **Anomaly Detection**: High accuracy in identifying outliers, consistent with ground truth labels.

### Support Vector Machine (SVM)

- SVM is used to classify new data points based on the clusters formed by hierarchical clustering.
- It enhances the ability to detect previously unseen anomalies by learning from the labeled clusters.

#### Results

- **SVM Accuracy**: Achieved high accuracy in detecting new anomalies.
- **Performance Metrics**: Precision, recall, and F1-score metrics indicated robust performance in anomaly detection.
- **Generalization**: SVM effectively generalized to new, unseen network traffic, improving overall detection rates.

## Conclusion

This project demonstrates the effectiveness of combining K-means and hierarchical clustering for initial anomaly detection, followed by SVM for enhanced detection of new anomalies. The approach improves network security by accurately identifying and classifying abnormal traffic patterns.

## Running the Notebooks

### Prerequisites

Ensure you have the required libraries installed. You can install them using:

```bash
pip install pandas numpy scikit-learn scipy matplotlib seaborn
```

### Notebooks

1. **Hierarchical Clustering and SVM**:
    - Load the notebook `hierarchicalClustering_to_SVM.ipynb`.
    - Run the cells sequentially to perform hierarchical clustering, evaluate with ground truth labels, and train an SVM classifier.

2. **K-means Clustering**:
    - Load the notebook `Anomaly Detection in Network Traffic with K-means clustering.ipynb`.
    - Run the cells sequentially to perform anomaly detection using K-means clustering and evaluate with ground truth labels.

## Data

Both notebooks use the KDD Cup 1999 dataset. Ensure you have the dataset (`kddcup.data_10_percent.csv`) in the same directory as the notebooks or provide the correct path to the dataset in the data loading sections.

## Conclusion

These notebooks provide a comprehensive guide to performing hierarchical clustering and K-means clustering for anomaly detection in network traffic data. They include data preprocessing steps, model training, evaluation with ground truth labels, and result visualization to help you understand and apply these techniques to your data.


---

