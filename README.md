# Faulty-wafer-detection

GENERAL INFO - Wafer is a semi conductor device which is made by a combination of various sensors.

PROBLEM STATEMENT - To find a faulty wafer by analysing the values produced by the sensors.

ARCHITECTURE OF THE PROJECT - 

1. Data Signature Aggrement(DSA) - Clinet will agree on the structure of the data that he is going to provide while training and for further prediction of the data
                                   i.e., structure of the file, data typres of each column and no of columns.
                                   
2. Based on the DSA, validation of the data set will be done, this is done to maintain a consistency in the system and also helps with security issues.
 
 DATA PREPROCESSING - 

3. The columns with zero standard deviation were dropped and the null values were handled using KNN imputer.

MODEL CREATION  - 

4.  Applying a single machine learning algorithm on the whole data might not provide a model with greater accuracy, there might be various factors on which the sensors change their behavior. 
So to avoid that situation we decided to cluster the data using K-Means++ clustering algorithm and using elbow - knee method to find the optimal value of k.

5. After forming clusters, various supervised machine learning algorithms were applied on each cluster and the top 2 algorithms with highest AUC score were selected for the production.

6. In production these two algorithms were hyptertuned using GridsearchCV then the model with their best parameters which produced the highest AUC score was selected.

7. When the new data is given to the model to predict, the model will first assign a cluster number for each wafer, then depending upon the model selected for that cluster prediction will take place.

 DEPLOYMENT - 
 
8. This application was deployed on GCP.
