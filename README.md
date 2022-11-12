# cryptocurrencies

## Analysis Purpose
___________________

The purpose of this analysis was to use unsupervised machine learning algorithms to see if we could find any patterns that we could use to recommmend a strategy for investment. As the data was not ready to move right into a prediction model we would have to clean up the data prior to any analysis.

### Data Pre-Processing
_______________________

The data we recieved to use on this analysis was good, but needed to be transformed in order for us to use it. First we would need to setup a dataframe, review the data and start making changes. On of the first items was to remove any data for coins that were no longer being traded, if we left this data in it could skew the prediction results. So that was the first update.

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/ETL_1.png)

The next step in the clean up process was to remove any algorithms that did not have information in the index. As determined before we needed only trading crypto currencies, we already transformed the dataframe to only show that so the column for "IsTrading" is no longer needed and would break the prediction model if we left it in unless we encoded the values. As this is not needed we removed the uneeded data.


![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/ETL_2.png)

Finally we wanted only values in the crypto coins mined, "totalmined" column, so we filtered out any coin values equal to zero. From there we created a dataframe with the coin name column as a reference field for after the prediction model is run to have a key of data to reference. we then dropped this column from the dataframe that was going to be used for prediction.

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/ETL_3.png)


### Standardizing Data
___________________________

Now that we had our data in a format that was useable for our needs we would need to start the process of standardizing the data.

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/standardize_data.png)

We took the fields Algorithnm and Prooftype and used the pd.get_dummies code to create numerical values for the features in this field. We then created a new data variable to house the dataframe so that we could pass it to the Standard Scaler to transform the data to a scale we could use for the prediction model.


### Reducing Data Dimensions with PCA
_____________________________________

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/PCA.png)

Here you can see that we reduced the dimensions down to three principal components. Then we created a dataframe with those principals and verified the count of the data stayed the same.


### KMeans and Clustering
__________________________

Finally we needed to determine how many clusters were best suited to create the model. To do this we would create an elbow curve with the data we just updated in the PCA process.

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/elbow_curve.png)

Based on what we saw in the curve we determined that 4 clusters would be best for this model. We then fit the model and ran the predictions.

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/Kmeans_init.png)


With that completed we could merge the dataframes into one so that we could see our data and predictions in one place. 

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/clustered_dataframe.png)


### Visaulize the data
______________________

Finally we would create visualizations to help use make sense of the predictions and further our analysis recommendations. 

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/3d_visualize.png)


![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/table.png)


with those plots done we would create a simplified dataframe by first running a minmax scaler and then finalizing a dataframe to scatter plot. 

![This is an image](https://github.com/Bren42/cryptocurrencies/blob/main/Images/Scatter_Plot_Final.png)


### Conclusion
______________

We can see from the early analysis that class 0 and class 1 have the most coins that are still actively being mined and traded. We could pick some coin choices in those classes and further drill down to make our final portfolio.


