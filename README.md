## NAME : Afifa A
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
lab=pd.read_csv("/content/SAMPLEIDS.csv")
lab.head()
```
![image](https://github.com/user-attachments/assets/8d70d4bb-29f0-444a-a2c0-454764fdbc78)

```
lab.head(5)
```
![image](https://github.com/user-attachments/assets/9b56e68a-02a8-423e-a7d3-fb9692bc8eff)

```
lab.tail(5)
```
![image](https://github.com/user-attachments/assets/b615e582-dcfd-4598-93d8-8154e0a1aa18)

```
lab.isnull().sum()
```
![image](https://github.com/user-attachments/assets/68ccb6ef-2dde-4341-a160-393afc6c5cc8)

```
lab.isnull().any()
```
![image](https://github.com/user-attachments/assets/a9f9425e-92a1-44ea-bcaa-82621f3834ff)

```
lab.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/a7529f59-0226-4915-ab5b-73b30e6ed400)

```
lab.fillna(50)
```
![image](https://github.com/user-attachments/assets/7b1e6048-0d89-4174-9706-e1fdbdc41be5)

```
lab.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/bf13c7c3-e1c6-453f-a3bf-ff8ce8da3aed)

```
lab.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/e9f3ffab-b0bf-402e-ab99-d9c833a904b6)

```
lab.fillna({'GENDER':'MALE','NAME':'PRAKASH','ADDRESS':'POONAMALEE','M1':'50','M2':'89','M3':'75','M4':'82','TOTAL':'896','AVG':'89.00000'})
```
![image](https://github.com/user-attachments/assets/4e4c657c-b4b8-4c13-8ee2-25804081027a)

```
exp=pd.read_csv("/content/iris.csv")
exp
```
![image](https://github.com/user-attachments/assets/0b87e93a-9104-4e4f-9046-4a05d3c88d34)

```
exp.describe()
```
![image](https://github.com/user-attachments/assets/0d5ee965-cd10-4423-89bb-7a4e0d142147)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=exp)
```
![image](https://github.com/user-attachments/assets/3961b64f-f54c-40e7-b648-869c4b70625d)

```
q1=exp.sepal_width.quantile(0.25)
q3=exp.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![image](https://github.com/user-attachments/assets/0c344395-8065-4f28-ad20-216e8c248074)

```
rid=exp[((exp.sepal_width<(q1-1.5*iq))|(exp.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/d2070957-bf2a-479b-b481-2b5c04aa7d48)

```
depo=exp[~((exp.sepal_width<(q1-1.5*iq))|(exp.sepal_width>(q3+1.5*iq)))]
depo
```
![image](https://github.com/user-attachments/assets/a444b2c9-ead9-4fb8-a6e2-582798252594)

```
sns.boxplot(x='sepal_width',data=depo)
```
![image](https://github.com/user-attachments/assets/19dfe545-b12c-4fe4-ae04-e1adfde058a1)

```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(exp.sepal_width))
z
```

![image](https://github.com/user-attachments/assets/29a4f1d2-807e-4497-a33e-16a30f8867ab)

```
p=exp[z<2]
p
```

![image](https://github.com/user-attachments/assets/62b3136a-87cd-4a20-9cc4-8e514e34abda)

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method. 
