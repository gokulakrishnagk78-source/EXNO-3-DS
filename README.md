## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
import numpy as np
from sklearn.preprocessing import PowerTransformer


df = pd.read_csv("C:\\Users\\krishna\\Downloads\\Encoding Data.csv")


df.drop_duplicates(inplace=True)           
df.dropna(inplace=True)                    



df['bin_1'] = df['bin_1'].map({'F': 0, 'T': 1})
df['bin_2'] = df['bin_2'].map({'N': 0, 'Y': 1})


df = pd.get_dummies(df, columns=['nom_0'])


ord_map = {'Cold': 0, 'Warm': 1, 'Hot': 2}
df['ord_2'] = df['ord_2'].map(ord_map)


df['ord_2_log'] = np.log1p(df['ord_2'])


df['ord_2_sqrt'] = np.sqrt(df['ord_2'])


pt = PowerTransformer(method='yeo-johnson')
df['ord_2_yeo'] = pt.fit_transform(df[['ord_2']])


df.to_csv("Cleaned_Data_set.csv", index=False)
print("Data cleaning, encoding, transformation complete. Saved as 'Cleaned_Data_set.csv'.")
```
#OUTPUT :
![Screenshot_17-10-2025_11319_localhost](https://github.com/user-attachments/assets/a1c0995f-ed11-4dc7-a68f-5f2332c3dcd8)
![Screenshot_17-10-2025_11231_localhost](https://github.com/user-attachments/assets/3622f967-3fee-4490-80b6-f7b66b871eb9)



# RESULT:
       
given data set is cleaned ,encoded and transformed successfully.
       
