# Ex02-Outlier
## Algorithm:

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

##Aim:
TO detect and remove the outliers in the given data set and save the final data.


##Step 1
Import the required packages(pandas,numpy,scipy)

##Step 2
Read the given csv file

##Step 3
Convert the file into a dataframe and get information of the data.

##Step 4
Remove the non numerical data columns using drop() method.

##Step 5
Detect the outliers in the data set using z scores method.

##Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

##Step 7
Check if the outliersare removed from data set using graphical methods.

##Step 8
Save the final data set into the file.

##Program:
1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

Program developed by : DHIVYAPRIYA R

Register number : 212222230032

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

##(3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))

df2 = df[(z<3)]

df2

print(df2.shape)

sns.boxplot(x="price_per_sqft",data=df2)

##(4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
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

##(4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
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

##Output:

##(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

##Dataset:
![Screenshot (24)](https://user-images.githubusercontent.com/119477552/228585207-23a03864-a0be-4aa2-b8db-917125467cd4.png)

##Dataset Head :
![Screenshot (25)](https://user-images.githubusercontent.com/119477552/228585152-1b87605e-f0f5-40e1-88e2-079821f79508.png)

##Dataset Info :
![Screenshot (26)](https://user-images.githubusercontent.com/119477552/228585108-defff13f-db39-4d04-815e-a3079ac13bee.png)

##Dataset Describe:
![Screenshot (27)](https://user-images.githubusercontent.com/119477552/228585031-c75a2fc6-4ae6-4c05-b0d8-8c7734373225.png)

##Null Values:
![Screenshot (28)](https://user-images.githubusercontent.com/119477552/228584994-445e12c2-b29e-4f26-878b-341262f440b1.png)

##Dataset Shape:
![Screenshot (29)](https://user-images.githubusercontent.com/119477552/228584934-31077b57-54f3-47b4-8df0-ed8736d8dae1.png)

##Box plot of price_per_sqft column with outliers:
![Screenshot (30)](https://user-images.githubusercontent.com/119477552/228584881-daddf06f-bc7b-4c9a-aba0-90e9c061cee6.png)

##price_per_sqft - Dataset after removing outliers:
![Screenshot (31)](https://user-images.githubusercontent.com/119477552/228584842-58876c37-4ea5-4327-9962-12228aeaecf4.png)

##price_per_sqft - Shape of Dataset after removing outliers :
![Screenshot (32)](https://user-images.githubusercontent.com/119477552/228584805-2a54f1e6-eb86-43c4-98d5-232280661723.png)

##Box Plot of price_per_sqft column without outliers:
![Screenshot (33)](https://user-images.githubusercontent.com/119477552/228584757-ad791a48-8b9e-4f0e-88a3-b5c046ffc4f6.png)

##(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
##Dataset after removal of outlier using z score:
![Screenshot (34)](https://user-images.githubusercontent.com/119477552/228584686-d89eb7b1-c9f8-42d9-9b67-dd506a2af7be.png)

##Shape of Dataset after removal of outlier using z score:
![Screenshot (35)](https://user-images.githubusercontent.com/119477552/228584557-e55bb848-78df-4369-a520-959ffb4e64ef.png)

##(4) For the data set height_weight.csv detect weight and height outliers using IQR method:

##Dataset:
![Screenshot (37)](https://user-images.githubusercontent.com/119477552/228584487-a8705491-688a-4fd6-b9c6-725cd7260524.png)

##Dataset Head:
![Screenshot (38)](https://user-images.githubusercontent.com/119477552/228584445-fdcfbf1a-a7a7-4705-952d-9bcc1ffb830d.png)

##Dataset Info:
![Screenshot (39)](https://user-images.githubusercontent.com/119477552/228584408-8df2d0a5-1716-4387-9c53-c07bcdeb2030.png)

##Dataset Describe:
![Screenshot (40)](https://user-images.githubusercontent.com/119477552/228584355-3edff919-f0ef-4c73-8089-a149657ad2a6.png)

##Null Values:
![Screenshot (41)](https://user-images.githubusercontent.com/119477552/228584287-f0a26a4e-5737-4772-9619-961717788dee.png)

##Dataset Shape:
![Screenshot (42)](https://user-images.githubusercontent.com/119477552/228584234-6cbaf7ef-91df-4dfc-8829-8f5276234224.png)

##Weight - With outliers:
![Screenshot (43)](https://user-images.githubusercontent.com/119477552/228584153-bb7fa5b0-d512-47b7-8194-2737846893f8.png)

##Weight - Dataset after removing Outliers using IQR method:
![Screenshot (44)](https://user-images.githubusercontent.com/119477552/228584123-e5c777d1-b842-4bc0-98a5-dddd8fb21f05.png)

##Weight - Shape of Dataset after removing Outliers using IQR method:
![Screenshot (45)](https://user-images.githubusercontent.com/119477552/228584084-85667bfd-af6b-43a6-a046-42d3da69b7a9.png)

##Weight - Without Outliers using IQR method:
![Screenshot (46)](https://user-images.githubusercontent.com/119477552/228584015-5ea1d683-b852-49f6-b56b-64ae9fe3a277.png)

##Height - With outliers:
![Screenshot (47)](https://user-images.githubusercontent.com/119477552/228583971-c6d46a78-f0d9-4901-98c7-84c769c7805a.png)

##Height - Dataset after removing Outliers using IQR method:
![Screenshot (48)](https://user-images.githubusercontent.com/119477552/228583921-59968a5c-81e6-4809-8802-3b40ed0c07b9.png)

##Height - Shape of Dataset after removing Outliers using IQR method:
![Screenshot (49)](https://user-images.githubusercontent.com/119477552/228583880-8eef4f79-1a53-48c5-922a-849c605f9be1.png)

##Height - Without Outliers using IQR method:
![Screenshot (50)](https://user-images.githubusercontent.com/119477552/228583831-40062045-d9d3-4c5e-9d97-df27316afc43.png)

##Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
