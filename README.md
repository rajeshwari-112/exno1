
# Exno:1
Data Cleaning Process

# AIM:
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation:
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm:
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:
```py
import pandas as pd
df= pd.read_csv("/content/SAMPLEIDS ().csv")
df
```
<img width="1079" height="859" alt="image" src="https://github.com/user-attachments/assets/e7737cd3-dd5d-4b5d-889d-cbde9a2c6927" />

```py
df.head(3)
```
<img width="1093" height="191" alt="image" src="https://github.com/user-attachments/assets/95c15ec5-9ddb-49b6-a4bd-fdfee14bfadf" />

```py
df.tail(5)
```
<img width="1118" height="272" alt="image" src="https://github.com/user-attachments/assets/47f6a8b6-2d61-49cf-80d6-b4666e642dd2" />

```py
df.isnull()
```
<img width="1009" height="867" alt="image" src="https://github.com/user-attachments/assets/025ef5af-1dc0-4c14-96b2-f0a96f2a32ac" />

```py
df.notnull()
```
<img width="953" height="852" alt="image" src="https://github.com/user-attachments/assets/2b2fb83b-ec6a-4a39-bf83-9f79fff55cb0" />

```py
df.isnull().sum()
```
<img width="255" height="582" alt="image" src="https://github.com/user-attachments/assets/001a2c72-2a65-4173-a694-48c255aa56d1" />

```py
df.isnull().any()
```
<img width="290" height="579" alt="image" src="https://github.com/user-attachments/assets/84bba7ce-d471-497d-b687-52543c4a5e0a" />

```py
df.dropna()
```
<img width="1158" height="583" alt="image" src="https://github.com/user-attachments/assets/0225f5c2-57a6-49c4-9337-e1c50acc5b96" />

```py
df.dropna(axis=1)
```
<img width="484" height="862" alt="image" src="https://github.com/user-attachments/assets/62e29f35-71fb-46bd-9e56-470f604572a7" />

```py
df.fillna(0)
```
<img width="1127" height="867" alt="image" src="https://github.com/user-attachments/assets/fcbb9886-a40b-4404-aed8-136ab03720c3" />

```py
df.fillna (method = 'ffill')
```
<img width="1079" height="865" alt="image" src="https://github.com/user-attachments/assets/f0bff26d-0e94-411c-b577-cb93d5c164c9" />

```py
df.fillna (method = 'bfill')
```
<img width="1075" height="858" alt="image" src="https://github.com/user-attachments/assets/8cbc1dc4-b8a2-40ad-9a93-237cad9c336e" />

```py
ir=pd.read_csv("/content/iris ().csv")
ir
```
<img width="770" height="521" alt="image" src="https://github.com/user-attachments/assets/e67d2039-1f02-461e-9929-1cc2b5517b85" />

```py
ir.describe()
```
<img width="795" height="379" alt="image" src="https://github.com/user-attachments/assets/b295f0b4-2400-4b9d-8fd2-01873dded29d" />

```py
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="807" height="708" alt="image" src="https://github.com/user-attachments/assets/5e5b1faf-bb14-4ef9-b86e-53bedb315db6" />

```py
Q1= ir.sepal_width.quantile(0.25)
Q3= ir.sepal_width.quantile(0.75)
IQR= Q3-Q1
print(IQR )
```
<img width="429" height="43" alt="image" src="https://github.com/user-attachments/assets/d0911872-9abf-4566-a3de-69e3abd6be1d" />

```py
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```
<img width="252" height="269" alt="image" src="https://github.com/user-attachments/assets/1f7b75e1-f1fb-47af-bf47-92d5f9f6211c" />

```py
rid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```
<img width="299" height="570" alt="image" src="https://github.com/user-attachments/assets/eef3640e-a0e9-4e31-9a37-e602c37abe80" />

```py
sns.boxplot(x='sepal_width',data= rid)
```
<img width="788" height="591" alt="image" src="https://github.com/user-attachments/assets/db049b8d-674a-4145-992e-5e4419bcc078" />

```py
import numpy as np
import scipy.stats as stats
Z= np.abs(stats.zscore(ir['sepal_width']))
Z
```
<img width="840" height="680" alt="image" src="https://github.com/user-attachments/assets/4b25b8ee-0f7c-4f5e-be4d-1212d6412a4a" />

```py
df1 = ir[Z<3]
df1
```
<img width="786" height="549" alt="image" src="https://github.com/user-attachments/assets/c22fb912-c213-411f-b517-5e7060fd097f" />

# Result:
The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.
