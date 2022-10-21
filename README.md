# Cryptocurrencies

## Overview
The data I'm working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what we are looking for, I decided to use unsupervised learning. To group the cryptocurrencies, I decided on a clustering algorithm. I used data visualizations to share my findings with the board.

## Resources
* Data Source: crypto_data.csv
* Software: Python 3.9.12, Conda 22.9.0, Jupyter Notebook 6.4.12

## Results
## Deliverable 1: Preprocessing the Data for PCA

1. Preprocess the dataset in order to perform PCA in Deliverable 2.
2. Keep all the cryptocurrencies that are being traded.
3. Drop the IsTrading column.
4. Remove rows that have at least one null value.
5. Filter the crypto_df DataFrame so it only has rows where coins have been mined.
6. Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
7. Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
8. Use the get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X.
9. Use the StandardScaler fit_transform() function to standardize the features from the X DataFrame.


<img width="995" alt="dummy variable" src="https://user-images.githubusercontent.com/106033535/197095314-85babf60-88b6-4f06-bee0-96958f963651.png">



## Deliverable 2: Reducing Data Dimensions Using PCA

1. Apply PCA to reduce the dimensions to three principal components.
2. Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.


<img width="493" alt="D2 reducind data with pca" src="https://user-images.githubusercontent.com/106033535/197095606-c1d2d05a-9ba6-4134-b0bd-2bac65800015.png">



## Deliverable 3: Clustering Cryptocurrencies Using K-means

1. Ceate an elbow curve using hvPlot to find the best value for K.

<img width="739" alt="elbow curve" src="https://user-images.githubusercontent.com/106033535/197095786-005eb843-7efa-4aa3-b95e-e3e999aa062e.png">

2. Use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
3. Create a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index should be the same as the crypto_df DataFrame.
4. Add the CoinName column that holds the names of the cryptocurrencies, to the clustered_df.
5. Add another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_, 

<img width="778" alt="clustered df" src="https://user-images.githubusercontent.com/106033535/197096130-0171a178-0daf-40e6-8496-75faa4cf14c4.png">



## Deliverable 4: Visualizing Cryptocurrencies Results

1. Create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame.

<img width="807" alt="3D-Scatter with the PCA" src="https://user-images.githubusercontent.com/106033535/197096278-f53a3ca9-d117-42d8-b059-03bda2e460bb.png">


2. Add the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover. Then create a table with tradable cryptocurrencies using the hvplot.table() function.

<img width="649" alt="tradable cryptocurrencies" src="https://user-images.githubusercontent.com/106033535/197096413-5566b227-dd60-4eec-b850-f3b3cfc979e7.png">

3. Use the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one.
4. Create a new DataFrame using the clustered_df DataFrame index that contains the scaled data you created in Step 5.
5. Add the CoinName column from the clustered_df DataFrame to the new DataFrame.
6. Add the Class column from the clustered_df DataFrame to the new DataFrame.
7. Create an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and have it show the CoinName when you hover over the the data point.

<img width="762" alt="hvplot scatter plot" src="https://user-images.githubusercontent.com/106033535/197096493-c8ed9b21-3165-4468-b2e8-50e80b09bd24.png">

