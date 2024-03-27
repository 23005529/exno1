# Ex : 1 Data Cleaning Process

## AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

## Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

## Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

## Coding and Output
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![Alt text](O1.png)
```
df.info()
```
![Alt text](O2.png)

```
df.isnull().sum()
```
![Alt text](O3.png)

```
df.nunique()
```
![alt text](O4.png)

```
df.dropna()
```
![alt text](O5.png)
```
d1=df.fillna(0)
d1
```
![alt text](O6.png)

```
d2=df.fillna(method='ffill')
d2
```
![alt text](O7.png)

```
d3=df.fillna(method='bfill')
d3
```
![alt text](O8.png)

```
delete=df.dropna()
delete
```
![alt text](O9.png)

## IQR(Inter Quartile Range)
```
ir=pd.read_csv('iris.csv')
ir
```
![alt text](<IQR O1.png>)

```
ir.describe()
```
![alt text](<IQR O2.png>)

```
sns.boxplot(x='sepal_width',data=ir)
```
![alt text](<IQR O3.png>)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![alt text](<IQR O4.png>)
```

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![alt text](<IQR O5.png>)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![alt text](<IQR O6.png>)
```
sns.boxplot(x='sepal_width',data=delid)
```
![alt text](<IQR O7.png>)

## Z-SCORE 
```
import matplotlib.pyplot as plt
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![alt text](<ZS O1.png>)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![alt text](<ZS O2.png>)

```
low = q1 - 1.5*iqr
low
```
![alt text](<ZS O3.png>)

```
high = q3 + 1.5*iqr
high
```
![alt text](<ZS O4.png>)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![alt text](<ZS O5.png>)

```
z = np.abs(stats.zscore(df['height']))
z
```
![alt text](<ZS O6.png>)

```
df1 = df[z<3]
df1
```
![alt text](<ZS O7.png>)








## Result
Hence the data was cleaned , outliers were detected and removed.
