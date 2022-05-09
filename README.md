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

~~
# CODE

#Encoding Data .csv
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

# OUPUT
