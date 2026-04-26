# 🛒 Zepto E-commerce SQL Data Analyst Portfolio Project
This is a complete, real-world data analyst portfolio project based on an e-commerce inventory dataset scraped from [Zepto](https://www.zeptonow.com/) — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.

This project is perfect for:
- 📊 Data Analyst aspirants who want to build a strong **Portfolio Project** for interviews and LinkedIn
- 📚 Anyone learning SQL hands-on
- 💼 Preparing for interviews in retail, e-commerce, or product analytics

# **🎥 Watch this [YouTube video](https://www.youtube.com/watch?v=x8dfQkKTyP0&list=PLAx-M6Di0SisFJ1rv5M_FRHUlGA5rtUf_&index=2) to implement the full project from scratch:**  
[![SQL Data Analyst Portfolio Project using Zepto Inventory Dataset](https://github.com/user-attachments/assets/a1895ada-15e4-4f98-aa0d-597a4092c845)](https://www.youtube.com/watch?v=x8dfQkKTyP0&list=PLAx-M6Di0SisFJ1rv5M_FRHUlGA5rtUf_&index=2)
🔗 *Link to Video:* [Watch on Youtube](https://www.youtube.com/watch?v=x8dfQkKTyP0&list=PLAx-M6Di0SisFJ1rv5M_FRHUlGA5rtUf_&index=2)

## 📌 Project Overview

The goal is to simulate how actual data analysts in the e-commerce or retail industries work behind the scenes to use SQL to:

✅ Set up a messy, real-world e-commerce inventory **database**

✅ Perform **Exploratory Data Analysis (EDA)** to explore product categories, availability, and pricing inconsistencies

✅ Implement **Data Cleaning** to handle null values, remove invalid entries, and convert pricing from paise to rupees

✅ Write **business-driven SQL queries** to derive insights around **pricing, inventory, stock availability, revenue** and more

## 📁 Dataset Overview
The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv) and was originally scraped from Zepto’s official product listings. It mimics what you’d typically encounter in a real-world e-commerce inventory system.

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks.

🧾 Columns:
- **sku_id:** Unique identifier for each product entry (Synthetic Primary Key)

- **name:** Product name as it appears on the app

- **category:** Product category like Fruits, Snacks, Beverages, etc.

- **mrp:** Maximum Retail Price (originally in paise, converted to ₹)

- **discountPercent:** Discount applied on MRP

- **discountedSellingPrice:** Final price after discount (also converted to ₹)

- **availableQuantity:** Units available in inventory

- **weightInGms:** Product weight in grams

- **outOfStock:** Boolean flag indicating stock availability

- **quantity:** Number of units per package (mixed with grams for loose produce)

## 🔧 Project Workflow

Here’s a step-by-step breakdown of what we do in this project:

### 1. Database & Table Creation
We start by creating a SQL table with appropriate data types:

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

### 2. Data Import
- Loaded CSV using pgAdmin's import feature.

 - If you're not able to use the import feature, write this code instead:
```sql
   \copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
  FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```
- Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV UTF-8 format.

### 3. 🔍 Data Exploration
- Counted the total number of records in the dataset

- Viewed a sample of the dataset to understand structure and content

- Checked for null values across all columns

- Identified distinct product categories available in the dataset

- Compared in-stock vs out-of-stock product counts

- Detected products present multiple times, representing different SKUs

### 4. 🧹 Data Cleaning
- Identified and removed rows where MRP or discounted selling price was zero

- Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability
  
### 5. 📊 Business Insights
- Found top 10 best-value products based on discount percentage

- Identified high-MRP products that are currently out of stock

- Estimated potential revenue for each product category

- Filtered expensive products (MRP > ₹500) with minimal discount

- Ranked top 5 categories offering highest average discounts

- Calculated price per gram to identify value-for-money products

- Grouped products based on weight into Low, Medium, and Bulk categories

- Measured total inventory weight per product category


## 🛠️ How to Use This Project

1. **Clone the repository**
   ```bash
   git clone https://github.com/amlanmohanty/zepto-SQL-data-analysis-project.git
   cd zepto-SQL-data-analysis-project
   ```
2. **Open zepto_SQL_data_analysis.sql**

    This file contains:

      - Table creation

      - Data exploration

      - Data cleaning

      - SQL Business analysis
  
3. **Load the dataset into pgAdmin or any other PostgreSQL client**

      - Create a database and run the SQL file

      - Import the dataset (convert to UTF-8 if necessary)

4. **Follow along with the YouTube video for full walkthrough. 👨‍💼**

## 📜 License

MIT — feel free to fork, star, and use in your portfolio.

## 👨‍💻 About the Author
Hey, I’m Amlan Mohanty — a Data Analyst & Content Creator.
I break down complex data topics into simple, practical content that actually helps you land a job.

 ### 🚀 Stay Connected & Join the Data Drool Community
If you enjoyed this project and want to keep learning and growing as a data analyst, let’s stay in touch! I regularly share content around SQL, data analytics, portfolio projects, job tips, and more.

🎥 YouTube: [Amlan Mohanty](https://www.youtube.com/@amlanmohanty1)
- Beginner-friendly tutorials, real-world projects, job and career advice

📺 Instagram: [data.drool](https://www.instagram.com/data.drool/)
- Quick SQL tips, data memes, and behind-the-scenes content

💼 LinkedIn: [Amlan Mohanty](https://www.linkedin.com/in/amlanmohanty1/)
- Let’s connect professionally and grow your data career


## 💡 Thanks for checking out the project! Your support means a lot — feel free to star ⭐ this repo or share it with someone learning SQL.🚀

