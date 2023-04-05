# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

Aim:

TO detect and remove the outliers in the given data set and save the final data.

Algorithm:

Step 1
Import the required packages(pandas,numpy,scipy)

Step 2
Read the given csv file

Step 3
Convert the file into a dataframe and get information of the data.

Step 4
Remove the non numerical data columns using drop() method.

Step 5
(i) Using IQR detect weight outliers and print them
(ii) Using IQR, detect height outliers and print them
Detect the outliers in the data set using z scores method.

Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7
Check if the outliersare removed from data set using graphical methods.

Step 8
Save the final data set into the file.
```
Program:
1) & (2) Examine price_per_sqft column and use IQR to
remove outliers and create new dataframe.
Program developed by : VAISHALI BALAMURUGAN
Register number : 212222230164
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
```
```
3)Examine price_per_sqft column and use zscore of 3 to
remove outliers.
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)

(4)(i) For the data set height_weight.csv detect weight
outliers using IQR method.
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("height_weight.csv")
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

(4)(ii) For the data set height_weight.csv detect height
outliers using IQR method.
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
```

OUTPUT:

(1)(2) Examine price_per_sqft column and use IQR to remove
outliers and create new dataframe.

Dataset:

![image](https://user-images.githubusercontent.com/119390134/229976460-a3dfb188-ce14-4665-a2fe-c99b08fb1213.png)

Dataset Head:

![image](https://user-images.githubusercontent.com/119390134/229976618-95999f4d-23b8-4168-8fe9-817617e4c2ad.png)

Dataset Info:

![image](https://user-images.githubusercontent.com/119390134/229976717-1ba3fd00-723e-4c71-8e7d-ca825345945a.png)

![image](https://user-images.githubusercontent.com/119390134/229977669-a0f1975a-3f6a-4231-880f-a9353755c64c.png)

![image](https://user-images.githubusercontent.com/119390134/229977749-f753bb76-042a-4fc7-b32d-ddeecbabd505.png)

![image](https://user-images.githubusercontent.com/119390134/229977837-1eec11b4-d248-41ca-893b-ba86cbbc0758.png)

![image](https://user-images.githubusercontent.com/119390134/229977921-f6940e1b-5bb5-418d-aadf-c8d1aafb896e.png)

(3) Examine price_per_sqft column and use zscore of 3 to
remove outliers.

![image](https://user-images.githubusercontent.com/119390134/229978183-eed315c8-20e3-4fe4-9c14-148d414b47a8.png)

![image](https://user-images.githubusercontent.com/119390134/229978233-0ac7b101-d141-48e6-8767-bf31ac22fbc4.png)

(4) For the data set height_weight.csv detect weight and
height outliers using IQR method:

![image](https://user-images.githubusercontent.com/119390134/229978930-e14b3424-390d-4e70-bf66-7609266d927f.png)

![image](https://user-images.githubusercontent.com/119390134/229979062-a9d28a1b-ea17-44f2-bf3d-0a18f375c2e9.png)

![image](https://user-images.githubusercontent.com/119390134/229979143-dcbb75fe-fce4-4211-99f8-9e91b758c5bd.png)

![image](https://user-images.githubusercontent.com/119390134/229979209-693b3008-ca0d-40dd-a6ad-44ad29e89da6.png)

![image](https://user-images.githubusercontent.com/119390134/229979273-b4faa538-b545-4171-9747-102c4d65fd9a.png)

![image](https://user-images.githubusercontent.com/119390134/229979680-9a0978a1-fe81-4c19-a1de-1ddf9fc7ed48.png)

![image](https://user-images.githubusercontent.com/119390134/229979740-e9f6d06e-dd8a-4c6d-9afe-7c46cef98622.png)

![image](https://user-images.githubusercontent.com/119390134/229979805-ed8d48f1-e053-4a56-bb9e-df4a6589242e.png)

Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the
file.

