# Coffee-Sales-
Data Analysis Project 
<br>
Author - Akanksha 

import pandas as pd
data = pd.read_excel("coffee_sales.xlsx")
print(data.head())
print(data.isnull().sum())
#fill missing catagoies values with the mode
data['card'].fillna(data['card'].mode()[0], inplace=True)
#Convert Date to datetime type
data['date'] = pd.to_datetime(data['date'])
# Check the data types
print(data.dtypes)
import numpy as np
# Remove outliers based on Z-score
from scipy.stats import zscore
data = data[(np.abs(zscore(data[['date', 'datetime','cash_type','card','money','coffee_name']])) < 6).all(axis=1)]
# Extract month and year from the Date
data['Month'] = data['date'].dt.month
data['Year'] = data['date'].dt.year
# Drop the original Date column
data.drop(columns=['date'], inplace=True)
import matplotlib.pyplot as plt
import seaborn as sns
# Sales over time
plt.figure(figsize=(10, 6))
sns.lineplot(data=data, x='Month', y='money', hue='Year')
plt.title('Monthly Sales Over Years')
plt.show()
# Sales by card
plt.figure(figsize=(10, 6))
sns.barplot(data=data, x='card', y='money')
plt.title('Sales by card')
plt.show()
# Sales by coffee_name
plt.figure(figsize=(10, 6))
sns.barplot(data=data, x='coffee_name', y='money')
plt.title('Sales by coffee_name')
plt.show()
from sklearn.model_selection import train_test_split
# Define features and target variable
X = data.drop(columns=['money'])
y = data['money']
import pandas as pd 
df = pd.read_excel("coffee_sales.xlsx")
print(df)
plt. show ()
