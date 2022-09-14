# Cryptocurrencies Analysis

## Purpose

The purpose of this analysis is to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

## Overview

•	Preprocess data for unsupervised learning.

•	Reducing Data Dimensions Using PCA.

•	Cluster data using K-means algorithm.

•	Determine the best number of centroids for K-means using the elbow curve.

•	Use PCA to limit features and speed up the model.

* Visualizing Cryptocurrencies Results.

## Preprocessing the data

#### The data is loaded from a CSV file. The unprocessed has null values, unnamed columns that need to be named, as well as filtering that need to be applied to preform PCA.

![crypto_df_raw](https://user-images.githubusercontent.com/103263248/190247774-2ea101ea-7b27-47fb-ab2e-f178b4591e5a.png)

#### Only the cryptocurrencies that are being traded and have a working algorithm are kept.

![working_algortihm_crypto_df](https://user-images.githubusercontent.com/103263248/190248126-325de981-5004-4b0e-a655-63677b352bd6.png)

#### The ‘IsTrading’ column is dropped.

![IsTrading_column_dropped](https://user-images.githubusercontent.com/103263248/190248163-e4ac8f2b-1695-43bb-b136-aa06e8174c14.png)

#### The DataFrame is checked and cleaned of null values and duplicates.

![check_null](https://user-images.githubusercontent.com/103263248/190248341-39f180b0-4c72-40ea-a975-df36e52ec59f.png)

#### After using '.dropna()'

![dropna_null](https://user-images.githubusercontent.com/103263248/190248366-b9adf32b-d824-4b9d-bf9e-3e389e048dd5.png)

![check_for_duplicate](https://user-images.githubusercontent.com/103263248/190248391-37ca5ac4-f94b-4897-878b-4663dd2dd6bf.png)

#### Only the rows where coins are being mined with a value greater than zero are kept.

![TCM_morethan_one](https://user-images.githubusercontent.com/103263248/190248451-a25541b0-37b9-405e-a057-388e8a603927.png)

#### Renamed the ‘Unnamed: 0’ column to ‘ ‘ and set as the index.

![clean_crypto](https://user-images.githubusercontent.com/103263248/190248783-d9e0e616-5a41-4424-bb76-496ef5eb1299.png)

#### A new DataFrame that holds the cryptocurrencies names is mane and the ‘CoinName’ column is dropped from the Crypto DataFrame.

![crypto_name_df](https://user-images.githubusercontent.com/103263248/190248827-830ab7a7-1ab9-4a24-b477-6c9d453c4d03.png)

#### Crypto DataFrame without the 'CoinNames' column.

![crypto_df_na_coinname](https://user-images.githubusercontent.com/103263248/190248856-f8531034-7ed1-4213-ba55-e0dde37c4961.png)

#### Pandas ‘get_dummies()’ is used to create variables for text features.

![X](https://user-images.githubusercontent.com/103263248/190248888-61ba8579-a74f-4be2-b653-08af6b4d73cf.png)

#### The final step in preprocessing the data is to standardize the data with StrandardScaler().

![x_scaled](https://user-images.githubusercontent.com/103263248/190248919-a3b7b1c7-b8d8-4649-acc0-aa5d7472dcd2.png)

## Reducing Data Dimensions Using PCA

#### PCA is used to reduce dimension to three principal components, and a new PCS DataFrame is created with them.

![pca_df](https://user-images.githubusercontent.com/103263248/190249016-8a5475c4-09d6-49af-911c-8bfda3cf8dda.png)

## Clustering Cryptocurrencies Using K-Means.

#### An Elbow Cure is created to find the best value for K. 

![elbow_curve](https://user-images.githubusercontent.com/103263248/190249100-bf32c3bd-ca0c-41cc-959b-808cc2a508c7.png)

#### Predictions are run after initializing the KMeans model.

![predictions](https://user-images.githubusercontent.com/103263248/190249114-021b4414-e97f-49de-a779-40ab78c05615.png)

#### A new Clustered DataFrame is created and data from the Crypto DataFrame, and PCS DataFrame, including the predictions held in the 'Class' coulumn, are concatenated on the same columns.

![clustered_df](https://user-images.githubusercontent.com/103263248/190249141-631e99a1-ea06-44f5-961f-10ce3af232ac.png)

## Visualizing Cryptocurrencies

#### A 3D Scatter Plot is used to visualize the PCA data and clusters with popup on hover to see crypto data information.

![cluster_scatter_popup](https://user-images.githubusercontent.com/103263248/190249194-6d6b9dbc-5ee9-4f06-ac41-21f6148cf100.png)

#### A table with tradable cryptocurrencies is created with the option to sort and select the data.

![hvplot_table_tradeable_crypto](https://user-images.githubusercontent.com/103263248/190249364-96b8b39d-b42b-44ea-ae7e-8d13528dd475.png)

#### The total number of tradable cryptocurrencies is found.

![count_tradable_crypto](https://user-images.githubusercontent.com/103263248/190249414-76094483-ae33-4b9b-9045-5e1660a57dff.png)

#### The data is scaled with MinMaxScaler().fir_transform and a new Plot DataFrame is created to hold the scaled data with the Clustered DataFrame index.

![plot_df](https://user-images.githubusercontent.com/103263248/190249497-871a46c5-77e2-46c9-a3d4-47fd50208de8.png)

#### A scatter plot is created using hvplot.scatter using x=”TotalCoinsMined” and y=”TotalCoinSupply” with popups on hover to display data information.

![hvplot_scatter_TCM_TCS_popup](https://user-images.githubusercontent.com/103263248/190249518-bd442245-d37e-4d2f-9550-e5559c4498db.png)
