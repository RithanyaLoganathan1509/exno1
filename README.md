# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
<img width="893" height="713" alt="image" src="https://github.com/user-attachments/assets/fa1ae5fa-625d-4443-a076-42bfa41235d0" />

```
data.info()
```
<img width="425" height="410" alt="image" src="https://github.com/user-attachments/assets/56099520-1371-42f1-b85e-01d0e1815712" />

```
data.head()
```
<img width="858" height="195" alt="image" src="https://github.com/user-attachments/assets/f0b5aa4e-d8a6-42a0-95fd-3d60a17ba806" />

```
data.tail()
```
<img width="876" height="187" alt="image" src="https://github.com/user-attachments/assets/bd1e3220-f5ea-4f91-93ac-156276c2080c" />

```
data.describe()
```
<img width="795" height="285" alt="image" src="https://github.com/user-attachments/assets/a36fba3c-2564-48b3-8828-600277d7a405" />

```
data.isnull()
```
<img width="765" height="704" alt="image" src="https://github.com/user-attachments/assets/56a37b85-ff12-4e3c-941b-538c1ccfebe9" />

```
data.isnull().sum()
```
<img width="158" height="284" alt="image" src="https://github.com/user-attachments/assets/e4876cca-21c3-4366-9a41-7e665e4fdeec" />


```
data.dropna()
```
<img width="896" height="449" alt="image" src="https://github.com/user-attachments/assets/853b9fa8-cc3f-4728-89fc-27d3ebc30d19" />

```
data.fillna(method='ffill')
```
<img width="889" height="709" alt="image" src="https://github.com/user-attachments/assets/48ecd043-4809-42ec-928c-22c816931e12" />

```
data.fillna(method='bfill')
```
<img width="889" height="696" alt="image" src="https://github.com/user-attachments/assets/29ff11a2-be62-452e-b421-197d4036f6fc" />


```
data.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```
<img width="888" height="703" alt="image" src="https://github.com/user-attachments/assets/767832a6-7e8a-4cb2-b3f2-1d3dd248554d" />

```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```
<img width="543" height="395" alt="image" src="https://github.com/user-attachments/assets/8370805a-a95d-47f0-8cec-7ec98e4a61f4" />

```
ir.describe()
```
<img width="473" height="287" alt="image" src="https://github.com/user-attachments/assets/abb3a7ea-1387-4404-83b9-486de9fe8ca9" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="727" height="578" alt="image" src="https://github.com/user-attachments/assets/6075e9d5-f2b6-45a6-9183-855b31bb8f32" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="1234" height="29" alt="image" src="https://github.com/user-attachments/assets/ce34c68d-eb76-4896-8cf2-a152c95a6384" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="355" height="121" alt="image" src="https://github.com/user-attachments/assets/e2504ac1-6ea9-4b08-a16b-af58f0b8565c" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="528" height="433" alt="image" src="https://github.com/user-attachments/assets/0d153aed-1dea-4131-99fe-576592b0f825" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="706" height="576" alt="image" src="https://github.com/user-attachments/assets/1faf65e5-e7d8-4485-96d5-16b7cdf68cb6" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="487" height="259" alt="image" src="https://github.com/user-attachments/assets/d42edc48-16ab-44d2-a1e5-bb16efcf4a4a" />

```
ir1=ir[z<3]
ir1
```
<img width="549" height="433" alt="image" src="https://github.com/user-attachments/assets/c1e6bbc9-7e07-4b43-8fc6-97f982d9d47f" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
