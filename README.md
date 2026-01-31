# Identifying U.S. Counties Based on Health profile
![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat&logo=pandas&logoColor=white)
### *Developing clusters and membership probabilities across 3,100+ counties.*

<img width="857" height="547" alt="download (1)" src="https://github.com/user-attachments/assets/bd8eca6b-00a5-45b7-aaaf-fcbab331129e" />
Visualized using Principal Component Analysis(PCA) to reduce features into a 2D space and retaining 90% of the variance.


---

## Cluster Archetypes
| Cluster | Identity | Characteristics |
| :--- | :--- | :--- |
| **Cluster 0 (Red)** | **Above Average Counties** | High access to care and exercise; higher environmental stress. |
| **Cluster 1 (Blue)** | **High Intervention** | Facing systemic challenges; higher rates of poverty and barriers to care. |
| **Cluster 2 (Green)** | **National Baseline** | Representing the "average" American county metrics. |
| **Cluster 3 (Purple)** | **Top Performers** | Exceptional health outcomes; low poverty; highest education levels. |

---

## Project Overview
This project analyzes the **2025 County Health Rankings** dataset to identify patterns in public health profiles across the United States. By utilizing **K-Means Clustering** and **Principal Component Analysis (PCA)**, I grouped counties into distinct archetypes. 

A standout model for this analysis is a **Membership Probability Model**. Instead of simply labeling a county with a cluster number, this model identifies the probability a county aligns with clusters based on health categories such as "Clinical Care" or "Socioeconomic Factors."

---

## Methodology

### 1. Data Preprocessing & Cleaning
* **Imputation:** Applied **Median Imputation** to handle missing values, using mean would have caused extreme outliers too affect the data. 
* **Feature Engineering:** Created a unique `State: County` index and transformed categorical data (Water Violations) into binary numeric formats to fit the model for analysis.
* **Standardization:** Utilized `StandardScaler` from Sci-kit Learn to normalize features, ensuring that units of measurement (e.g., Physician Rates vs. Percentages) were weighted equally.

### 2. Similarity Analysis (Cosine Distance)
Before clustering, I developed a tool to find "Similar Counties" using **Cosine Similarity** to understand specific relational patterns.
* **Key Insight:** Health challenges often extend across state lines. For example, **Robeson, NC** shares higher similarity with counties in **Arkansas and Mississippi** rather than counties within the state of **North Carolina**.

### 3. Machine Learning: K-Means & PCA
* **Optimal K:** Using the **Elbow Method**, I identified **4 distinct clusters** as the point of diminishing returns for inertia.
* **Dimensionality Reduction:** I used PCA to visualize the 20+ features in a 2D space.
    * **PCA1 (Socioeconomic Axis):** Influenced by poverty, education, and fair/poor health scores.
    * **PCA2 (Clinical Access Axis):** Influenced by the density of mental health providers, doctors, and dentists.

---

## The "County Signature" (Probability Model)
To provide deeper analysis, I developed a `heatmap_for_county()` function. This calculates the probability of a county belonging to a cluster based on **Health Categories**:
* Quality of Life
* Health Behaviors
* Clinical Care
* Social & Economic Factors
* Physical Environment

**Insight:** This reveals that a county might be assigned to Cluster 1 overall, but its "Signature" might show it belongs to Cluster 0 in terms of "Clinical Care," providing a more precise roadmap for policy interventions.


---

## Technologies Used
| Category | Tools |
| :--- | :--- |
| **Language** | Python (3.10+) |
| **Data Science** | Pandas, NumPy |
| **Machine Learning** | Scikit-Learn (K-Means, PCA, StandardScaler) |
| **Visualization** | Seaborn, Matplotlib |

---
## Project Structure
```text
├── data/
│   ├── 2025_county_health_data.csv        # Raw dataset from county health rankings
├── county_health_profiles_analysis.ipynb  # Main file with ML and Clustering
├── README.md                              # Project documentation
└── requirements.txt                       # Installation for dependencies
