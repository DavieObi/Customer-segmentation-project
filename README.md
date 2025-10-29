# 🛍️ Customer Segmentation using Unsupervised Learning

## 📘 Project Overview
This project focuses on **customer segmentation** using the **Online Retail dataset**. The goal is to analyze customer purchasing behavior, clean and preprocess the dataset, and apply clustering techniques to group customers with similar characteristics. This segmentation helps businesses understand their customer base, tailor marketing strategies, and improve overall customer satisfaction.

The project involves:
- Data loading, cleaning, and preprocessing  
- Encoding categorical variables  
- Normalization and exploratory data analysis (EDA)  
- Feature visualization and correlation analysis  
- Dimensionality reduction using PCA  
- Clustering using K-Means and Mean Shift algorithms  
- Evaluation of clustering performance and visual interpretation of results  

---

## 💡 Problem Statement
Retail businesses often struggle to identify and understand distinct groups of customers based on their purchasing patterns. Without proper segmentation, marketing efforts can be inefficient and generic, leading to wasted resources and missed opportunities for customer retention.

The problem, therefore, is:  
> How can we use data-driven techniques to segment customers into meaningful groups based on their purchasing behaviors and transaction details?

---

## 🎯 Project Objectives
1. To analyze and preprocess the Online Retail dataset for consistency and reliability.  
2. To encode categorical variables and normalize data for effective clustering.  
3. To explore data visually and understand feature relationships using EDA and PCA.  
4. To apply clustering algorithms (K-Means and Mean Shift) to identify customer groups.  
5. To evaluate clustering performance using appropriate metrics (Silhouette, Calinski-Harabasz, Davies-Bouldin).  
6. To visualize and interpret clusters to gain insights that can guide business strategies.  

---

## 🧹 Loading and Cleaning the Dataset
### Loading the Dataset
In this section, we load the dataset from an Excel file and perform some basic data cleaning steps.

**Loading the Dataset:**  
We use `pd.read_excel` to read the Excel file located at the specified path and load it into a pandas DataFrame named `original_df`.

**Dropping Missing Values:**  
We use the `dropna` method to remove any rows with missing values from the DataFrame. The `inplace=True` parameter ensures that the changes are made directly to the original DataFrame without creating a copy.

**Resetting the Index:**  
We reset the index of the DataFrame using the `reset_index` method. The `inplace=True` parameter ensures that the changes are made directly to the original DataFrame. The `drop=True` parameter ensures that the old index is not added as a new column.

**Displaying the DataFrame:**  
Finally, we display the cleaned DataFrame to inspect the data.

---

## 🔠 Encoding Categorical Features
In this section, we encode categorical features in the dataset using `LabelEncoder`.

**Initializing LabelEncoder:**  
We create an instance of `LabelEncoder` from the `sklearn.preprocessing` module. This encoder converts categorical labels into numerical values.

**Defining Categorical Columns:**  
We define a list of columns that contain categorical data which need to be encoded.

**Encoding Each Categorical Column:**  
We use a for loop to iterate over each column in the list of categorical variables. For each column, we use the `fit_transform` method of `LabelEncoder` to convert the categorical values into numerical values. The `astype(str)` method ensures that all values are treated as strings before encoding.

**Displaying the DataFrame:**  
Finally, we display the DataFrame to inspect the encoded data.

---

## 🧽 Data Cleaning and Preprocessing
In this section, we perform additional data cleaning steps to prepare the dataset for analysis.

**Dropping the 'InvoiceDate' Column:**  
We remove the 'InvoiceDate' column from the DataFrame as it may not be needed for further analysis. The `axis=1` parameter specifies that we are dropping a column, and `inplace=True` ensures that the changes are made directly to the original DataFrame.

**Identifying Rows with Negative Quantities:**  
We identify rows where the 'Quantity' column has negative values, which may indicate errors or returns. We store the indices of these rows in a variable.

**Dropping Rows with Negative Quantities:**  
We remove the rows with negative quantities from the DataFrame. The `axis=0` parameter specifies that we are dropping rows, and `inplace=True` ensures that the changes are made directly to the original DataFrame.

**Resetting the Index:**  
We reset the index of the DataFrame using the `reset_index` method. The `drop=True` parameter ensures that the old index is not added as a new column, and `inplace=True` ensures that the changes are made directly to the original DataFrame.

**Displaying the DataFrame:**  
Finally, we display the cleaned DataFrame to inspect the data.

---

## ⚖️ Normalizing the Data and Descriptive Statistics
In this section, we normalize the data and compute descriptive statistics.  

**Normalizing the Data:**  
We use `MinMaxScaler` to scale the features to a specified range (1 to 5 in this case). Normalization ensures that all features are on a similar scale, which can improve the performance of machine learning algorithms.

