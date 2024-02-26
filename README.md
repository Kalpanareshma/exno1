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
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![ds1](https://github.com/Kalpanareshma/exno1/assets/122040453/f078cf22-2a6b-4655-a82a-2a4894e68017)
```
data = pd.get_dummies(data)
data.isnull().sum()
```
![ds2](https://github.com/Kalpanareshma/exno1/assets/122040453/6c5cd81d-9cec-4e63-97ec-5dee5e1575cb)
```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![ds3](https://github.com/Kalpanareshma/exno1/assets/122040453/77679d67-4378-45b2-a61f-f778723f6d4d)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![ds4](https://github.com/Kalpanareshma/exno1/assets/122040453/ecfa0ada-740f-4aec-9bfa-0e0d1ded38d7)

#IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/a435e325-7337-4220-ae10-d51f5381ddae)
```
ir.describe()
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/32410ed8-76e3-4e1c-923e-f6345797a04e)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/362cfcaf-b13a-4b52-b503-cec25494b892)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/92a05b8a-3e20-4fd0-9b05-6b32a9692b14)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/2fe90fd2-38a7-45e5-8f91-3b31b979c7a5)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/e7495149-035b-4544-9766-8e7371737e12)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/3991c6b2-6efc-4be1-bb7c-a279ce507297)
#Z Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/Kalpanareshma/exno1/assets/122040453/21af3c8c-f10f-449f-a596-3dd4c981ed94)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
















# Result
         Thus the given data is read,cleansed and the cleaned data is saved into the file.
