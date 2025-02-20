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


# CODE:
```python
Name : s.thirisha
Register Number : 212222230160
**Feature Generation - Encoding Data.csv**
import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/Encoding Data.csv")
df1 = df.copy()
df1.head(5)
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
climate = ['Cold','Warm','Hot']
enc = OrdinalEncoder(categories = [climate])
enc.fit_transform(df1[["ord_2"]])
df1['Ord_2'] = enc.fit_transform(df1[["ord_2"]])
df1.head(5)
df2 = df1.copy()
le = LabelEncoder()
df2['Nom_0'] = le.fit_transform(df2[["nom_0"]])
df2.head(5)
df3 = df2.copy()
from category_encoders import BinaryEncoder
be = BinaryEncoder()
data = be.fit_transform(df['bin_1'])
df3  = pd.concat([df,data],axis=1)
df3.head(5)
df4 = df3.copy()
from category_encoders import BinaryEncoder
be1 = BinaryEncoder()
newdata = be.fit_transform(df['bin_2'])
df4  = pd.concat([df,newdata],axis=1)
df4.head(5)
df['ord_2'] = le.fit_transform(df['ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(df['ord_2'])

**Feature Generation - data.csv**
import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/data.csv")
df.head(5)
df.info()
df.isnull().sum()
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['Ord_2'] = le.fit_transform(df['Ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(df['Ord_2'])
from sklearn.preprocessing import OneHotEncoder
enc = OneHotEncoder()
enc = enc.fit_transform(df[['City']]).toarray()
encoded_colm = pd.DataFrame(enc)
df = pd.concat([df, encoded_colm], axis=1)
df = df.drop(['City'], axis=1)
df.head(10)
df = pd.get_dummies(df, prefix=['Ord_2'], columns=['Ord_2'])
df.head(10)
df = pd.get_dummies(df, prefix=['Ord_1'], columns=['Ord_1'])
df.head(10)

**Feature Generation - titanic_dataset.csv**
import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/titanic_dataset.csv")
df.head(5)
df.info()
df.isnull().sum()
df['Age']=df['Age'] . fillna(df['Age'].mean())
df['Cabin']=df['Cabin']. fillna(df['Cabin']. mode() [0])
df['Embarked']=df['Embarked'] . fillna(df['Embarked'].mode( )[0])
df.isnull().sum()
from sklearn.preprocessing import LabelEncoder
lc = LabelEncoder()
df['Sex'] = lc.fit_transform(df['Sex'])
sbn.set(style ="darkgrid")
sbn.countplot(df['Sex'])
from sklearn.preprocessing import OneHotEncoder
enc= OneHotEncoder()
enc= enc.fit_transform(df[['Name']]).toarray()
encoded_colm = pd.DataFrame(enc)
df= pd.concat([df, encoded_colm], axis=1)
df= df.drop(['Name'], axis=1)
df.head(10)
df = pd.get_dummies(df, prefix=['Ticket'] ,columns=['Ticket'])
df.head(10)
df = pd.get_dummies(df, prefix=['Embarked'] ,columns=['Embarked'])
df.head(10)
```

# OUPUT:
![image](https://user-images.githubusercontent.com/120380280/232667837-7942ddce-557c-439e-9d92-d6db2f0c5175.png)
![image](https://user-images.githubusercontent.com/120380280/232667878-4ad9ac76-c1f7-4cfd-97fd-8437244b3f80.png)
![image](https://user-images.githubusercontent.com/120380280/232667979-a6306c14-189a-4031-a451-67a8bab42a97.png)
# Feature Generation - data.csv
![image](https://user-images.githubusercontent.com/120380280/232668079-c1182d6a-0a18-492d-b4f8-c0dc81f33939.png)
![image](https://user-images.githubusercontent.com/120380280/232668569-fee1dbbd-27a6-4590-8300-d4ced6e5c43d.png)
![image](https://user-images.githubusercontent.com/120380280/232668603-f1ea1bbd-882d-4922-a0bc-0a563e30b7bb.png)
![image](https://user-images.githubusercontent.com/120380280/232668631-1bede1ec-4b71-4e87-9eb9-d9ee12ca69a8.png)
# Feature Generation - titanic_dataset.csv
![image](https://user-images.githubusercontent.com/120380280/232668719-2e7fa230-ddf7-4cfe-a53a-22d02c66e1c2.png)
![image](https://user-images.githubusercontent.com/120380280/232668753-733ec7f7-751b-47c3-9048-607ecdc05109.png)
![image](https://user-images.githubusercontent.com/120380280/232668785-23eac213-0cff-4586-aba2-77ed9f4d4d1d.png)
![image](https://user-images.githubusercontent.com/120380280/232668824-bbe37963-6a4f-4e6f-8e1a-6da6ff13dc5f.png)

# RESULT:
Thus the Feature Generation for the given datasets had been executed successfully



