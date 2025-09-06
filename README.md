# Exno:1
DATA CLEANING PROCESS

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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="1276" height="855" alt="data sci exp01-0 1" src="https://github.com/user-attachments/assets/72bfbcee-6124-4c45-ae8e-2721952c4e78" />


```
df.head()
```


<img width="1220" height="312" alt="dat sciexp01-0 2" src="https://github.com/user-attachments/assets/46649798-11c9-447c-a0eb-492249b72078" />


```
df.tail()
```
<img width="1265" height="326" alt="data sci exp01-0 3" src="https://github.com/user-attachments/assets/95c91c68-8113-4550-b4b8-879bc594e25d" />

```
df.isnull()
```

<img width="1301" height="865" alt="data sci exp01=0 4" src="https://github.com/user-attachments/assets/973ca10f-8c68-4627-8a74-971641a9c1f7" />


```
df.notnull()
```

<img width="1371" height="858" alt="data sci exp01=0 5" src="https://github.com/user-attachments/assets/97d7f2c1-17be-4abd-9510-85f9c4b16e6e" />

```
df.isnull().sum()
```

<img width="1317" height="631" alt="data sci exp01=0 6" src="https://github.com/user-attachments/assets/46a56d9d-9f2c-492c-8eb7-28ade7627163" />

```
df.isnull().any()
```

<img width="1143" height="650" alt="data sci exp01=0 7" src="https://github.com/user-attachments/assets/c2a8e6c1-e1c9-4d66-b222-2eeb4aeba1e2" />

```
df.dropna(axis=0)
```

<img width="1325" height="637" alt="data sci exp01=0 8" src="https://github.com/user-attachments/assets/ec8bdef1-a565-4549-9d61-7d66612a60d7" />

```
df.dropna(axis=1)
```

<img width="1137" height="857" alt="data sci exp01-0 9" src="https://github.com/user-attachments/assets/03891ccf-e8ad-4300-97c2-77750f618cfe" />

```
df.fillna(5)
```

<img width="1517" height="857" alt="data sci exp01-0 10" src="https://github.com/user-attachments/assets/4787e08c-fcfe-464d-9507-49efd02e355f" />

```
df.fillna(method='ffill')
```

<img width="1740" height="863" alt="data sci exp01-0 11" src="https://github.com/user-attachments/assets/2267bf84-a7f7-4edd-a03c-03e5014ffa3e" />

```
df.fillna(method='bfill')
```

<img width="1787" height="867" alt="data sci exp01-0 12" src="https://github.com/user-attachments/assets/6237dba8-73fe-472f-982c-24b15fdf692d" />

```
df.fillna({'GENDER':'MALE','NAME':'SANTHOSH','ADDRESS':'KANCHIPURAM','M1':'76.0','M2':'69.0','M3':'80.0','M4':'76.0','TOTAL':'301.0','AVG':'100.333333'})
```

<img width="1610" height="855" alt="data sci exp01=0 13" src="https://github.com/user-attachments/assets/e97e5cec-5ce8-4100-b79d-ddccc95b3f93" />

```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```

<img width="1172" height="637" alt="data sci exp01-0 14" src="https://github.com/user-attachments/assets/660bd645-c23c-43b3-ab36-b3c2b68e1299" />

```
ir.describe()
```

<img width="903" height="452" alt="data sci exp01-0 15" src="https://github.com/user-attachments/assets/838bfe0c-7a00-4f72-aebe-3e0db9bee493" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="1298" height="680" alt="data sci exp01-0 16" src="https://github.com/user-attachments/assets/91b67fea-c2bc-4587-9709-77c7f8861c18" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```

<img width="860" height="202" alt="data sci exp01-0 17" src="https://github.com/user-attachments/assets/6ff23336-08cf-4e04-8b7e-a935d3db62a3" />


```
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```

<img width="1067" height="357" alt="data sci exp01-0 18" src="https://github.com/user-attachments/assets/088b1b2e-7d25-4ba7-8723-844a4df74246" />

```
delid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
delid
```

<img width="1191" height="613" alt="data sci exp01-0 19" src="https://github.com/user-attachments/assets/a7b38abd-f732-46b1-be8b-19071c03b5fb" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="1282" height="657" alt="data sci exp01-0 20" src="https://github.com/user-attachments/assets/c79067e3-b483-4876-aeea-3ffcb75efca0" />

```
import numpy as np
import scipy.stats as stats
xyz=np.abs(stats.zscore(ir['sepal_width']))
xyz
```

<img width="1322" height="801" alt="data sci exp01-0 21" src="https://github.com/user-attachments/assets/4fea979b-9a29-44da-ace1-e5a641d141e3" />

```
ir1=ir[xyz>3]
ir1
```

<img width="1485" height="315" alt="data sci exp01-0 22" src="https://github.com/user-attachments/assets/fe07770a-53fc-4e04-8c98-a34d4b398a39" />












# Result
The given data and perform data cleaning and save the cleaned data to a file is completed successful
