# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
~~~    
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
~~~


<img width="1028" height="851" alt="image" src="https://github.com/user-attachments/assets/44db0541-7080-4ece-86d5-060adfd2b17c" />



~~~
df.head()
~~~


<img width="993" height="229" alt="image" src="https://github.com/user-attachments/assets/3468091b-7ca5-4108-bffa-0c6d2ca67535" />



~~~
df.tail()
~~~


<img width="1015" height="244" alt="image" src="https://github.com/user-attachments/assets/5e34e305-dfc7-438e-8d22-cb1e2ea9c90d" />


~~~
df.isnull()
~~~


<img width="809" height="852" alt="image" src="https://github.com/user-attachments/assets/c41e71e1-238f-40ab-afb4-0e68b9542b52" />


~~~
df.notnull()
~~~


<img width="815" height="856" alt="image" src="https://github.com/user-attachments/assets/0f41872f-004b-4dfc-928e-95c09ea502a7" />


~~~
df.isnull().sum()
~~~



<img width="174" height="544" alt="image" src="https://github.com/user-attachments/assets/fb10d266-c9da-41dd-a7d1-4a43fb53b15a" />


~~~
df.isnull().any()
~~~


<img width="206" height="559" alt="image" src="https://github.com/user-attachments/assets/2cf1275e-594b-4d52-ab19-9949849bc4dc" />


~~~
df.dropna()
~~~



<img width="1024" height="547" alt="image" src="https://github.com/user-attachments/assets/e8bd5c58-6529-4ec8-b1ad-aa1fdf7a51a6" />


~~~
df.dropna(axis=0)
~~~



<img width="1023" height="549" alt="image" src="https://github.com/user-attachments/assets/6d1aed9e-8545-4acc-9e1b-f5578780172b" />


~~~
df.dropna(axis=1)
~~~



<img width="284" height="858" alt="image" src="https://github.com/user-attachments/assets/79c0e29a-1385-47ec-9cf9-2bb64bf0d59f" />



~~~
df.fillna(5)
~~~



<img width="1011" height="855" alt="image" src="https://github.com/user-attachments/assets/b1b013f6-9527-44c5-a8a9-c9f96f9857db" />



~~~
df.fillna(method='ffill')
~~~


<img width="1013" height="848" alt="image" src="https://github.com/user-attachments/assets/8e4bfbd6-788a-4db2-8009-9a14abb7fdbb" />


~~~
df.fillna(method='bfill')
~~~


<img width="1007" height="859" alt="image" src="https://github.com/user-attachments/assets/b0df141f-bdc6-4acb-85c4-e92c0ca80f8a" />


~~~
df.fillna({'GENDER':'FEMALE','NAME':'JAY'})
~~~


<img width="1013" height="851" alt="image" src="https://github.com/user-attachments/assets/7497b152-fe1a-4dfe-86b4-2fa57287b22e" />


~~~
ir=pd.read_csv('iris.csv')
ir
~~~



<img width="654" height="511" alt="image" src="https://github.com/user-attachments/assets/c89dfba8-b2c6-464c-a36d-6ca42a36ffbb" />


~~~
ir.describe()
~~~



<img width="583" height="354" alt="image" src="https://github.com/user-attachments/assets/aa823973-a7f0-4181-9fa0-a3f9b775d566" />


~~~
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
~~~


<img width="671" height="573" alt="image" src="https://github.com/user-attachments/assets/fce19189-a691-46ce-9453-e6e496e2715d" />


~~~
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
IQR=q3-q1
print(IQR)
~~~


<img width="80" height="42" alt="image" src="https://github.com/user-attachments/assets/d52fe6b9-3075-4ac6-a379-a4ff15297ef5" />


~~~
rid=ir[((ir.sepal_width)<(q1-1.5*IQR))|((ir.sepal_width)>(q3+1.5*IQR))]
rid['sepal_width']
~~~


<img width="210" height="250" alt="image" src="https://github.com/user-attachments/assets/93cce43e-244c-411d-b057-70f747966240" />


~~~
delid=ir[~((ir.sepal_width<(q1-1.5*IQR))|(ir.sepal_width>(q3+1.5*IQR)))]
delid
~~~


<img width="659" height="511" alt="image" src="https://github.com/user-attachments/assets/578264dc-93fc-4de1-b28f-40e99deea29f" />


~~~
sns.boxplot(x='sepal_width',data=delid)
~~~


<img width="669" height="565" alt="image" src="https://github.com/user-attachments/assets/544144d6-c5b3-49bd-8cf4-f1abfb733617" />


~~~
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['sepal_width']))
z
~~~


<img width="651" height="663" alt="image" src="https://github.com/user-attachments/assets/fe7d2eec-4d06-44b9-bc7a-3444435d983b" />


~~~
ir1=ir[z<3]
ir1
~~~


<img width="662" height="509" alt="image" src="https://github.com/user-attachments/assets/6aaddc37-b53a-43dc-9e11-0f5789f35282" />


         
# Result
      
      Thus, the program for data cleaning using python has executed successfully
