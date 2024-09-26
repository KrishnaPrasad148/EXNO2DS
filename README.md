# EXNO2DS
# AIM:
  To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("titanic_dataset.csv")
df
```
<img src="https://github.com/user-attachments/assets/c8cdbd5f-07b6-4262-b214-961a6073b63d" width="900">


```
df.info()
```
![image](https://github.com/user-attachments/assets/e7edb8d5-7cb0-434b-8d4e-8acf98ee596a)


```
df.shape
```
![image](https://github.com/user-attachments/assets/72307575-6255-4303-8150-e11bc634414f)


```
df.set_index("PassengerId", inplace=True)
df.describe()
```
![image](https://github.com/user-attachments/assets/1dd26f1f-e5a6-4c42-bdfd-468094c5985f)


```
df.nunique()
```
![image](https://github.com/user-attachments/assets/4556d571-efa4-4b2d-8aab-90575c930f81)


```
df["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/4b989308-8cf1-4b56-8294-30fac3b10063)


```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/e33dc162-b94f-4024-9654-2021c552273b)


```
sns.countplot(data = df, x = "Survived")
```
<img src="https://github.com/user-attachments/assets/fb1fe9cd-c283-43cc-a9f3-bfc722691bf1" width="500">


```
df
```
<img src="https://github.com/user-attachments/assets/0bae13b2-ea61-4937-a757-78e05163903a" width="900">


```
df.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/31cf5b22-0f28-4214-9bae-d8c55a468968)


```
df.rename(columns={'Sex':'Gender'}, inplace = True)
df
```
<img src="https://github.com/user-attachments/assets/c6b0913b-0b85-4b9f-9dfe-2445e2161a87" width="900">


```
sns.catplot(x = 'Gender', col = 'Survived', kind = 'count', data = df, height = 5, aspect = .7)
```
<img src="https://github.com/user-attachments/assets/96e37385-b484-4163-b1d3-855843363e08" width="500">


```
sns.catplot(x = 'Survived', hue = 'Gender', kind = 'count', data = df)
```
<img src="https://github.com/user-attachments/assets/1ee8e2d3-0310-4333-9a0f-ea3d0ad98115" width="500">


```
df.boxplot(column = 'Age', by = 'Survived')
```
<img src="https://github.com/user-attachments/assets/8cb8b905-7a03-4d97-b170-c49850eeddf6" width="500">


```
sns.scatterplot(x = df['Age'], y = df['Fare'])
```
<img src="https://github.com/user-attachments/assets/259a826f-c28c-4b92-a2ad-70a3314e3938" width="500">


```
sns.jointplot(x = 'Age', y = 'Fare', data = df)
```
<img src="https://github.com/user-attachments/assets/65800d1b-5d48-470c-89bb-df87dcb1bb48" width="500">


```
fig, ax1= plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1, x = 'Pclass', y= 'Age',hue = 'Gender', data = df)
```
<img src="https://github.com/user-attachments/assets/3666531f-918b-4fb8-a6e2-628a39e27665" width="500">


```
sns.catplot(data = df, col = 'Survived', x = 'Gender', hue = 'Pclass', kind = 'count')
```
<img src="https://github.com/user-attachments/assets/2db22244-1487-46b8-b826-4ae69432ef3e" width="600">


```
sns.pairplot(df)
```
<img src="https://github.com/user-attachments/assets/5a6dc0dc-1ba6-4f1f-9515-7abece7152fb" width="600">


```
numerical_df = df.select_dtypes(include=['number'])
corr = numerical_df.corr()
sns.heatmap(corr, annot=True)
```
<img src="https://github.com/user-attachments/assets/e9928a4d-c6d5-4cbb-bf5f-32966012c8fb" width="600">


# RESULT
  Hence performed the exploratory data analysis on the given dataset
