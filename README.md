# Coffee-Sales-
Data Analysis Project 
<br>
Author - Akanksha 
<br> 
#Import libraries 
import pandas as pd
<br>
data = pd.read_excel("coffee_sales.xlsx")
<br>
print(data.head())
<br>
print(data.isnull().sum())
<br>
#fill missing catagoies values with the mode
<br>
data['card'].fillna(data['card'].mode()[0], inplace=True)
<br>
#Convert Date to datetime type
<br>
data['date'] = pd.to_datetime(data['date'])
<br>
# Check the data types
<br>
print(data.dtypes)
<br>
import numpy as np
<br>
# Remove outliers based on Z-score
<br>
from scipy.stats import zscore
<br>
data = data[(np.abs(zscore(data[['date', 'datetime','cash_type','card','money','coffee_name']])) < 6).all(axis=1)]
<br>
# Extract month and year from the Date
<br>
data['Month'] = data['date'].dt.month
<br>
data['Year'] = data['date'].dt.year
<br>
# Drop the original Date column
<br>
data.drop(columns=['date'], inplace=True)
<br>
import matplotlib.pyplot as plt
<br>
import seaborn as sns
<br>
# Sales over time
<br>
plt.figure(figsize=(10, 6))
<br>
sns.lineplot(data=data, x='Month', y='money', hue='Year')
<br>
plt.title('Monthly Sales Over Years')
<br>
plt.show()
<br>
# Sales by card
<br>
plt.figure(figsize=(10, 6))
<br>
sns.barplot(data=data, x='card', y='money')
<br>
plt.title('Sales by card')
<br>
plt.show()
<br>
# Sales by coffee_name
<br>
plt.figure(figsize=(10, 6))
<br>
sns.barplot(data=data, x='coffee_name', y='money')
<br>
plt.title('Sales by coffee_name')
<br>
plt.show()
<br>
from sklearn.model_selection import train_test_split
<br>
# Define features and target variable
<br>
X = data.drop(columns=['money'])
<br>
y = data['money']
<br>
import pandas as pd 
<br>
df = pd.read_excel("coffee_sales.xlsx")
<br>
print(df)
<br>
pt. show ()
