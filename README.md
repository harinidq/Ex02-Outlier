# Ex02-Outlier
# AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

## ALGORITHM:
# STEP 1
Read the given Data.

# STEP 2
Get the information about the data.

# STEP 3
Detect the Outliers using IQR method and Z score.

# STEP 4
Remove the outliers.

# STEP 5
Plot the datas using Box Plot.

## PROGRAM:
```
DEVELOPED BY: M.D.HARINI
REGISTER NUMBER: 212222230043

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT:
# bhp.csv 

## df.head()
![image](https://user-images.githubusercontent.com/113497680/227696829-2b2c4833-7a33-4637-b4d4-6d6ac36180a0.png)

## df.describe()
![image](https://user-images.githubusercontent.com/113497680/227696853-a5f8d79e-4b79-46a0-a3a5-e4cf669b6a54.png)

## df.info()
![image](https://user-images.githubusercontent.com/113497680/227696891-210cfea0-87c1-4c14-8b49-e2ca6aa336c9.png)

## df.shape
![image](https://user-images.githubusercontent.com/113497680/227696915-27c31042-5f4e-4a41-a196-0948a56729ed.png)

## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697033-5f37d7bf-5873-4f37-93a3-85549e9b9ccc.png)

## NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/113497680/227697067-2ced6ac7-f1a5-41d8-bcac-10d6f411d632.png)

## OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697085-6bd32e37-0cfd-4e6b-9219-75367b943643.png)

## newdata.shape
![image](https://user-images.githubusercontent.com/113497680/227697118-864eb6f4-a0af-4e4c-aeed-f62685ef3259.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/113497680/227697144-fb3fa483-4be3-40c6-8247-36efb3727271.png)

## Zscore of 3

## NEWDATA USING Zscore
![image](https://user-images.githubusercontent.com/113497680/227697180-b910c4d4-9432-4661-8ab0-0103d59cd9b9.png)

## OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697498-841b680c-cc1c-4336-a3e8-66e593ed8142.png)

## newdata2.shape
![image](https://user-images.githubusercontent.com/113497680/227697517-2a4fcfff-5a33-4280-93de-24ddace8605e.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://user-images.githubusercontent.com/113497680/227697554-ad30744e-15c4-4430-8dfe-2a634a22ab38.png)

## height_weight.csv
dataset.shape![image](https://user-images.githubusercontent.com/113497680/227697684-ff57dbf7-4f2f-45a7-96d4-3b1674e3f7f2.png)

## dataset.describe()
![image](https://user-images.githubusercontent.com/113497680/227697776-2ad996e1-af2c-42d8-b538-f12634a15487.png)

## dataset.info()
![image](https://user-images.githubusercontent.com/113497680/227697826-599bd43a-be78-4642-9fb9-d211f7b993ae.png)

## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697840-ee0641fa-7c75-45c8-b05b-5cd283c534a3.png)

## HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697862-a81373f7-9fe1-4ba0-82ca-d0966f37bec1.png)

## DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227697889-48081c13-3f87-438b-9973-973a5f26878a.png)

## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227698039-951bdf5c-f8f3-4e7f-bd41-873fc9466ec9.png)

## WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227698161-fe823f9c-4186-4ffe-a4ac-932f3709ea09.png)

## DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227698258-855227af-f2f3-49ed-827c-dba02417d494.png)

## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/113497680/227698332-6c0b393e-9607-42fa-a928-75ef6c14ab3f.png)

## RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
