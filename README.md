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
df = pd.read_csv('Data_set.csv')
df
```

<img width="2111" height="817" alt="image" src="https://github.com/user-attachments/assets/f8743cd9-8cc0-4117-9050-58f8077e9474" />


```
df.info()
```

<img width="824" height="549" alt="image" src="https://github.com/user-attachments/assets/8477a909-f742-42b6-b086-4b826b7febaa" />

```
df.describe()
```

<img width="1272" height="560" alt="image" src="https://github.com/user-attachments/assets/e6da61b2-0703-467f-9246-3e720a80511f" />

```
df.head(10)
```

<img width="2166" height="681" alt="image" src="https://github.com/user-attachments/assets/cd90432c-8fd1-416d-9e1e-688cc5f651c9" />

```
df.tail(5)
```

<img width="2081" height="387" alt="image" src="https://github.com/user-attachments/assets/4354e45a-16f7-419a-82aa-5a8337a5d348" />

```
df.shape
````

<img width="267" height="144" alt="image" src="https://github.com/user-attachments/assets/18765374-46d6-44ad-8e13-d28bcb965332" />

```
df.isnull()
```

<img width="1788" height="808" alt="image" src="https://github.com/user-attachments/assets/812410bc-642d-4f1d-bc20-d61a8ff5e87e" />

```
df.notnull()
```

<img width="1785" height="809" alt="image" src="https://github.com/user-attachments/assets/701f4aac-1023-41de-9e6b-ec14a5b13826" />

```
df.isnull().sum()
```

<img width="480" height="354" alt="image" src="https://github.com/user-attachments/assets/07589e72-00db-471c-b0a6-b460005d9711" />

```
df.dropna(axis=0)
```
<img width="2167" height="808" alt="image" src="https://github.com/user-attachments/assets/cc331f78-4456-428c-b64f-b75d2ca00ede" />

```
df.dropna(axis=1)
```
<img width="792" height="812" alt="image" src="https://github.com/user-attachments/assets/4c5ac1d6-5abd-4744-8d3c-b4a678179c0c" />

```
dfs = df[df['num_episodes']>20]
dfs
```
<img width="1931" height="1268" alt="image" src="https://github.com/user-attachments/assets/43055c94-afc9-4867-916f-c87ca4cfd355" />

```
df.fillna(0)
```
<img width="1907" height="713" alt="image" src="https://github.com/user-attachments/assets/88c59ff2-8ed8-44b7-9eb1-8467b25da1a3" />

```
dfs = df[df['show_name'].str.startswith(('A','F'))&(df['num_episodes']>25)]
dfs
```
<img width="1907" height="178" alt="image" src="https://github.com/user-attachments/assets/70800ca3-e8db-4fb5-b227-4909986b1734" />

```
df.iloc[:3]
```
<img width="1883" height="212" alt="image" src="https://github.com/user-attachments/assets/f0db2377-7e69-484e-b232-b6eff434c499" />

```
df.iloc[:4]
```
<img width="1853" height="284" alt="image" src="https://github.com/user-attachments/assets/ce187edb-0653-4520-af98-7ef169a10054" />

```
df.iloc[[1,3,5],[1,3,5]]
```
<img width="547" height="231" alt="image" src="https://github.com/user-attachments/assets/54f4a458-9ef6-4861-a584-7855de331295" />

```
df.fillna('sample value')
```
<img width="1933" height="728" alt="image" src="https://github.com/user-attachments/assets/96bc9f99-b292-4cd7-9fbf-8845fe02621d" />

```
ffil = df.fillna(method = 'ffill')
ffil
```
<img width="1904" height="728" alt="image" src="https://github.com/user-attachments/assets/f58d8572-aeb8-47de-8275-932d21664616" />

```
bfil = df.fillna(method = 'bfill')
bfil
```
<img width="1918" height="722" alt="image" src="https://github.com/user-attachments/assets/9a1a93e1-7c58-4efb-a1da-131eae96cc7f" />

```
m = df.num_episodes.mean()
m
```
<img width="1902" height="729" alt="image" src="https://github.com/user-attachments/assets/c20395ab-6ce9-4e8c-bef8-4d3c2a436814" />

```
m = df.fillna(df['num_episodes'].mean())
m
```
<img width="1902" height="729" alt="image" src="https://github.com/user-attachments/assets/43916c52-b04e-400f-93b6-1552d0ea6bff" />

```
fmean = df['lifetime_popularity_rank'].fillna(value=df['lifetime_popularity_rank'].mean())
fmean
```
<img width="775" height="376" alt="image" src="https://github.com/user-attachments/assets/c6daf6a1-c120-473e-8a47-ce12403b5d48" />

```
df1 = df[z<3]
df1
```
<img width="304" height="775" alt="image" src="https://github.com/user-attachments/assets/18a3aff7-007e-4e6f-90fc-ab39a2ea53b8" />

```
import numpy as np
from scipy import stats
z = np.abs(stats.zscore(df['height']))
z
```
<img width="877" height="99" alt="image" src="https://github.com/user-attachments/assets/c0045f0e-b161-4ac1-99d6-e399a400fc34" />

```
max = df['height'].quantile(0.75)
q2 = df['height'].quantile(0.5)
min = df['height'].quantile(0.25)
iqr = max-min
lb = min-1.5*iqr
ub = max+1.5*iqr
dfs = df[(df['height']>=lb)&(df['height']<=ub)]
dfs
```
<img width="300" height="711" alt="image" src="https://github.com/user-attachments/assets/b3d15eb4-f3d0-4f49-b8eb-fa207ef01696" />

```
lb = min-1.5*iqr
ub = max+1.5*iqr
outliers = df[(df['height']<lb)|(df['height']>ub)]
print("Lower bound:",lb)
print("Upper bound:",ub)
print("Outliers:",outliers)
```
<img width="445" height="165" alt="image" src="https://github.com/user-attachments/assets/c673e33d-620b-4d0d-8be7-8699eb83e16a" />

```
max = df['height'].quantile(0.75)
min = df['height'].quantile(0.25)
iqr = max-min
iqr
```
<img width="410" height="43" alt="image" src="https://github.com/user-attachments/assets/b8f46a49-18ee-43e1-a3a1-9dcaa3eee5ce" />

```
sns.scatterplot(data=df)
```
<img width="1021" height="778" alt="image" src="https://github.com/user-attachments/assets/4618f271-90aa-4366-b252-2d2362177316" />

```
sns.boxplot(data=df)
```
<img width="1064" height="785" alt="image" src="https://github.com/user-attachments/assets/ef20e86e-b812-4f04-8aaa-0afe2a631a1b" />

```
df=pd.read_csv('heights.csv')
df
```

<img width="307" height="808" alt="image" src="https://github.com/user-attachments/assets/8467a6aa-f24a-4b61-8b98-32ba03557e38" />
```

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
