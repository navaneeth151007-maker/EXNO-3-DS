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
from sklearn.preprocessing import LabelEncoder, OneHotEncoder, StandardScaler, MinMaxScaler, PowerTransformer
data = pd.read_csv(r"E:\Data_to_Transform.csv")
print(data.head())
print(data.info())

```
<img width="838" height="607" alt="image" src="https://github.com/user-attachments/assets/b4968585-b47c-469e-944a-b709b3b37ace" />

```
categorical_cols = data.select_dtypes(include=['object']).columns
numerical_cols = data.select_dtypes(include=np.number).columns

print( list(categorical_cols))
print( list(numerical_cols))

```
<img width="1172" height="88" alt="image" src="https://github.com/user-attachments/assets/166afe0c-e902-4411-bed3-94954630ba37" />

```
le = LabelEncoder()
label_encoded_data = data.copy()

for col in categorical_cols:
    label_encoded_data[col + '_LabelEncoded'] = le.fit_transform(label_encoded_data[col])

print(label_encoded_data.head())

```
<img width="772" height="342" alt="image" src="https://github.com/user-attachments/assets/b31285e5-e4bf-4d86-9b01-f061ccea9ae0" />

```
onehot_encoded_data = pd.get_dummies(data, columns=categorical_cols, drop_first=True)
print(onehot_encoded_data.head())
```
<img width="815" height="350" alt="image" src="https://github.com/user-attachments/assets/8c435668-a021-4301-b172-c6cc07d5de5d" />

```
scaler = StandardScaler()
standardized_data = onehot_encoded_data.copy()
standardized_data[numerical_cols] = scaler.fit_transform(standardized_data[numerical_cols])
print(standardized_data.head())
```
<img width="863" height="317" alt="image" src="https://github.com/user-attachments/assets/cbf09598-148d-420e-9946-76c463d971fe" />

```
minmax = MinMaxScaler()
normalized_data = onehot_encoded_data.copy()
normalized_data[numerical_cols] = minmax.fit_transform(normalized_data[numerical_cols])
print(normalized_data.head())
```
<img width="1012" height="336" alt="image" src="https://github.com/user-attachments/assets/23c9cdbf-5895-4535-a111-48f51b4932b7" />

```
label_encoded_data.to_csv("LabelEncoded_Data.csv", index=False)
onehot_encoded_data.to_csv("OneHotEncoded_Data.csv", index=False)
standardized_data.to_csv("Standardized_Data.csv", index=False)
normalized_data.to_csv("Normalized_Data.csv", index=False)
power_data.to_csv("PowerTransformed_Data.csv", index=False)

```
# RESULT
The above code and output for the Feature Encoding and Transformation
       

       
