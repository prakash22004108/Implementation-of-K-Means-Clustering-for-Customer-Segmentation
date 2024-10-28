# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
STEP 1. Start
STEP 2. Data Preparation: Load and explore customer data.
STEP 3. Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
STEP 4. Apply K Means Clustering: Perform clustering on customer data.
STEP 5. Visualize Segmented Customers: Plot clustered data to visualize customer segments.
STEP 6. End

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: PRAKASH R
RegisterNumber: 212222240074
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []  # Within-Cluster Sum of Square
# It is the sum of squared distance between each point & the centroid in a cluster.
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")

km = KMeans(n_clusters=5)
km.fit(data.iloc[:, 3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data['cluster'] = y_pred
o = data[data['cluster'] == 0]
p = data[data['cluster'] == 1]
q = data[data['cluster'] == 2]
r = data[data['cluster'] == 3]
s = data[data['cluster'] == 4]

plt.scatter(o['Annual Income (k$)'], o['Spending Score (1-100)'], c="red", label="cluster0")
plt.scatter(p['Annual Income (k$)'], p['Spending Score (1-100)'], c="blue", label="cluster1")
plt.scatter(q['Annual Income (k$)'], q['Spending Score (1-100)'], c="green", label="cluster2")
plt.scatter(r['Annual Income (k$)'], r['Spending Score (1-100)'], c="orange", label="cluster3")
plt.scatter(s['Annual Income (k$)'], s['Spending Score (1-100)'], c="magenta", label="cluster4")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.legend()
plt.title("Customer Segments")

```

## Output:
![image](https://github.com/user-attachments/assets/7c56fbc0-57f1-4743-a21f-affc49011506)
![image](https://github.com/user-attachments/assets/4ab9c23a-f61b-4884-a07d-b5d36a03ca4f)
![image](https://github.com/user-attachments/assets/f0a2239f-c949-49c9-b38a-6fe1f7c75c2a)
![image](https://github.com/user-attachments/assets/a8786161-62ad-47d8-ba76-4f0d979592e7)




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
