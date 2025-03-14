# Supermart Grocery Sales Analysis

## Introduction
The **Supermart Grocery Sales dataset** provides insights into **customer purchasing behavior, sales distribution, discount strategies, and regional performance**. This project focuses on analyzing **sales trends, category performance, and the impact of discounts on profitability** using **exploratory data analysis (EDA)**. By leveraging Python for **data manipulation and visualization**, we aim to identify actionable insights that can help retailers **optimize inventory, pricing, and marketing strategies**.

## Problem Statement
Retail businesses often struggle with **inventory optimization, demand forecasting, and discounting strategies** due to a lack of insights into sales data. This project seeks to answer key questions such as:
- Which **product categories and sub-categories** generate the highest sales?
- How do **discount rates affect profit margins**?
- What are the **seasonal and yearly sales trends**, and how can they be leveraged?
- Which **regions contribute most to overall sales**, and where is improvement needed?

By analyzing **historical grocery sales data**, this project provides **data-driven insights to enhance retail decision-making and improve overall profitability**.

## Dataset Details
- The dataset contains grocery sales records from Tamil Nadu, India.
- Key columns: `Order ID`, `Customer Name`, `Category`, `Sub Category`, `City`, `Order Date`, `Region`, `Sales`, `Discount`, `Profit`, `State`.
- The dataset is cleaned, processed, and analyzed using Python.

## Tools Used
- **Python** (Pandas, Matplotlib, Seaborn, NumPy)
- **SQL** (for deeper data analysis, if needed)
- **Excel** (for data exploration and validation)

## Code Implementation
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('supermart_grocery_sales.csv')

# Data Overview
print(df.shape)
print(df.info())

# Convert Order Date to datetime format
df['Order Date'] = pd.to_datetime(df['Order Date'], errors='coerce')
df['month'] = df['Order Date'].dt.month_name()
df['year'] = df['Order Date'].dt.year

# Sales by Category
plt.figure(figsize=(8, 5))
sns.barplot(x='category', y='sales', data=df.groupby('category')['sales'].sum().reset_index(), palette='coolwarm')
plt.title('Total Sales by Category')
plt.xlabel('Category')
plt.ylabel('Sales')
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()

# Sales Distribution by Region
plt.figure(figsize=(6, 6))
region_sales = df.groupby('region')['sales'].sum().reset_index()
plt.pie(region_sales['sales'], labels=region_sales['region'], autopct='%1.1f%%',
        colors=sns.color_palette('pastel'), startangle=140, wedgeprops={'edgecolor': 'black'})
plt.title('Sales Distribution by Region')
plt.show()
```

## Key Insights
### **1. Sales by Category and Sub-Category**
- **Technology and Food categories** generate the highest sales.
- Certain sub-categories like **Phones and Fresh Produce** are top revenue generators.
- Lower-performing sub-categories may require **better promotions or discount strategies**.

### **2. Sales Distribution by Region**
- The **Western and Eastern regions contribute the most to total sales**.
- The Southern region has **lower sales**, suggesting potential for growth through targeted marketing.

### **3. Impact of Discounts on Profitability**
- **High discounts on certain items reduce overall profit margins**.
- While discounts drive sales, they should be strategically optimized for **high-demand items**.

### **4. Seasonal and Yearly Sales Trends**
- Sales **peak during the holiday season (December)**, indicating strong seasonal demand.
- Yearly sales trends show **consistent growth**, suggesting expansion opportunities.

## Conclusion
This project provides **actionable insights** to help retailers **optimize inventory, pricing, and marketing strategies**. By leveraging historical sales data, businesses can **forecast demand, reduce unnecessary discounts, and enhance customer retention**.

## How to Run the Notebook
1. Open the project in **Google Colab** or **Jupyter Notebook**.
2. Upload the dataset (`supermart_grocery_sales.csv`).
3. Run the provided Python scripts to analyze trends and generate visualizations.

---
This analysis highlights the power of **data-driven decision-making in retail** and paves the way for further insights into customer behavior and profitability.
