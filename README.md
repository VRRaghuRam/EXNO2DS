# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT

```

# STEP 1: Import Libraries

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load Dataset
df = pd.read_csv("titanic_dataset.csv")


# STEP 2: Handle Missing Values

df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
df.drop('Cabin', axis=1, inplace=True)


# STEP 3: Analyze Outliers Using Boxplot

sns.boxplot(y=df['Age'])
plt.title("Age Boxplot")
plt.show()

sns.boxplot(y=df['Fare'])
plt.title("Fare Boxplot")
plt.show()


# STEP 4: Remove Outliers Using IQR

for col in ['Age', 'Fare']:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    df = df[(df[col] >= Q1 - 1.5 * IQR) &
            (df[col] <= Q3 + 1.5 * IQR)]


# STEP 5: Countplot

sns.countplot(data=df, x='Sex')
plt.show()

sns.countplot(data=df, x='Survived')
plt.show()


# STEP 6: Displot

sns.displot(df['Age'], kde=True)
plt.show()

sns.displot(df['Fare'], kde=True)
plt.show()


# STEP 7: Cross Tabulation

print(pd.crosstab(df['Sex'], df['Survived']))
print(pd.crosstab(df['Pclass'], df['Survived']))


# STEP 8: Heatmap

sns.heatmap(df.select_dtypes(include='number').corr(),
            annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
```
<img width="572" height="411" alt="image" src="https://github.com/user-attachments/assets/f2fa25fa-e22a-4110-bc80-422326efc150" />
<img width="581" height="411" alt="image" src="https://github.com/user-attachments/assets/fce59680-2f96-47ca-8dc4-2278ec185410" />
<img width="581" height="463" alt="image" src="https://github.com/user-attachments/assets/5fda0ff3-a331-4270-a0e7-90be4826d59c" />
<img width="581" height="445" alt="image" src="https://github.com/user-attachments/assets/ec70cbfb-b269-4f00-bb62-5e8d900a70b2" />
<img width="484" height="484" alt="image" src="https://github.com/user-attachments/assets/7e464790-2b86-4de4-8839-8d275473f7bb" />
<img width="484" height="484" alt="image" src="https://github.com/user-attachments/assets/85eaf9df-9c09-4e10-8141-a5824d061a15" />
<img width="396" height="342" alt="image" src="https://github.com/user-attachments/assets/98e558bb-3838-42e3-abd8-8b4f411f3c08" />
<img width="616" height="518" alt="image" src="https://github.com/user-attachments/assets/83bf31df-859e-4a0a-af57-c18f95075f3e" />



# RESULT   
Thus, the Titanic dataset was successfully analyzed and visualized using Python.
