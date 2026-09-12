# Mall Customer Segmentation Using K-Means Clustering
## Executive Summary
This project **applies K-Means clustering** to segment mall customers into distinct groups based on their behavioural characteristics. Two clustering models were developed: an initial model based on `annual income` and `spending score`, and an extended model incorporating `age` as a third dimension. The resulting segments are profiled and interpreted to support the development of targeted marketing strategies.
![3D scatter plot of customer clusters based on age, annual income, and spending score](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/age_income_spending_clusters_3d.png)
## Business Problem
Customers with different income and spending habits usually need different marketing approaches. The marketing team needs to answer questions like:
- Which customers are the most valuable to the business?
- Which customers would respond well to premium offers?
- Which customers require a different marketing approach altogether?
- Does age meaningfully change how customers should be grouped?

Rather than applying a single marketing strategy across the entire customer base, segmentation allows a business to group customers with similar characteristics and design targeted campaigns accordingly. This can improve customer retention, increase the effectiveness of promotional spend, and support more informed business decisions.

In this project, K-Means clustering is used to identify meaningful customer segments based on `annual income`, `spending score`, and `age`.
## Dataset
This project uses the publicly available Mall Customer Segmentation Dataset from Kaggle.

For licensing reasons, the dataset is not included in this repository. Please download it from the link below and place `Mall_Customers.csv` in the project's root directory, or update the file path in the notebook accordingly.

Dataset: https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

The dataset contains information on 200 mall customers.
## Project Workflow
```
Load Dataset
      ↓
Explore the Data
      ↓
Data Cleaning & Preparation
      ↓
Exploratory Data Analysis
      ↓
Determine Optimal Number of Clusters
      ↓
Train K-Means Model (Income & Spending Score)
      ↓
Train K-Means Model (Age, Income & Spending Score)
      ↓
Profile and Interpret Customer Segments
      ↓
Generate Business Recommendations
```
## Exploratory Data Analysis
Before building the clustering models, the dataset was explored to better understand customer characteristics and to confirm that it was suitable for analysis. The exploration included:
1. Checking for missing values and duplicate records.
2. Reviewing the distribution of Age, Annual Income, and Spending Score.
3. Comparing these distributions across genders.
4. Examining the relationship between Annual Income and Spending Score.
5. Reviewing correlation between the numeric variables.
No missing values or duplicate records were found. The `CustomerID` column was dropped, as it does not contribute to the clustering process.
### Gender Distribution
The dataset is slightly skewed toward female customers, though not to a degree that raises concern for the analysis.
![Bar chart showing the number of male and female customers in the dataset](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/gender_distribution.png)
### Income and Spending Score
Plotting annual income against spending score reveals several naturally occurring customer groups, visible even prior to applying any clustering algorithm. This pattern was the primary motivation for selecting K-Means as the modelling approach.
![Scatter plot of annual income versus spending score showing natural groupings in the data](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/income_spending_scatter.png)
## Building the Model
### Income & Spending Score (k = 5)
The optimal number of clusters was determined using the **Elbow Method**. The resulting curve flattens noticeably at k = 5, indicating that five clusters provide an appropriate balance between model simplicity and explanatory power.
A K-Means model was then trained using `Annual Income` and `Spending Score` as input features, assigning each customer to one of five clusters.
![Scatter plot of customer clusters based on annual income and spending score, with cluster centers marked](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/income_spending_clusters.png)
A crosstab of cluster assignment against gender was reviewed to check whether any segment was disproportionately associated with a particular gender. No substantial imbalance was observed, suggesting that these clusters are driven primarily by income and spending behaviour rather than gender.
### Age, Income & Spending Score (k = 6)
To assess whether age meaningfully refines the segmentation, a second model was trained using `Age`, `Annual Income`, and `Spending Score` together. The Elbow Method was applied again, this time indicating an optimal value of k = 6.
A K-Means model was trained on all three features and visualised using a three-dimensional scatter plot.
![3D scatter plot of customer clusters based on age, annual income, and spending score](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/age_income_spending_clusters_3d.png)
The inclusion of age introduces additional separation within the data, particularly between younger, high-spending customers and older customers with comparable income but lower spending levels.
## Results
The mean values of Age, Annual Income, and Spending Score were calculated for each of the six clusters to profile their characteristics. These profiles were then used to assign each segment a descriptive, behaviour-based name.
![Table showing average age, annual income, and spending score for each named customer segment](https://github.com/nkorlov-data/Mall-Customer-Segmentation-Clustering/blob/main/images/cluster_profiles_table.png)
A normalised crosstab (percentage by row) was used to compare segment composition across genders. Minor variation was observed, but not to an extent that would justify treating gender as a primary driver of segmentation.
## Business Insights & Recommendations
### VIP Customers & Young Professionals
These segments combine high income with high spending and represent the mall's most commercially valuable customers.  
**Potential actions:**
- VIP loyalty programmes
- Early access to new collections
- Premium product recommendations
### Trend Seekers
Despite comparatively lower income, this segment spends actively, suggesting strong engagement but potential price sensitivity.  
**Potential actions:**
- Value bundles and instalment options
- Rewards or cashback programmes
- Trend-focused promotional campaigns
### Prudent Investors
This segment has high income but low spending, indicating unrealised purchasing potential.
**Potential actions:**
- Personalised promotions
- Customer surveys to identify purchasing barriers
- Exclusive, income-appropriate offers
### Steady Customers & Classic Shoppers
These segments represent a stable but lower-priority portion of the customer base.
**Potential actions:**
- Seasonal promotions
- Basic loyalty incentives
- Periodic re-engagement campaigns

These recommendations should be treated as a starting point for further analysis. **Given the relatively small sample size of 200 customers**, the identified segments would benefit from validation against actual purchase history before being used to inform significant business decisions.
## Built With
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
## How to Run the Project
Clone the repository:
```
git clone https://github.com/<your-username>/mall-customer-segmentation.git
```
Navigate into the project folder:
```
cd mall-customer-segmentation
```
Install the required packages:
```
pip install -r requirements.txt
```
Run the notebook:
```
jupyter notebook MallCustomerClustering.ipynb
```
## Future Improvements
- Compare K-Means with alternative clustering approaches.
- Incorporate additional customer features, such as purchase frequency or product category, where available.
- Validate the identified segments against real campaign performance data.
