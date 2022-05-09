# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file

# CODE

## Encoding Data.csv
~~~
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

from sklearn.preprocessing  import LabelEncoder , OrdinalEncoder
from sklearn.preprocessing import StandardScaler as sc
from category_encoders import BinaryEncoder
be=BinaryEncoder()
data1=be.fit_transform(df["bin_1"])
data1

df2=df.copy()
be1=BinaryEncoder()
data2=be1.fit_transform(df2["bin_2"])
df2["bin_2"]=be1.fit_transform(df2[["bin_2"]])
df2

df3=df2.copy()
oe=OrdinalEncoder()
oe.fit_transform(df3[["ord_2"]])

df3
le=LabelEncoder()
df4=df3.copy()
le.fit_transform(df4[["nom_0"]])
df4["nom_0"]=le.fit_transform(df4[["nom_0"]])
df4

from category_encoders import BinaryEncoder
be=BinaryEncoder()
be.fit_transform(df4[["bin_1"]])
df4

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df5=pd.DataFrame(ss.fit_transform(df4),columns=['id','bin_1','bin_2','nom_0','ord_2'])
df5
~~~
# Data.csv
~~~
import pandas as pd
df=pd.read_csv("data.csv")
df

df1=df.copy()
be=BinaryEncoder()
be.fit_transform(df1[["bin_1"]])
df1["bin_1"]=be.fit_transform(df1[["bin_1"]])
df1

df2=df1.copy()
be2=BinaryEncoder()
be2.fit_transform(df2[["bin_2"]])
df2["bin_2"]=be2.fit_transform(df2[["bin_2"]])
df2

df3=df2.copy()
le=LabelEncoder()
le.fit_transform(df3[["City"]])
df3["City"]=le.fit_transform(df3[["City"]])
oe=OrdinalEncoder()

df4=df3.copy()
df4["Ord_1"]=oe.fit_transform(df4[["Ord_1"]])
df4

df5=df4.copy()
df5["Ord_2"]=oe.fit_transform(df5[["Ord_2"]])
df5

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df6=pd.DataFrame(ss.fit_transform(df5),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df6

from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df7=pd.DataFrame(scaler.fit_transform(df6),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df7

from sklearn.preprocessing import MaxAbsScaler
maxabsscaler=MaxAbsScaler()
df8=pd.DataFrame(maxabsscaler.fit_transform(df7),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df8

from sklearn.preprocessing import RobustScaler
rscaler = RobustScaler()
df9=pd.DataFrame(rscaler.fit_transform(df8),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df9
~~~
# Titanic Data set
~~~
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

del df["Name"]
del df["Cabin"]
del df["Ticket"]
df

df1=df.copy()
from sklearn.preprocessing  import LabelEncoder , OrdinalEncoder
from sklearn.preprocessing import StandardScaler as sc
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Age"]=df["Age"].fillna(df["Age"].median())
df

df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df

oe=OrdinalEncoder ()
oe.fit_transform(df[["Embarked"]])

embark=['S','C','Q']
emb=OrdinalEncoder(categories=[embark])
emb

emb.fit_transform(df[['Embarked']])
df["Embarked"]=emb.fit_transform(df[["Embarked"]])
df

be=BinaryEncoder()
newdata=be.fit_transform(df1["Sex"])
newdata

from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df2=pd.DataFrame(scaler.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df3=pd.DataFrame(ss.fit_transform(df2),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
maxabsscaler=MaxAbsScaler()
df4=pd.DataFrame(maxabsscaler.fit_transform(df3),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
rscaler = RobustScaler()
df5=pd.DataFrame(rscaler.fit_transform(df4),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
~~~
# OUPUT

![1](https://user-images.githubusercontent.com/94980741/167471878-3f6b6ae0-c454-48a3-8dfc-49f663544664.png)
![2](https://user-images.githubusercontent.com/94980741/167471914-197cede4-9427-4476-b3ba-82acf007b94c.png)
![3](https://user-images.githubusercontent.com/94980741/167471939-018f2e1c-35c8-44cd-bc74-1204ba21c80b.png)
![4](https://user-images.githubusercontent.com/94980741/167471955-65d21d0e-fc50-46b3-aee0-8027d2f0601c.png)
![5](https://user-images.githubusercontent.com/94980741/167471971-b398b63b-ee6b-4a80-9445-8bbb15088497.png)
![6](https://user-images.githubusercontent.com/94980741/167471982-e2d0ca27-184a-4900-bd33-ffb31a049e0f.png)

# Data.csv
![7](https://user-images.githubusercontent.com/94980741/167472292-177b9684-c034-4ecf-b870-4cc960781e4f.png)
![8](https://user-images.githubusercontent.com/94980741/167472306-742eddab-d52f-400e-a1a2-392c5458d1f4.png)
![9](https://user-images.githubusercontent.com/94980741/167472319-90906fae-40c5-4861-b563-14d83be84728.png)
![10](https://user-images.githubusercontent.com/94980741/167472338-98a702cd-7ccd-442d-9a54-d3c5cca1f1c9.png)
![11](https://user-images.githubusercontent.com/94980741/167472357-f084172e-1dc6-4a6b-ac9c-b13a237e3035.png)

![12](https://user-images.githubusercontent.com/94980741/167472368-160131b4-d36a-4f81-b37c-7c01fa566d27.png)
![13](https://user-images.githubusercontent.com/94980741/167472407-99920a3a-d7b9-4070-aa7b-6429b98e7486.png)
![14](https://user-images.githubusercontent.com/94980741/167472427-b15da776-fb16-4179-9ef3-7407a399b2ce.png)

# Titanic.csv
![15](https://user-images.githubusercontent.com/94980741/167472622-c4a04f8f-4849-4b86-8eef-2d62febb4c8b.png)
![16](https://user-images.githubusercontent.com/94980741/167472671-9f8b849d-ba6d-4e75-8a73-c96c46339600.png)
![17](https://user-images.githubusercontent.com/94980741/167472697-41a81c5e-8961-4ce7-b8e2-a35e9bba2bee.png)
![19](https://user-images.githubusercontent.com/94980741/167472740-e01c1837-90db-49f1-ac4b-2764f4a56849.png)
![20](https://user-images.githubusercontent.com/94980741/167472771-2449e19f-6f88-4acb-8e16-a56bf60f8685.png)
![18](https://user-images.githubusercontent.com/9498074![21](https://user-images.githubusercontent.com/94980741/167472799-f4003435-c1a8-49bb-82a8-97def31b864f.png)
![21](https://user-images.githubusercontent.com/94980741/167472876-1ac62be1-4d7b-46aa-8825-48deaa248c25.png)

# Result:
The given data and perform Feature Generation process and save the data to a file has been successfully read.

