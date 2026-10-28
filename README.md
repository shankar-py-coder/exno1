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
import numpy as np
df=pd.read_csv("/SAMPLEIDS (3).csv")
df
```
<img width="1012" height="705" alt="image" src="https://github.com/user-attachments/assets/fa1eea7a-f3f8-4f3b-93c3-0f266d4fd2b5" />
```
df.isnull().sum()
```
<img width="742" height="632" alt="image" src="https://github.com/user-attachments/assets/9d8d26e7-14aa-4b21-be80-18c94f72c419" />
```
df.info()
```
<img width="701" height="476" alt="image" src="https://github.com/user-attachments/assets/fd1438bf-84de-4551-9e8b-73d7f86cc491" />
```
df.describe()
```
<img width="1047" height="422" alt="image" src="https://github.com/user-attachments/assets/d6eb808d-8f5b-4548-bda3-ebf2e19e355d" />
```
df.shape
```
<img width="597" height="92" alt="image" src="https://github.com/user-attachments/assets/7f7a69e0-b97c-468f-8c34-d77001f7a5a2" />
```
df.head(3)
```
<img width="1123" height="230" alt="image" src="https://github.com/user-attachments/assets/969875b6-b4fa-4066-9751-5172f67862f9" />

```
df.tail(3)
```
<img width="1077" height="222" alt="image" src="https://github.com/user-attachments/assets/0c78189e-212d-43ba-9032-6b5155d587c1" />
```
df.dropna(how='any').shape
df.shape
```
<img width="806" height="195" alt="image" src="https://github.com/user-attachments/assets/692c87d2-4e08-4134-b627-42bf21298190" />
```
df.TOTAL.fillna(mn,inplace=True)
```
<img width="1727" height="231" alt="image" src="https://github.com/user-attachments/assets/86551ce4-33f6-47de-aae5-1f91f5000e69" />
```
df.isna().sum()
```
<img width="692" height="622" alt="image" src="https://github.com/user-attachments/assets/ddc31fb4-391a-40cb-a5ed-dbb03edbd59f" />
```
df['M1'].fillna(method='ffill',inplace=True)
```
<img width="1572" height="253" alt="image" src="https://github.com/user-attachments/assets/bc829a40-a5d4-49ce-b095-a1f884185a76" />
```
df.isna().sum()
```
<img width="997" height="625" alt="image" src="https://github.com/user-attachments/assets/0689f41e-62df-43d7-8638-024f8351f248" />
```
df['M2'].fillna(method='ffill',inplace=True)
```
<img width="1660" height="267" alt="image" src="https://github.com/user-attachments/assets/9d8975c3-0d33-4053-b9f6-dfedf3c4318b" />
```
df.isna().sum()
```
<img width="736" height="608" alt="image" src="https://github.com/user-attachments/assets/983a4472-8648-4ab9-b4a8-7e09ee0f9c7b" />
```
df['M3'].fillna(method='bfill',inplace=True)
```
<img width="1672" height="268" alt="image" src="https://github.com/user-attachments/assets/35415455-2440-4492-a116-966a88cd60cd" />
```
df.isna().sum()
```
<img width="620" height="625" alt="image" src="https://github.com/user-attachments/assets/a2f69864-25c8-48bd-8fb8-a65023118561" />
```
df['M4'].fillna(method='ffill',inplace=True)
```
<img width="1712" height="273" alt="image" src="https://github.com/user-attachments/assets/8ff906cb-e015-4a9a-a637-a0676ef4b4e4" />
```
df.isna().sum()
```
<img width="752" height="607" alt="image" src="https://github.com/user-attachments/assets/d4e4a2d8-31b1-4c7f-b12d-3adec6cc6453" />
```
df.drop_duplicates(inplace=True)
df
```
<img width="1016" height="702" alt="image" src="https://github.com/user-attachments/assets/6cbc33d5-be4c-4acb-871d-badf1ba0bab6" />
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
<img width="706" height="612" alt="image" src="https://github.com/user-attachments/assets/a4ef1512-6c9f-4a35-81a2-f9a9bad08e6e" />
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
<img width="731" height="616" alt="image" src="https://github.com/user-attachments/assets/f56802c0-ac38-48ff-9757-37b8e850e7cf" />
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
<img width="432" height="582" alt="image" src="https://github.com/user-attachments/assets/f4687d43-e96f-4035-bcee-54a2b3fe66f9" />
```
sns.boxplot(data=af)
```
<img width="711" height="537" alt="image" src="https://github.com/user-attachments/assets/3f3cd899-9365-462a-af6e-bcf915c3a7ed" />
```
sns.scatterplot(data=af)
```
<img width="692" height="527" alt="image" src="https://github.com/user-attachments/assets/1404ed09-684b-4f71-bfd9-c39efb5d2c81" />
```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
<img width="392" height="160" alt="image" src="https://github.com/user-attachments/assets/f6f1581e-f419-451f-b9d6-f2fa28a8c209" />
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
upper_bound
```
<img width="767" height="290" alt="image" src="https://github.com/user-attachments/assets/0b43db0b-5ba9-4632-b513-cf153978d8fe" />
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print('Q1:',Q1)
print('Q3:',Q3)
print('IQR:',IQR)
print('lower_bound:',lower_bound)
print('upper_bound:',upper_bound)
print('outliers:',outliers)
```
<img width="920" height="323" alt="image" src="https://github.com/user-attachments/assets/9bcbdbfa-0cdd-4eb0-9893-9485b9cd41b7" />
```
af=af[((af>lower_bound)&(af<upper_bound))]
af
```
<img width="533" height="597" alt="image" src="https://github.com/user-attachments/assets/e6baf770-9bd8-47c2-8c39-27889e49d892" />
```
af.dropna(inplace=True)
af
```
<img width="282" height="443" alt="image" src="https://github.com/user-attachments/assets/1da55fd4-8864-4af0-9832-59d010bae626" />
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print("mean of the dataset is",mean)
print("std. deviation is",std)
```
<img width="832" height="207" alt="image" src="https://github.com/user-attachments/assets/3af11a25-c89e-4549-8481-c45ffed6b9f0" />
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print("outlier in dataset is",outlier)
```
<img width="858" height="231" alt="image" src="https://github.com/user-attachments/assets/052295e9-354d-4c0d-8eef-c472072e40ad" />

# Result
Thus the python program for reading the given data and perform data cleaning and save the cleaned data to a file is executed.
