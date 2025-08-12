# Name : AFIFA A
# Register number: 212223040008
# Exno:1 Data Cleaning Process

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
### Data Cleaning
```
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```
![image](https://github.com/user-attachments/assets/0b733593-c624-4940-8293-65d05ff45229)
```
data.head()
```
![image](https://github.com/user-attachments/assets/06e1ddde-b8bc-4677-967f-529191dbe4d3)
```
data.tail()
```
![image](https://github.com/user-attachments/assets/e3d3b29f-b562-4ff1-850b-5567d2ba7db6)
```
data.isnull()
```
![image](https://github.com/user-attachments/assets/f608e511-86ee-44ec-8421-74e348021caa)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/eb27fd60-5d41-44bf-8828-ce9ea32973f0)
```
data.isnull().any()
```
![image](https://github.com/user-attachments/assets/09506df2-ef07-4611-8a29-d72c10b716e9)
```
data.dropna()
```
![image](https://github.com/user-attachments/assets/64c85113-58ad-4c1e-9586-d6f99a422216)
```
data.fillna(0)
```
![image](https://github.com/user-attachments/assets/46002150-0be6-4187-b025-d83690429907)
```
data.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/8a8b8595-db29-4ac1-93d5-eb114d19487b)
```
data.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/ec229a15-0a80-4374-bcf9-97679e3e50e7)
```
 data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/65ac16fb-42e4-44e3-9db1-45c763a75ded)
### IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv("iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/b3aea645-a472-47ab-b7f3-dc7968c5c6e4)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/b090d36a-5492-49ef-b802-f1ff35c17287)
```
ir.shape
```
![image](https://github.com/user-attachments/assets/ef5bd4db-bb4d-49e3-a128-dc1c39ad1ead)
```
ir.info()
```
![image](https://github.com/user-attachments/assets/2c5ce04b-5252-4f4f-bdfc-af1619dcd251)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/02ccc2dc-3806-45f0-a8a3-611013adc992)
```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
```
![image](https://github.com/user-attachments/assets/a317c618-f4ae-4eaa-a056-557738f7d66a)
```
 out=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 out['sepal_width']
```
![image](https://github.com/user-attachments/assets/f0e564b7-6b6d-41b9-b70e-f258236f301d)
```
 nor=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 nor['sepal_width']
```
![image](https://github.com/user-attachments/assets/2f01f216-abf7-4f86-a4d5-f8ebf4052d1b)
```
sns.boxplot(x='sepal_width',data=nor)
```
![image](https://github.com/user-attachments/assets/d7937282-ea65-47ab-abee-798f0f806f9e)
### Z-SCORE
```
import numpy as np
import pandas as pd
df=pd.read_csv("/heights.csv")
df
```
![image](https://github.com/user-attachments/assets/823f9503-fc0b-4b88-abf5-f12bbb6857a9)
```
import scipy.stats as stats
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/a4e7ee09-9234-4914-9f94-b95bc38c3963)
```
low = q1 - 1.5*iqr
print(low)
high = q3 + 1.5*iqr
print(high)
```
![image](https://github.com/user-attachments/assets/bd2c79bd-d8d9-4d5c-a6de-ae0df27e4a75)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/462ba034-2a52-47cd-a5ef-6c8dc3a17c39)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/865c01f6-a50d-40cd-92c1-cd65f1553e5c)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/62540181-a6a9-4cc6-a14a-fa337b473390)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