We create an instance of `MinMaxScaler` with the specified feature range, fit it to the data, and transform the features. The transformed array is converted back into a pandas DataFrame with the original column names.

**Descriptive Statistics:**  
We compute descriptive statistics for the normalized DataFrame. This includes measures such as mean, standard deviation, minimum, maximum, and quartiles for each feature.  
Descriptive statistics provide a summary of the central tendency, dispersion, and shape of the distribution of the data.

---

## 📊 Data Visualization and Analysis
In this section, we perform various visualizations and analyses to understand the distribution and relationships of the features in the dataset.

**Histogram of All Features:**  
We create histograms for all features in the DataFrame to visualize their distributions.  

**Pairplot of a Sample of the Data:**  
We create a pairplot of a random sample of 1000 rows from the DataFrame to visualize the relationships between pairs of features.

**Correlation Heatmap:**  
We compute the correlation matrix of the DataFrame and create a heatmap with annotations to visualize feature correlations.

**Principal Component Analysis (PCA):**  
We perform PCA with 2 components to reduce dimensionality and visualize the data in a 2D space.

**Distribution of Each Feature:**  
We create histograms with kernel density estimates (KDE) to visualize feature distributions.

**Boxplot of Each Feature:**  
We create boxplots for each feature to visualize the distribution and identify any outliers.

---

## 🤖 Clustering and Evaluation
In this section, we perform **K-Means clustering** on the dataset, evaluate the clustering performance using various metrics, and visualize the results.  

**Determine the Optimal Number of Clusters:**  
We use the Elbow method to find the optimal number of clusters by plotting the within-cluster sum of squares (WCSS) for different values of K. The "elbow" point in the plot indicates the optimal number of clusters.

**Evaluate Clustering Performance:**  
We evaluate the clustering performance using three metrics:
- Silhouette Score  
- Calinski-Harabasz Score  
- Davies-Bouldin Score  

**Visualize Clustering Results:**  
We visualize the clustering results using scatter plots to see how the data points are grouped into different clusters.

**Principal Component Analysis (PCA):**  
We perform PCA to reduce the dimensionality of the data and visualize the clusters in a lower-dimensional space.

**Final Clustering with Optimal K:**  
We perform K-Means clustering with the optimal number of clusters (K=5 in this case) and visualize the final clustering results. We also add the cluster labels to the DataFrame for further analysis.

---

## 🌐 Mean Shift Clustering and Visualization
In this section, we perform **Mean Shift clustering** on a sample of the dataset and visualize the results.

**Sampling the Data:**  
We take a random sample of 5000 rows from the normalized DataFrame to make the clustering process more efficient and manageable.

**Estimating Bandwidth:**  
We estimate the bandwidth parameter for the Mean Shift algorithm using the `estimate_bandwidth` function. The bandwidth determines the size of the region to search for the mode (highest density) of the data.

**Performing Mean Shift Clustering:**  
We perform Mean Shift clustering on the sampled data using the estimated bandwidth. Mean Shift is a non-parametric clustering algorithm that does not require specifying the number of clusters in advance. It works by shifting data points towards the mode of the data.

**Adding Cluster Labels to the DataFrame:**  
We add the cluster labels obtained from the Mean Shift algorithm as a new column in the sampled DataFrame. This allows us to identify which cluster each data point belongs to.

**Visualizing Clusters and Centroids:**  
We create a scatter plot to visualize the clusters and their centroids. Each cluster is represented by a different color, and the centroids are marked with black 'x' symbols.

By following these steps, we can effectively cluster the sampled dataset using Mean Shift, evaluate the clustering performance, and visualize the results to gain valuable insights into the data.



## 🧩 Conclusion
This project successfully demonstrates how unsupervised learning techniques can be applied to segment customers based on their purchasing behavior. By performing data cleaning, preprocessing, normalization, and clustering, we derived meaningful customer groups that provide valuable business insights.

The **K-Means** and **Mean Shift** clustering algorithms helped identify distinct customer segments, each with unique purchasing patterns. These clusters can guide strategic decision-making in areas such as marketing, product recommendation, and customer retention.

**Key Takeaways:**
- Data preprocessing and normalization significantly improve clustering performance.  
- PCA effectively reduces dimensionality for easier visualization without losing critical information.  
- Clustering enables businesses to identify high-value customers, frequent buyers, and seasonal shoppers.  
- Insights from segmentation can be used to design targeted promotions, optimize inventory, and enhance customer experience.

Overall, this project highlights the power of data-driven segmentation in helping retail businesses understand their customers better and make informed, personalized marketing decisions.
