# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# Aim:
TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:

## Step 1

Import the required packages(pandas,numpy,scipy)

## Step 2
Read the given csv file

## Step 3
Convert the file into a dataframe and get information of the data.

## Step 4

Remove the non numerical data columns using drop() method.

## Step 5

Detect the outliers in the data set using z scores method.

## Step 6

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

## Step 7

Check if the outliersare removed from data set using graphical methods.

## Step 8

Save the final data set into the file.

# Program:
1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

Program developed by :Vidhyasri.k

Register number : 212222230170

import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/bhp.csv")

df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]

df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)

(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)

(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
import pandas as pd

import numpy as np

import seaborn as sns

df = pd.read_csv("/content/height_weight - Sheet1.csv")

df

df.head()

df.info()

df.describe()

df.isnull().sum()

df.shape

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]

df1

df1.shape

sns.boxplot(x="weight",data=df1)

(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
sns.boxplot(x="height",data=df)

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1

ul = q3+1.5*IQR

ll = q1-1.5*IQR

df2 =df[((df['height']>=ll)&(df['height']<=ul))]

df2

df2.shape

sns.boxplot(x="height",data=df2)

# Output:

## (1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

## Dataset:
file:///home/sec/Pictures/Screenshots/Screenshot%20from%202023-03-30%2011-19-25.png

## Dataset Head :

## Dataset Info :


## Dataset Describe:

## Null Values:

## Dataset Shape:

## Box plot of price_per_sqft column with outliers:

## price_per_sqft - Dataset after removing outliers:

## price_per_sqft - Shape of Dataset after removing outliers :

## Box Plot of price_per_sqft column without outliers:

## (3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

## Dataset after removal of outlier using z score:

## Shape of Dataset after removal of outlier using z score:

## (4) For the data set height_weight.csv detect weight and height outliers using IQR method:

## Dataset:

![Screenshot from 2023-03-31 11-11-01](https://user-images.githubusercontent.com/119477817/229032996-c5b07d10-7d9b-4970-9ce6-2abb6f532540.png)

## Dataset Head:

![Screenshot from 2023-03-31 11-12-24](https://user-images.githubusercontent.com/119477817/229033172-7d4d05d0-6fcd-466a-b310-0f75918720bd.png)


## Dataset Info:

![Screenshot from 2023-03-31 11-13-13](https://user-images.githubusercontent.com/119477817/229033272-32a45d04-6c18-4b88-af54-6d8e9e7ad552.png)


## Dataset Describe:

![image](https://user-images.githubusercontent.com/119477817/229033345-aa3d56cf-2262-4063-a17b-b3a2da0ded13.png)

 
## Null Values:
![Screenshot from 2023-03-31 19-14-21](https://user-images.githubusercontent.com/119477817/229136828-68823307-1667-4090-bcba-628e0db04fc6.png)

## Dataset Shape:
![Screenshot from 2023-03-31 19-15-15](https://user-images.githubusercontent.com/119477817/229137065-5f624fc5-8ad1-48af-adac-44c7cc6cade9.png)

## Box plot of price_per_sqrt column with outliers:
![Screenshot from 2023-03-31 19-16-50](https://user-images.githubusercontent.com/119477817/229137482-1d1eaae8-c713-4dfd-93c7-51bbb70394dc.png)

## price_per_sqft-Dataset after removing outliers:
![Screenshot from 2023-03-31 19-19-09](https://user-images.githubusercontent.com/119477817/229138324-7fc88311-bdbf-43a5-a56e-6ddf2831f4c5.png)

## price_per_sqft-shape of dataset after removing outliers:
![Screenshot from 2023-03-31 19-20-56](https://user-images.githubusercontent.com/119477817/229138771-4efa0ca4-9073-4c1b-98b3-479d0d425182.png)

## Box plot of price_per_sqft column without outliers:
![Screenshot from 2023-03-31 19-22-32](https://user-images.githubusercontent.com/119477817/229139122-e7529bd7-1ea2-4d82-9f52-a6cd9777f60e.png)

## (3) Examine price_per_sqft column and use zscore of 3 to remove outliers.

## Dataset after removal of outlier using z score:

![Screenshot from 2023-03-31 19-25-05](https://user-images.githubusercontent.com/119477817/229139785-640395af-5309-40df-b948-169126f47778.png)

## Shape of Dataset after removal of outlier using zscore:
![Screenshot from 2023-03-31 19-26-47](https://user-images.githubusercontent.com/119477817/229140205-8605549b-e731-4cd4-870f-104e45a51466.png)

## (4) For the data set height_weight.csv detect weight and height outliers using IQR method:

## Dataset:
![Screenshot from 2023-03-31 19-28-49](https://user-images.githubusercontent.com/119477817/229140785-b6b2ace5-7e95-40bf-95bd-e5e275b45664.png)

## Dataset head:
![Screenshot from 2023-03-31 19-30-05](https://user-images.githubusercontent.com/119477817/229141120-03d97c66-0577-4f10-9cf2-b44c5baed24f.png)

## Dataset info:
![Screenshot from 2023-03-31 19-31-07](https://user-images.githubusercontent.com/119477817/229141381-70681167-923f-40f0-a22f-0b670b194928.png)

## Dataset describe:
![Screenshot from 2023-03-31 19-32-03](https://user-images.githubusercontent.com/119477817/229141599-3c03b147-4e50-4a2c-8ca8-9be4d94518cc.png)

## Null values:
![Screenshot from 2023-03-31 19-33-14](https://user-images.githubusercontent.com/119477817/229141891-23d0df45-db13-441c-971c-8c0d154774c4.png)

## Dataset shape:
![Screenshot from 2023-03-31 19-34-04](https://user-images.githubusercontent.com/119477817/229142138-983f89b7-b078-43dc-bb94-a4cf05cfac5e.png)

## Weight -with outliers:

![Screenshot from 2023-03-31 19-35-09](https://user-images.githubusercontent.com/119477817/229142568-e70878d5-dcab-46f3-9396-af1b5c712e40.png)

## Weight -Dataset after removing outliers using IQR method:
![Screenshot from 2023-03-31 19-36-36](https://user-images.githubusercontent.com/119477817/229143006-e49aecce-d6c2-47f5-9f00-8fdf8c0f7c00.png)

## Weight -shape of dataset after removing outliers using IQR method:
![Screenshot from 2023-03-31 19-38-52](https://user-images.githubusercontent.com/119477817/229143855-ac71f365-68c1-488d-84f4-d7b386f90533.png)

## Weight -without outliers using IQR method:
![Screenshot from 2023-03-31 19-39-51](https://user-images.githubusercontent.com/119477817/229144062-13ee424d-5689-4e34-a088-084aed804568.png)

## Height with outliers:
![Screenshot from 2023-03-31 19-41-15](https://user-images.githubusercontent.com/119477817/229144373-8be7319a-8422-470a-bbd4-a2cee6d4d90e.png)

## Height - shape of dataset  after removing outliers using IQR method: 
![Screenshot from 2023-03-31 19-43-29](https://user-images.githubusercontent.com/119477817/229144912-0cfa418b-e126-430c-aba7-9304386dfe69.png)

## Height - without outliers using IQR method:
![Screenshot from 2023-03-31 19-44-21](https://user-images.githubusercontent.com/119477817/229145105-39d94eca-f85e-4d50-9d2b-ba1ab18c8666.png)

# Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
