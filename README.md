# **Luxury Travel CustomerSegmentation applying a Clustering Model**
### This project develops an business solution─an automated machine learning clustering model─for the luxury travel industry, enabling customer segmentation and labeling to facilitate the subsequent establishment of a feature dashboard and formulation of strategy.
### Expected Outcome
- #### Average value of target customer increase 59%
- #### Booking volume of target customer escalate 10%
- #### Efficiency of segmenting customers enhance 75%

---

# 1. [Experimentation](Code/experimentation.ipynb)
### The experimentation exhibits the business solution for customer segmentation, including data preparation, data exploration, data modeling, model evaluation and Result Analysis.
![](image/Workflow_Experimentation.png)  

### 1.1 Data Preparation
#### Data is cleaned and RFM framework is applied for feature engineering.

### 1.2 Data Exploration
#### 1.2.1 General Exploration
![](image/PercentageByLoyaltyClub.png "Figure 1: Percentage of Customers with Different LoyaltyClub")  
![](image/Density_EquiryDate.png "Figure 2: Kernel Density Estimate Plot of EnquiryDate")  
![](image/Percentage_MetaGroupName.png "Figure 3: Percentage of Customers with Different MetaGroupName")  
![](image/Count_People_Night.png "Figure 4: Boxenplots of number of adults, child, infant and night")  

#### 1.2.2 Segment-Specific Exploration
![](image/RecencyBySegmentTitle.png "Figure 5: Boxen Plot Comparing Days among SegmentTitle")
![](image/FrequencyBySegmentTitle.png "Figure 6: Boxen Plot Comparing EnquiryN, QuoteN and BookN among SegmentTitle")
![](image/MonetaryBySegmentTitle.png/ "Figure 7: Boxen Plot Comparing CommercialValue among SegmentTitle")  

### 1.3 Data Modeling
#### 1.3.1 Outlier Detection
##### Isolation Forest is developed for outlier handling and initial customer segmentation.
##### The outliers exhibit greater recency, frequency and monetary, consequently, outliers are grouped into a segment.
![](image/RecencyByOutlier.png "Figure 8: Boxen Plot Comparing Days between Outliers and Non-outliers")
![](image/FrequencyByOutlier.png "Figure 9: Boxen Plot Comparing EquiryN, QuoteN and BookN between Outliers and Non-outliers")
![](image/MonetaryByOutlier.png "Figure 10: Boxen Plot Comparing CommercialValue between Outliers and Non-outliers")  


#### 1.3.2 Dimensionality Reduction
##### Principle Component Analysis (PCA) is conducted to reduce dimensionality.
##### Correlation matrix is deployed to evaluate whether to conduct PCA.
![](image/CorrelationMatrix_RFM.png "Figure 11: Correlation Matrix of RFM Variables")
##### Loading Matrix is constructed to select the PC for further analysis, illustrating PC1 and PC2 are significant attributes.
![](image/Loading_RFM.png "Figure 12: PCA Loading Matrix of RFM Variables")  

#### 1.3.3 Clustering Model Building
##### Five clustering models are constructed, namely KMeans, AHC, BIRCH, DBSCAN, Mean Shift.  

##### K-Means
##### The scree plot is visualized to determine the optimal number of K, manifesting that 3 and 4 are elbow points.
![](image/Screeplot_KMeans.png "Figure 13: Scree Plot of KMeans")
##### The clustering result of KMeans with K=3 and 4 are visualized.
![](image/ScatterPlot_KMeans_3.png "Figure 14: Scatter Plot of KMeans with K=3")
![](image/ScatterPlot_KMeans_4.png "Figure 15: Scatter Plot of KMeans with K=4")  

##### AHC
##### The clustering result of AHC is visualized in Figure 16.
![](image/ScatterPlot_AHC.png "Figure 16: Scatter Plot of AHC")  

##### BIRCH
##### The clustering result of BIRCH with K=3 and K=4 are visualized in Figure 17 and Figure 18, separately.
![](image/ScatterPlot_Birch_3.png "Figure 17: Scatter Plot of BIRCH with K=3")
![](image/ScatterPlot_Birch_4.png "Figure 18: Scatter Plot of BIRCH with K=4")  

##### DBSCAN
##### The clustering result of DBSCAN is visualized in Figure 19.
![](Imaimagege/ScatterPlot_DBSCAN_4.png "Figure 19: Scatter Plot of DBSCAN")  

##### Mean Shift
##### The clustering result of Mean Shift is visualized in Figure 20
![](image/ScatterPlot_MeanShift_4.png "Figure 20: Scatter Plot of MeanShift")  

