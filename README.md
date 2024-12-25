# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.  Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.
    

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by:MITHUN S
RegisterNumber: 24901037 
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("C:/Users/LENOVO/Downloads/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = [] #Within-Cluster Sum of Square
#It is the sum of squared distance between each point & the centroid in a cluster.
for i in range(1,11):
kmeans = KMeans(n_clusters = i,init = "k-means++")
kmeans.fit(data.iloc[:,3:])
wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluste
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="clu
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="clust
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="clu
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="c
plt.legend()
plt.title("Customer Segments")
```

## Output:

![K Means Clustering for Customer Segmentation](![Screenshot 2024-12-25 234803](https://github.com/user-attachments/assets/5d4b05ea-6b79-4fd8-9770-cad6f55f6990)
)

![image](https://github.com/user-attachments/assets/fc9d8cca-b985-4a82-9fb0-ce9a3983ff8e)

![image](https://github.com/user-attachments/assets/d3d554fc-1ff4-4534-b7cc-7a56a9383551)

![image](https://github.com/user-attachments/assets/d4da3452-2d66-42ca-8286-13e6982dcf17)

![image](https://github.com/user-attachments/assets/51e7be49-a246-4a3c-9e7b-fd30fbc1d22b)





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
