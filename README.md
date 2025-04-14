# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

#Regno: 212224040020 Name: Aman Singh

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
Pyhton codes:
import pandas as pd
import numpy as np
df=pd.read_csv("/content/SAMPLEIDS.csv")
df

df.shape

df.describe()

df.info()

df.head(10)

df.tail(5)

df.isna()

df.isna().sum()

df.dropna(how="any").shape

x=df.dropna(how="any")
x

mn=df.TOTAL.mean()
mn

df.TOTAL.fillna(mn,inplace=True)
df

df.isnull().sum()

df.M1.fillna(method="ffill",inplace=True)
df

df.isna().sum()

df.M2.fillna(method='ffill',inplace=True)
df

df.isna().sum()

df.M3.fillna(method='ffill',inplace=True)
df

df.isna().sum()

df.duplicated()

df.drop_duplicates(inplace=True)
df

df.duplicated()

df['DOB']

import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

"""**OutLiers Detection and removal Using IQR**"""

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

sns.boxplot(data=df)

sns.scatterplot(data=df)

q1=df.quantile(0.25)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound

upper_bound

outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)

df=df[((df>=lower_bound)&(df<=upper_bound))]
df

df=df.dropna()
df

sns.boxplot(data=df)

sns.scatterplot(data=df)

data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)

threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier);

from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

Screenshots of the codes with Outputs:

<img width="1440" alt="Screenshot 2025-04-14 at 12 49 21 PM" src="https://github.com/user-attachments/assets/8b9c2bba-b68d-4347-8ce4-6b802c35e04b" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 27 PM" src="https://github.com/user-attachments/assets/29de6e3c-269b-4688-b323-43d5a0a6bac9" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 32 PM" src="https://github.com/user-attachments/assets/ce7cd5ba-4282-4c23-b766-0413c9e79816" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 37 PM" src="https://github.com/user-attachments/assets/8d535cc7-42a2-43e6-b5c3-a22d03909bec" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 45 PM" src="https://github.com/user-attachments/assets/f94b8cf6-628a-4751-a482-92140f86cf79" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 50 PM" src="https://github.com/user-attachments/assets/9a31f5f6-20b5-4401-b0ad-fc7bf0318eff" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 49 56 PM" src="https://github.com/user-attachments/assets/b5bf1047-1a7c-4df3-84a9-f5562c9fac60" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 00 PM" src="https://github.com/user-attachments/assets/0107a476-e318-4d84-9e49-42afbea98fb0" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 03 PM" src="https://github.com/user-attachments/assets/7cd4f487-8585-4a29-8b73-1fc0129e3099" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 07 PM" src="https://github.com/user-attachments/assets/0cc7c3af-44bf-48b3-a656-b9f2ec9cc523" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 11 PM" src="https://github.com/user-attachments/assets/83fbe3eb-bbe4-4865-8993-9662dcb61d72" />

<img width="1440" alt="Screenshot 2025-04-14 at 12 50 15 PM" src="https://github.com/user-attachments/assets/17ba07d5-3f26-4b23-8db4-a5236f68e310" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 20 PM" src="https://github.com/user-attachments/assets/286ebdd5-4bbb-4fd9-96f1-9210d7e70914" />

<img width="1440" alt="Screenshot 2025-04-14 at 12 50 23 PM" src="https://github.com/user-attachments/assets/d113d1ef-4b27-41b7-87c0-e6ff2ba73fc5" />
<img width="1440" alt="Screenshot 2025-04-14 at 12 50 35 PM" src="https://github.com/user-attachments/assets/f5b6d117-5864-44b5-9930-c9591b3edd3f" />



# RESULT
        Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score