### 1.4 Model Evaluation
#### 1.4.1 Effectiveness
##### According to the clustering results above, KMeans and BIRCH algorithm are capable for this clustering task.  

#### 1.4.2 Similarity
##### Internal cluster validity index (CVIs), Silhouette, Calinski-Harabasz, and Davies-Bouldin indices, are computed, standardized and labelled as “ScaleddScore” to compare cohesion and separation degree within clusters of each model, illustrated by Figure 21.
![](image/Model_EvaluationMetrics.png "Figure 21: Standardized Score of CVIs")  

#### 1.4.3 Stability
##### The clustering outcomes performed by each model on the entire dataset are regarded as the true labels. Each model is re-trained to predict on 50% and 25% subsamples of the data without setting a random seed, with the resulting clusters treated as predicted labels. Subsequently, the Rand Index of each model is computed based on true and predicted labels.
![](image/Model_Evaluation_ARI.png "Grouped Box Plot comparing ARI aming Methods")

#### 1.4.4 Summary
##### K-Means with K=4 is chosen to segment customers given its relatively high extent of effectiveness of clustering, similarity and stability.  

### 1.5 Result Analysis
#### Customers are grouped into six clusters and their features are further analyzed.
![](image/PercentageByCluster.png "Figure 22: Pie Chart exhibitting Percentage of New Segments")

##### According to Figure 23, 24, 25, Customers within cluster 4 and 3 are named as "Frequent High-valued Spenders" and "Recent High-valued Spenders", separately, given their relatively high recency, frequency, and monetary. Guests within cluster 0 is labeled as "Steady Spenders", as they exhibit moderate frequency and spending and possess fairly recent records. Cluster 1 is named as "Recent Spenders", since they placed highly recent bookings, whereas, their records are infrequent and low-valued. Clients within cluster 2 is labeled as "Lapsed Guests", given that their records are with the least recency, high infrequency, and the lowest spending. Clients within cluster 5 are marked as “Non-spenders” as they do not place any order.
![](image/RecencyByCluster.png "Figure 23: Boxen Plot comparing Recency among New Segments")
![](image/FrequencyByCluster.png "Figure 24 Boxen Plot comparing Frequency among New Segments")
![](image/MonetaryByCluster.png "Figure 25: Boxen Plot comparing Monetary among New Segments")

##### Customer features of each new segment are manifested by Figure 26, 27, 28 and 29.
![](image/HeatMap_StatusBySegment.png "Figure 26: Heat Map exhibitting Percentage of Customers in each New Segments by Record Status")
![](image/HeatMap_MetaGroupNameBySegment.png "Figure 27: Heat Map exhibitting Percentage of Customers in each New Segment by Meta Group Name")
![](image/HeatMap_ClassBySegment.png "Figure 28: Heat Map exhibitting Percentage of Customers in each New Segment by Original Segment")
![](image/FeatureDashboard.png "Dashboard exhibitting Percentage of Customer in each New Segment By Features")


---
# 2. Production
### The key stages of the production-level clustering model development are demonstrated below. 
![](image/Workflow_Production.png) 

### 2.1 [Data Collection](Code/data_collection.py)
##### SQlAlchemy and Pandas are leveraged in the step of data collection.  

### 2.2 [Data Preparation](Code/data_preparation.py)
#### 2.2.1 NumPy and Pandas are utilized in the step of data preparation for data cleaning.
#### 2.2.2 Feature engineering is conducted on the basis of RFM framework.  

### 2.3 [Data Exploration](Code/data_exploration.py)
#### 2.3.1 General Exploration
#### 2.3.2 Segment-Specific Exploration  

### 2.4 [Data Preprocessing](Code/data_preprocessing.py)
#### 2.4.1 Isolation Forest is deployed for outlier detection and initial segmentation.
#### 2.4.2 Principle Component Analysis (PCA) is employed for dimensionality reduction.  

### 2.5 [Model Training](Code/model_training.py)
#### K-Means with K=4 is selected for production.  

### 2.6 Model Deployment
#### 2.6.1 [MLflow Tracking](Code/mlflow_tracking.py)
##### MLflow is utilized to track each re-trained model.
#### 2.6.2 [Model Selection](Code/model_selection.py)
##### The model with the best performance is selected for production.  

### 2.7 [Label Production](Code/data_upload)
#### Clustering result are uploaded and customers are labeled.
##### Feature dashboard of customers can be developed for further analysis.  

### 2.8 [Main Pipeline](Code/main.py)

---
### **Contact**
#### Feel free to contact for further information.
#### **LinkedIn:** [LinkedIn Link](https://www.linkedin.com/in/chih-peng-javen-li-7b35561b9/)
