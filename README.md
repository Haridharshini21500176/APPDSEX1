# APPDSEX1
Implementing Data Preprocessing and Data Analysis

## AIM:
To implement Data analysis and data preprocessing using a data set

## ALGORITHM:
Step 1: Import the data set necessary

Step 2: Perform Data Cleaning process by analyzing sum of Null values in each column a dataset.

Step 3: Perform Categorical data analysis.

Step 4: Use Sklearn tool from python to perform data preprocessing such as encoding and scaling.

Step 5: Implement Quantile transfomer to make the column value more normalized.

Step 6: Analyzing the dataset using visualizing tools form matplot library or seaborn.

## CODING AND OUTPUT:
```
NAME : S.ANUSHARON
REG NO : 212222240010
```
## DATA CLEANING PROCESS
```
import pandas as pd
import pandas as pd
from sklearn.preprocessing import LabelEncoder
from sklearn.preprocessing import MinMaxScaler
import statsmodels.api as sm
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/content/Toyota.csv")

df.head()
df.tail()
df.info()
df.describe()
df.shape()
df.fillna(method="ffill",inplace=True)
df.isnull().sum()
```
![Screenshot 2024-11-27 210817](https://github.com/user-attachments/assets/37477dce-4d3b-48e9-88aa-dc84ac3044a9)
![Screenshot 2024-11-27 210846](https://github.com/user-attachments/assets/e3d3074a-6d7c-45a3-86e9-5efdeac63d78)
![Screenshot 2024-11-27 210918](https://github.com/user-attachments/assets/727f570d-cc5a-40e9-9986-ed728f7acc98)
![Screenshot 2024-11-27 210940](https://github.com/user-attachments/assets/4ef5067e-eb25-49d3-a247-d5c93d20990d)
![Screenshot 2024-11-27 211008](https://github.com/user-attachments/assets/be25641b-3ef2-4785-a4bf-ea4570a7cd65)
BEFORE & AFTER FILLING THE NULL VALUES
![Screenshot 2024-11-27 211053](https://github.com/user-attachments/assets/bb70787a-4901-490d-9e3f-c1f00be2436f)

![Screenshot 2024-11-27 211112](https://github.com/user-attachments/assets/ccb336ba-fefa-4536-a801-8c60ed50ace7)
## OUTLIER DETECTION & REMOVAL
```
sns.boxplot(df["Age"])
q1, q3 = df['Age'].quantile([0.25,0.75])
iqr = q3 - q1
lower_limit = q1 - 1.5 * iqr
upper_limit = q3 + 1.5 * iqr
df = df[(df['Age'] >= lower_limit) & (df['Age'] <= upper_limit)]
sns.boxplot(df["Age"])

sns.boxplot(df["Price"])
q1, q3 = df['Price'].quantile([0.25,0.75])
iqr = q3 - q1
lower_limit = q1 - 1.5 * iqr
upper_limit = q3 + 1.5 * iqr
df = df[(df['Price'] >= lower_limit) & (df['Price'] <= upper_limit)]
sns.boxplot(df["Price"])
```
![Screenshot 2024-11-27 211222](https://github.com/user-attachments/assets/0346746d-457a-4a2f-96f2-e3ac8d8f0f3b)
![Uploading Screenshot 2024-11-27 211242.png…]()               

## CATEGORICAL ANALYSIS
```
fuel_type_counts = df['FuelType'].value_counts()
print(fuel_type_counts)
fuel_type_counts.plot(kind='bar',color='pink')
plt.title('Count of Fuel Types')
plt.xlabel('Fuel Type')
plt.ylabel('Count')
plt.xticks(rotation=0)
plt.grid(axis='x', linestyle='solid', alpha=0.7)
plt.show()
```
![Screenshot 2024-11-27 211638](https://github.com/user-attachments/assets/0574c498-55d4-404a-b4d9-db52ecdd475d)
![Screenshot 2024-11-27 211728](https://github.com/user-attachments/assets/ed00923c-fb7b-42d8-a2b4-b380cb933361)
## BIVARIATE AND MULTIVARIATE ANALYSIS
```
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Age', y='Price', hue='FuelType', data=df)
plt.title('Bivariate Analysis: Age vs. Price by Fuel Type')
plt.xlabel('Age')
plt.ylabel('Price')
plt.show()

sns.pairplot(df[['Age', 'Price', 'KM', 'FuelType']], hue='FuelType')
plt.show()
```
## ENCODING & FEATURE TRANSFORMATION
```
from sklearn.preprocessing import LabelEncoder
le=LabelEncoder()
df['FuelType']=le.fit_transform(df['FuelType'])
df['FuelType']
df.tail()
df=pd.read_csv("Toyota.csv",index_col=0,na_values=["??","????"])
df["MetColor"]=df["MetColor"].astype('object')
df["Automatic"]=df['Automatic'].astype('object')
print(np.unique(df['Doors']))
df['Doors'].replace("three",3,inplace=True)
df['Doors'].replace("four",4,inplace=True)
df['Doors'].replace("five",5,inplace=True)
df['Doors']

df.skew()
np.log(df["KM"] )
```
LABEL ENCODER
![Screenshot 2024-11-27 212129](https://github.com/user-attachments/assets/5e0f8174-7cf8-4752-9577-c3b06737313b)


FEATURE TRANSFORMATION
![Screenshot 2024-11-27 212152](https://github.com/user-attachments/assets/f2f8fe06-a93e-4532-bda2-0822ca8b51a4)


BEFORE :
![Screenshot 2024-11-27 212215](https://github.com/user-attachments/assets/50ab7b44-16bc-487f-8c41-e65b39237c64)

AFTER :
![Screenshot 2024-11-27 212240](https://github.com/user-attachments/assets/21263be2-077b-4904-ae65-319e83546c2c)


## DATA VISUALIZATION
```
sns.violinplot(x='Age', y='FuelType', data=df)
plt.show()

dfc['FuelType'] = dfc['FuelType'].astype('category')
dfc['FuelType'] = dfc['FuelType'].cat.codes
data = dfc.drop(columns=['Automatic'])
sns.heatmap(data.corr(), annot=True, fmt='.2f')
plt.title('Correlation Heatmap')
plt.show()
```
![Screenshot 2024-11-27 212333](https://github.com/user-attachments/assets/4b3dd294-29e3-423d-a9f6-e77534be78ab)





## RESULT:
Thus Data analysis and Data preprocessing implemeted using a dataset.
