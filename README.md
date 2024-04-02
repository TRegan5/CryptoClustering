# Crypto Clustering - Module 19 Challenge

## Repository of code, resource file, and readme 
- https://github.com/TRegan5/CryptoClustering

## Prepare the Data
Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.
Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.



## Find the Best Value for k Using the Original Scaled DataFrame
Use the elbow method to find the best value for k:

- Create a list with the number of k values from 1 to 11.
- Create an empty list to store the inertia values.
- Create a for loop to compute the inertia with each possible value of k.
- Create a dictionary with the data to plot the elbow curve.
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

**What is the best value for k?**
`The best value for k is 4`

##  Cluster Cryptocurrencies with K-means Using the Original Scaled Data
Cluster the cryptocurrencies for the best value for k on the original scaled data:

### Initialize the K-means model with the best value for k.
- Fit the K-means model using the original scaled DataFrame.
- Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
- Create a copy of the original data and add a new column with the predicted clusters.
- Create a scatter plot using hvPlot as follows:
- Set the x-axis as "PC1" and the y-axis as "PC2".
- Color the graph points with the labels found using K-means.
- Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.


### Optimize Clusters with Principal Component Analysis
- Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.

- Retrieve the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:

**What is the total explained variance of the three principal components?**
`Total explained variance of the three principal components is 0.895031657030984`

- Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

## Find the Best Value for k Using the PCA Data
Use the elbow method on the PCA data to find the best value for k:
- Create a list with the number of k-values from 1 to 11.
- Create an empty list to store the inertia values.
- Create a for loop to compute the inertia with each possible value of k.
- Create a dictionary with the data to plot the Elbow curve.
- Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

**What is the best value for k when using the PCA data?
Does it differ from the best k value found using the original data?**
`The best k value found using the PCA data was the same as using the original data: k = 4.`

## Cluster Cryptocurrencies with K-means Using the PCA Data
Cluster the cryptocurrencies for the best value for k on the PCA data:

- Initialize the K-means model with the best value for k.
- Fit the K-means model using the PCA data.
- Predict the clusters to group the cryptocurrencies using the PCA data.
- Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
- Create a scatter plot using hvPlot as follows:
    - Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
    - Color the graph points with the labels found using K-means.
    - Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

**What is the impact of using fewer features to cluster the data using K-Means?** `At first glance, the plotted cluster analysis results do not appear all that different: each method showing two main clusters containing a majority of the data (clusters 0 and 2) and two additional clusters (clusters 1 and 3) with seemingly one outlier each. However, comparing the graphical ranges of the plots reveals a tighter concentration of the data in the first two clusters using PCA -- expected via dimensional-reduction -- than in the original scaled dataset. Secondly, PCA more greatly separates outliers from the two main clusters, with cluster 1 completely removed from the clusters 0 and 2, while the scaled clustering plotted that outlier amongst the datapoints for clusters 0 and 2. Finally, the PCA plot shows at least as distinct a separation of clusters as the scaled data, meaning the use of fewer features in PCA produces a very similar performance as the original model.`