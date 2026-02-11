### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07.02.26
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
# Visitor segmentation based on characteristics
# read the data
import pandas as pd
df=pd.read_csv(r"C:\Users\admin\Downloads\clustervisitor (1).csv")
df
cluster = {"Young": (df['Age'] <= 30),"Middle": ((df['Age'] > 30) & (df['Age'] <= 50)),"Old": (df['Age'] > 50)}

count=[]
for group,condition in cluster.items():
    visitors=df[condition]
    count.append(len(visitors))
    print(f"The visitors on {group} age are")
    print(visitors)
    print("count=",len(visitors))

import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

```
### Output:
<img width="431" height="216" alt="image" src="https://github.com/user-attachments/assets/1b6d1342-9dcf-4a91-ab2f-c806cc7cc3a4" />
<img width="449" height="440" alt="image" src="https://github.com/user-attachments/assets/7f7b1d98-b147-4dd5-9b42-b285123db0e1" />
<img width="378" height="110" alt="image" src="https://github.com/user-attachments/assets/b6f46276-c916-4655-a830-746ef4fe7c65" />
<img width="517" height="409" alt="image" src="https://github.com/user-attachments/assets/4f8df786-e4a3-4bc1-8763-384a31bf9553" />





### Visualization:
```python
# Create a list to store counts of visitors in each age group
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3

import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()
```
### Output:
<img width="333" height="826" alt="image" src="https://github.com/user-attachments/assets/dc30e989-f92a-4f6e-afa3-a75e8c6ffcca" />

<img width="574" height="431" alt="image" src="https://github.com/user-attachments/assets/516a2c6a-b07d-40c4-ab2b-79d9b5d014bc" />



### Result:
Implementation of Cluster and Visitor Segmentation for Navigation patterns hasbeen done successfully.
