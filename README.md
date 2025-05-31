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

Reading the data:
```
import pandas as pd
df=pd.read_csv('Housing.csv')
df.head()
```
# Output
![image](https://github.com/user-attachments/assets/bd0ad9cf-d7d2-40e3-8c9f-71db5de3270c)

Data Info:
```
df.info()
```
# output
![image](https://github.com/user-attachments/assets/7103d65e-3910-4b5c-b003-c2a93c4b51c2)

# Removing null values:
```df_clean = df.dropna()
df_clean
```
# Output:
![image](https://github.com/user-attachments/assets/1c9fa979-16ad-405b-a3d1-00fec4c23e59)

# Saving the clean data:
```df_clean.to_csv("Housing_clean.csv", index=False)```
# Removing Outliers using IQR:
```for col in colss:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1

    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    outlier_rows = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
    outliers[col] = outlier_rows.shape[0]
    print(f"{col}: {outlier_rows.shape[0]} outliers found")
```
# Output:
![image](https://github.com/user-attachments/assets/11a989aa-513a-4d1a-8981-b97a1fad3d08)

# Using Z Score:
```
import numpy as np
from scipy.stats import zscore
z_scores = np.abs(df[colss].apply(zscore))
outliers_z = (z_scores > 3)
for col in colss:
    print(f"{col}: {outliers_z[col].sum()} outliers found")
```
# Output:
![image](https://github.com/user-attachments/assets/b6bc6867-a627-4f3b-bb18-7a6a5a2b58e6)

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.


