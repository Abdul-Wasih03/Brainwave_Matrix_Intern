# Sales Data Analysis
## Overview
A comprehensive analysis of sales data using various types of visualizations. The dataset, retail_sales_dataset.csv, includes information on transactions, including transaction IDs, dates, customer IDs, genders, ages, product categories, quantities, prices per unit, and total amounts.

### Dataset:
The dataset includes the following columns:

Transaction ID: Unique identifier for each transaction<br>
Date: Date of the transaction<br>
Customer ID: Unique identifier for each customer<br>
Gender: Gender of the customer<br>
Age: Age of the customer<br>
Product Category: Category of the product purchased<br>
Quantity: Number of units purchased<br>
Price per Unit: Price per unit of the product<br>
Total Amount: Total amount spent in the transaction<br>
Visualizations: The following visualizations have been created to analyze the sales data<br>

### 1. Sales Over Time
Type: Line Chart<br>
Description: Displays the total sales amount over time, showing how sales vary by date.<br>
### Code:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv('retail_sales_dataset.csv')

# Convert 'Date' to datetime format
df['Date'] = pd.to_datetime(df['Date'])

# Aggregate sales by date
sales_over_time = df.groupby('Date')['Total Amount'].sum().reset_index()

# Plot
plt.figure(figsize=(12, 6))
plt.plot(sales_over_time['Date'], sales_over_time['Total Amount'], marker='o')
plt.title('Sales Over Time')
plt.xlabel('Date')
plt.ylabel('Total Amount')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
### 2. Sales by Product Category
Type: Bar Chart<br>
Description: Shows total sales for each product category.<br>
### Code:
```python
import seaborn as sns

# Aggregate sales by product category
sales_by_category = df.groupby('Product Category')['Total Amount'].sum().reset_index()

# Plot
plt.figure(figsize=(10, 6))
sns.barplot(x='Total Amount', y='Product Category', data=sales_by_category, palette='viridis')
plt.title('Sales by Product Category')
plt.xlabel('Total Amount')
plt.ylabel('Product Category')
plt.tight_layout()
plt.show()
```

### 3. Sales by Gender
Type: Pie Chart<br>
Description: Visualizes the proportion of total sales by gender.<br>
### Code:
```python
# Aggregate sales by gender
sales_by_gender = df.groupby('Gender')['Total Amount'].sum().reset_index()

# Plot
plt.figure(figsize=(8, 8))
plt.pie(sales_by_gender['Total Amount'], labels=sales_by_gender['Gender'], autopct='%1.1f%%', colors=['#ff9999','#66b3ff'])
plt.title('Sales by Gender')
plt.show()
```
### 4. Sales by Age
Type: Bar Chart<br>
Description: Displays total sales for each age group.<br>
### Code:
```python
# Aggregate sales by age
sales_by_age = df.groupby('Age')['Total Amount'].sum().reset_index()

# Plot
plt.figure(figsize=(12, 6))
sns.barplot(x='Age', y='Total Amount', data=sales_by_age, palette='magma')
plt.title('Sales by Age')
plt.xlabel('Age')
plt.ylabel('Total Amount')
plt.grid(True)
plt.tight_layout()
plt.show()
```

### 5. Box Plot (Total Amount by Product Category)
Type: Box Plot<br>
Description: Shows the distribution and outliers of total amounts for each product category.<br>
### Code:
```python
# Box plot
plt.figure(figsize=(12, 6))
sns.boxplot(x='Product Category', y='Total Amount', data=df, palette='Set2')
plt.title('Box Plot of Total Amount by Product Category')
plt.xlabel('Product Category')
plt.ylabel('Total Amount')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### 6. Scatter Plot (Total Amount vs. Quantity)
Type: Scatter Plot<br>
Description: Visualizes the relationship between total amount and quantity, color-coded by product category.<br>
### Code:
``` python
# Scatter plot
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Quantity', y='Total Amount', data=df, hue='Product Category', palette='viridis', alpha=0.7)
plt.title('Scatter Plot of Total Amount vs. Quantity')
plt.xlabel('Quantity')
plt.ylabel('Total Amount')
plt.legend(title='Product Category')
plt.grid(True)
plt.tight_layout()
plt.show()
```
### 7. Violin Plot (Total Amount by Age)
Type: Violin Plot<br>
Description: Illustrates the distribution of total amounts across different age groups.<br>
### Code:
```python
# Violin plot
plt.figure(figsize=(12, 6))
sns.violinplot(x='Age', y='Total Amount', data=df, palette='magma')
plt.title('Violin Plot of Total Amount by Age')
plt.xlabel('Age')
plt.ylabel('Total Amount')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### 8. Heatmap of Sales by Product Category and Gender
Type: Heatmap<br>
Description: Shows the intensity of total sales across different product categories and genders.<br>
### Code:
```python
import numpy as np

# Pivot table for heatmap
heatmap_data = df.pivot_table(index='Product Category', columns='Gender', values='Total Amount', aggfunc=np.sum)

# Heatmap plot
plt.figure(figsize=(10, 8))
sns.heatmap(heatmap_data, annot=True, cmap='YlGnBu', fmt='.0f')
plt.title('Heatmap of Total Amount by Product Category and Gender')
plt.xlabel('Gender')
plt.ylabel('Product Category')
plt.tight_layout()
plt.show()
```

## Result:
Thus, to perform Sales data analysis of a commercial store is successful.


## For a detailed analysis and visualizations, please refer to the attached Jupyter Notebook file.

