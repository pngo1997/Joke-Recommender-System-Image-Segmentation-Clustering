# 🏗️ Joke Recommender & Image Segmentation Clustering  

## 📜 Overview  
This project implements two distinct tasks:  

1. **Joke Recommender System**  
   - Uses **item-based collaborative filtering** to predict user ratings of jokes from the **Jester Online Joke Recommender System** dataset.  
   - Compares **standard item-based CF** with **SVD-based item-based CF** using **Mean Absolute Error (MAE)** as an evaluation metric.  
   - Implements a function to find the **most similar jokes** based on user ratings.  

2. **Image Segmentation Clustering**  
   - Applies **K-Means clustering** to an **image segmentation dataset**.  
   - Compares clustering results **before and after PCA dimensionality reduction**.  
   - Evaluates clustering performance using **Completeness and Homogeneity scores**.  

## 🎯 Problem Explanation  

### **Joke Recommender System**  
The dataset consists of:  
- **`modified_jester_data.csv`** – A **1000 × 100** matrix where each row represents a **user's joke ratings**. Ratings are normalized to a **20-point scale (1 to 21)**, with **0 indicating missing ratings**.  
- **`jokes.csv`** – A mapping of **joke IDs to joke text**.  

The main objectives are:  
1. Load and preprocess the joke rating data.  
2. Implement a function to compute **Mean Absolute Error (MAE)** for evaluating prediction accuracy.  
3. Compare **standard item-based CF** vs. **SVD-based CF**.  
4. Implement a function to **find the top-k most similar jokes** based on user ratings.  
5. Develop a **model-based item-based recommender** using **Cosine Similarity or Pearson Correlation**.  

### **Image Segmentation Clustering**  
The main objectives are:  
1. **Preprocess the dataset** (Min-Max normalization to **[0,1] range**).  
2. **Cluster images using K-Means** (`K=7`) and evaluate cluster assignments using **Completeness & Homogeneity scores**.  
3. **Perform PCA** to determine the number of principal components that retain **at least 95% variance**.  
4. **Cluster again using K-Means on the PCA-transformed data** and evaluate improvements in clustering quality.  
5. **Compare and interpret** clustering results before and after PCA.  

## 🛠️ Implementation Details  

### **1. Joke Recommender System**  
- **Data Loading**:  
  - Loads joke ratings matrix into a **NumPy array**.  
  - Loads joke text into a **dictionary mapping joke IDs to text**.  
- **Evaluation Function (`test()`)**:  
  - Iterates over all users and evaluates prediction accuracy using **20% test-ratio**.  
  - Computes **Mean Absolute Error (MAE)** for:  
    - **Standard Item-Based CF (`standEst`)**  
    - **SVD-Based Item-Based CF (`svdEst`)**  
- **Finding Similar Jokes (`print_most_similar_jokes()`)**:  
  - Takes a **query joke ID** and finds the **k most similar jokes** based on user ratings.  
  - Uses **Cosine Similarity** or **Pearson Correlation** as a similarity metric.  
- **Model-Based Item-Based Recommender**:  
  - Precomputes **item-item similarities** using **Cosine Similarity or Pearson Correlation**.  
  - Predicts ratings using the **weighted average of k most similar items**.  
  - **Cross-validates performance across different values of k**.  

### **2. Image Segmentation Clustering**  
- **Preprocessing**:  
  - Loads **image feature matrix** and **class labels**.  
  - Applies **Min-Max normalization** to scale features between **0 and 1**.  
- **K-Means Clustering (Without PCA)**:  
  - Uses **Euclidean distance** as the similarity measure.  
  - Computes **Completeness & Homogeneity scores**.  
- **Principal Component Analysis (PCA)**:  
  - Determines the number of **principal components (PCs)** required to **retain 95% variance**.  
  - Projects data into the lower-dimensional **PC space**.  
- **K-Means Clustering (With PCA)**:  
  - Runs K-Means clustering **again on PCA-transformed data**.  
  - Computes **Completeness & Homogeneity scores** to compare improvements.  
- **Comparison & Discussion**:  
  - Analyzes the **difference in clustering performance before & after PCA**.  

## 🚀 Technologies Used  
- **Python** (for recommender system & clustering).  
- **NumPy & Pandas** (for data manipulation).  
- **Scikit-learn** (for clustering, PCA, and evaluation metrics).  
- **Matplotlib & Seaborn** (for visualization).  
