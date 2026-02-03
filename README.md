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

import pandas as pd
science=pd.read_csv("/content/SAMPLEIDS.csv")
science

<img width="867" height="713" alt="image" src="https://github.com/user-attachments/assets/08f152ae-b89c-4086-86f4-d42cbc253bac" />

science.head()

<img width="702" height="180" alt="image" src="https://github.com/user-attachments/assets/830236eb-c585-4401-bc5d-f420c5bcd6a2" />

science.tail()

<img width="704" height="167" alt="image" src="https://github.com/user-attachments/assets/e93e4920-6308-4612-b425-699e3096dd8e" />

science.info()

<img width="327" height="283" alt="image" src="https://github.com/user-attachments/assets/f55a732d-26f9-4cde-a6dd-05f37bba6066" />

science.describe()

<img width="645" height="259" alt="image" src="https://github.com/user-attachments/assets/2136024c-7a30-45fe-bc4f-560671733510" />

science.isnull().sum()

<img width="165" height="381" alt="image" src="https://github.com/user-attachments/assets/139fa157-bbaa-400f-b905-2241f65ca068" />

science.isnull()

<img width="579" height="584" alt="image" src="https://github.com/user-attachments/assets/b5c870cf-e6ff-48d5-899b-6156725187c6" />


science.isnull().any()

<img width="156" height="371" alt="image" src="https://github.com/user-attachments/assets/eaf95b34-4e0f-420f-8ada-11724842d354" />

science.isnull().sum()

<img width="153" height="371" alt="image" src="https://github.com/user-attachments/assets/79c3b598-cc36-4d6b-bf32-2ccaa6b6afe7" />

science.dropna()

<img width="716" height="397" alt="image" src="https://github.com/user-attachments/assets/cd9c196a-d7bf-417d-942f-3cf43e3b0add" />

science.dropna(axis=1)

<img width="230" height="592" alt="image" src="https://github.com/user-attachments/assets/fffa8557-1cb7-47f9-961b-3ff582e8a5f7" />


science.fillna(3)

<img width="707" height="621" alt="image" src="https://github.com/user-attachments/assets/34e129da-01d2-4b8a-8dec-b070ccb9d2bf" />

science.fillna(method='ffill')

<img width="711" height="628" alt="image" src="https://github.com/user-attachments/assets/aaa99434-6c2b-4e05-a753-9be6c096ecf6" />


science.fillna(method='bfill')

<img width="711" height="630" alt="image" src="https://github.com/user-attachments/assets/f1e95625-1e7b-4778-86d2-12d6776163f1" />


science.fillna({'GENDER':'MALE','NAME':'SRI'})

<img width="727" height="590" alt="image" src="https://github.com/user-attachments/assets/62bc3d28-b8ae-4525-9c7e-46bfd4ff6bca" />


df=pd.read_csv("/content/iris.csv")
df

<img width="475" height="346" alt="image" src="https://github.com/user-attachments/assets/a7c158dd-0231-412d-8d01-366d5280d183" />

df.describe()

<img width="423" height="271" alt="image" src="https://github.com/user-attachments/assets/3efefb00-3fbc-430c-9410-b0fcdfd788ab" />

df.isnull()

<img width="476" height="340" alt="image" src="https://github.com/user-attachments/assets/de6dc807-cfc3-4f04-97e6-31ed5304da53" />

df.isnull().any()

<img width="172" height="203" alt="image" src="https://github.com/user-attachments/assets/8fb73024-e15b-4e88-8c16-0c0b9f024776" />

import seaborn as sns
sns.boxplot(x='sepal_width',data=df)

<img width="495" height="382" alt="image" src="https://github.com/user-attachments/assets/4e84ba54-00c0-4a63-9374-97a0a766b354" />


Q1=df.sepal_width.quantile(0.25)
Q3=df.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)

<img width="80" height="33" alt="image" src="https://github.com/user-attachments/assets/42a50b5d-0e85-4b73-a814-8f54b4639e00" />

ran=df[~((df.sepal_width<(Q1-1.5*IQR))|(df.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']

<img width="172" height="180" alt="image" src="https://github.com/user-attachments/assets/1bb64429-819e-43dc-927f-b9a26380baef" />


sns.boxplot(x='sepal_width',data=ran)

<img width="161" height="342" alt="image" src="https://github.com/user-attachments/assets/e92228cd-8323-49f4-b258-2bb02fad71d7" />


import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(df['petal_length']))
z

<img width="495" height="445" alt="image" src="https://github.com/user-attachments/assets/6b870586-3558-485c-83bf-a32bf44f0bea" />

ir1=df[z<3]
ir1

<img width="466" height="350" alt="image" src="https://github.com/user-attachments/assets/fa1af3cb-883a-4e0b-b271-a185dc462a05" />



# Result

Thus the given data successfully performed data cleaning and saved the cleaned data to a file
