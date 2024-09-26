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
<table>
  <tr>
    <td width=50%>


  ## CODING

  </td>
  <td>
              
## OUTPUT

</td>
</tr>

<tr>
    <td width=50%>


```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("titanic_dataset.csv")
df
```
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/a25e15b2-7127-4925-b2c0-e9b119ff4cdb)



</td>
</tr>

</td>
</tr>

<tr>
    <td width=50%>


```
df.info()
```
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/df549815-bcee-4e9b-b61a-2c5826da296e)




</td>
</tr>

<tr>
    <td width=50%>


```
df.shape
```
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/48a47a2f-2f9d-4f21-be68-d01203656e98)




</td>
</tr>

<tr>
    <td width=50%>


```
df.set_index("PassengerId", inplace=True)
df.describe()
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/ebd1add6-b462-4035-848b-b2a4846a6774)




</td>
</tr>

<tr>
    <td width=50%>


```
df.nunique()
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/574a2f0b-16ef-46b3-9f56-2182459d416d)




</td>
</tr>

<tr>
    <td width=50%>


```
df["Survived"].value_counts()
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/804a2bd1-6289-4145-8844-e90d30feea84)




</td>
</tr>

<tr>
    <td width=50%>


```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/bbadc9bf-6332-4095-8ea7-fd2236bdbb61)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.countplot(data = df, x = "Survived")
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/24b23962-11c4-4a32-a684-b4c6f06019f9)




</td>
</tr>

<tr>
    <td width=50%>


```
df
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/1b65a6b7-1bb9-4ea0-b8df-6626b9f5703f)




</td>
</tr>

<tr>
    <td width=50%>


```
df.Pclass.unique()
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/77071a52-debe-4cbe-8388-4cbe2ee22d66)




</td>
</tr>

<tr>
    <td width=50%>


```
df.rename(columns={'Sex':'Gender'}, inplace = True)
df
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/f6d24aa5-44c3-4830-9ee9-7ce459e0e251)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.catplot(x = 'Gender', col = 'Survived', kind = 'count',
 data = df, height = 5, aspect = .7)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/fa9fc28c-dd97-4c67-a876-abd88dd10872)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.catplot(x = 'Survived', hue = 'Gender',
kind = 'count', data = df)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/45584658-af44-46e8-b7e0-0acea5677de5)




</td>
</tr>

<tr>
    <td width=50%>


```
df.boxplot(column = 'Age', by = 'Survived')
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/b44b6744-3ee2-49ea-a280-4683ccfb4799)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.scatterplot(x = df['Age'], y = df['Fare'])
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/5073fe0b-918c-4f6c-b18b-4a33c24dbd9f)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.jointplot(x = 'Age', y = 'Fare', data = df)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/162a6b25-390a-443c-8f8f-5155ffd5a068)




</td>
</tr>

<tr>
    <td width=50%>


```
fig, ax1= plt.subplots(figsize=(8,5))
pt = sns.boxplot(ax=ax1, x = 'Pclass', y= 'Age',
hue = 'Gender', data = df)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/f1bbf37c-d647-496a-8d32-2df2df13b110)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.catplot(data = df, col = 'Survived', x = 'Gender',
 hue = 'Pclass', kind = 'count')
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/8430ae10-4ebb-4a8c-a803-8c8cfb6346b6)




</td>
</tr>

<tr>
    <td width=50%>


```
sns.pairplot(df)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/cdeea6af-9a90-4ddd-9323-79adead7b99b)




</td>
</tr>

<tr>
    <td width=50%>


```
numerical_df = df.select_dtypes(include=['number'])
corr = numerical_df.corr()
sns.heatmap(corr, annot=True)
````
  </td>
  <td>
              

![image](https://github.com/user-attachments/assets/c6b0fbd3-04df-44e2-acf4-89cd5c582be1)




</td>
</tr>

</table>


# RESULT
###Hence performed the exploratory data analysis on the given dataset
