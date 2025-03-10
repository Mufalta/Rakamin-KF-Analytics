# 🚀 Introduction
### **Kimia Farma Business Performance Analysis**

📌 **Description:**

In today's data-driven world, **business performance analysis** plays a crucial role in making informed decisions. This project focuses on analyzing **Kimia Farma's** business performance **from 2020 to 2023** using **Google Big Query** as part of a **Rakamin Academy** program in collaboration with **Kimia Farma**. 🎓🏥

This repository contains the complete **workflow**, from **data processing** to **final insights**. By leveraging **SQL queries** and **data visualization tools**, this project will transform raw data into **meaningful business intelligence** and uncover **key insights**. 💡

The final results will be presented through an **interactive dashboard in Google Looker Studio**, making it easier to interpret trends and patterns in **Kimia Farma's financial and operational performance**. 💰📈

# 📖 Background

Driven by a quest to gain deeper insights into **Kimia Farma's business performance**, this project was initiated as a part of a **Big Data Analytics program by Rakamin Academy** in collaboration with **Kimia Farma**. The goal is to analyze key business metrics from **2020 to 2023**, providing valuable insights for decision-making.

The dataset is obtained directly from **Kimia Farma's internal records**. Due to the **sensitive and confidential** nature of the data, the dataset will not publicly shared. This analysis aims to generate a **comprehensive dashboard in Google Looker Studio**, allowing stakeholders to visualize **Kimia Farma's business trends** effectively.

### **Through SQL queries and data visualization, the project seeks to answer**:

📈 How has Kimia Farma’s revenue changed from 2020 to 2023?

🗺️ What is Indonesia’s geo map distribution of total profit by province?

🏆 Which are the top 10 provinces with the highest total transactions?

💰 Which are the top 10 provinces with the highest net sales?

⭐ How does Kimia Farma’s total profit distribution look across Indonesia’s provinces?

By developing this project, I aim to enhance my **data analytics skills**, particularly in **SQL, BigQuery, and Google Looker Studio**, while delivering valuable insights for **Kimia Farma’s business strategy**. 📊

# 🛠️ Tools I Used

For this project analyzing Kimia Farma's business performance, I utilized several key tools:

- **Google BigQuery**: The backbone of my analysis, enabling efficient querying and processing of large datasets.
- **Google Looker Studio**: Used to create interactive dashboards, transforming raw data into visual insights for better decision-making.
- **Git & GitHub**: Essential for version control, tracking progress, and sharing my work in a structured and collaborative manner.

These tools allowed me to streamline data analysis, visualization, and project management effectively. 🔍

# 📂 Data Understanding

In this project, I worked with **four CSV files** containing key business data from **Kimia Farma**:

- ```kf_final_transaction``` 🧾: Contains transactional records, including sales and revenue details.
- ```kf_inventory``` 📦: Tracks product stock levels and inventory movement.
- ```kf_kantor_cabang``` 🏢: Provides information about branch locations and operational details.
- ```kf_product``` 🏷️: Lists product details, including categories and pricing.

After uploading these files into **Google BigQuery**, I created a new table called ```analyze``` within the same dataset. This table serves as a **centralized data source**, combining the four CSV files to facilitate a more streamlined and efficient analysis process.

The next step involved **merging these** datasets using SQL queries to ensure a structured and cohesive dataset for further analysis. Below is the SQL code used to create the ```analyze``` table:
```sql
CREATE OR REPLACE TABLE `kimia_farma.analyze` AS
SELECT 
    t.transaction_id,
    t.date,
    t.branch_id,
    c.branch_name,
    c.kota,
    c.provinsi,
    c.rating AS rating_cabang,
    t.customer_name,
    t.product_id,
    p.product_name,
    t.price AS actual_price,
    t.discount_percentage,
    
    -- Calculate Net Sales
    t.price * (1 - t.discount_percentage / 100) AS nett_sales,
    
    -- Determine the Gross Profit Percentage based on Price
    CASE 
        WHEN t.price <= 50000 THEN 0.10
        WHEN t.price > 50000 AND t.price <= 100000 THEN 0.15
        WHEN t.price > 100000 AND t.price <= 300000 THEN 0.20
        WHEN t.price > 300000 AND t.price <= 500000 THEN 0.25
        ELSE 0.30
    END AS persentase_gross_laba,

    -- Calculate Net Profit
    (t.price * (1 - t.discount_percentage / 100)) * 
    CASE 
        WHEN t.price <= 50000 THEN 0.10
        WHEN t.price > 50000 AND t.price <= 100000 THEN 0.15
        WHEN t.price > 100000 AND t.price <= 300000 THEN 0.20
        WHEN t.price > 300000 AND t.price <= 500000 THEN 0.25
        ELSE 0.30
    END AS nett_profit,

    t.rating AS rating_transaksi
FROM `kimia_farma.kf_final_transaction` t
JOIN `kimia_farma.kf_kantor_cabang` c 
    ON t.branch_id = c.branch_id
JOIN `kimia_farma.kf_product` p 
    ON t.product_id = p.product_id;
```
After successfully creating the ```analyze``` table in **Google BigQuery** by merging the CSV files, the next step is to connect this table to **Google Looker Studio** for **data analysis and visualization**.

### **Connecting BigQuery to Google Looker Studio**

1. Open **Google Looker Studio** and create a new data source.
2. Select **Google BigQuery** as the data source.
3. Choose the project containing the ```kimia_farma``` dataset and select the ```analyze``` table.
4. Click **Connect** to link the table to Looker Studio.

### **Using Google Looker Studio for Analysis & Visualization**

Once the ```analyze``` table is connected, the data can be visualized using various Looker Studio components, such as:

- **Bar Charts & Line Charts** 📈: To observe sales trends.
- **Geo Maps** 🗺️: To visualize the distribution of transactions, net sales and net profit across different locations.
- **Tables & Scorecards** 📊: To highlight key metrics like total revenue, net profit, and transactions.

By leveraging **Google Looker Studio**, I can gain deeper insights into **Kimia Farma's business performance**, enabling data-driven decision-making. 🎯

# 📑 The Analysis

After transforming the data into an **interactive dashboard**, it's time to delve into the analysis. To provide better clarity, I will display the **dashboard images** below for reference.. Additionally, you can explore the **live dashboard** on Google Looker Studio by clicking the link below:
[Kimia Farma Dashboard](https://lookerstudio.google.com/s/uoDWQvZIEZg)

![](https://raw.githubusercontent.com/Mufalta/Rakamin-KF-Analytics/main/Images/Dashboard.jpg)

_Dashboard of Kimia Farma Business Performance from 2020 to 2023_

To answer specific business questions, I will use animated GIFs to simulate **real-time** data exploration within the dashboard.

### **1. How has Kimia Farma’s revenue changed from 2020 to 2023** 📈

To analyze Kimia Farma's revenue trends from 2020 to 2023, I set ```date``` as the dimension (x-axis) and ```nett_sales``` as the metric (y-axis). Since the data represents changes over time. I used a **Line Chart**, which is ideal for visualizing trends and identifying revenue patterns across different periods. This approach allows us to track revenue fluctuations over time and identify key growth patterns.

Here's the breakdown of Kimia Farma's revenue evolved from 2020 to 2023:

- **Recurring February Decline:** Net sales consistently experience a sharp drop every February, indicating a seasonal pattern likely influenced by lower demand or external factors.
- **Highest Net Sales:** The highest net sales were recorded in May 2020, totaling Rp7,498,873,272, representing the peak sales period in the analyzed timeframe.
- **Lowest Net Sales:** The lowest net sales occurred in February 2022, reaching Rp6,670,918,229, marking the weakest performance in the observed period.

![](https://raw.githubusercontent.com/Mufalta/Rakamin-KF-Analytics/main/Images/Net_Sales_Over_Time.png.jpg)

_Line chart visualizing the net sales from 2020 to 2023_

### **2. What is Indonesia’s geo map distribution of total profit by province** 🗺️

To analyze net profit distribution across provinces, I set ```Province``` as the location dimension and ```nett_profit``` as the metric. I used a **Filled Map Chart** because it provides a clear geographic visualization of profit variations. The color intensity helps quickly identify provinces with the highest and lowest profits, making regional comparisons easier.

Here's the breakdown of net profit distribution across provinces:

- **Highest Profit**: The highest net profit is recorded in West Java, reaching approximately Rp29.10 billion, making it the most profitable province.
- **Widespread Sales**: Net profit is distributed across almost all provinces, indicating a broad market reach across Indonesia.
- **No Sales in Some Provinces**: Some provinces, including Bengkulu, Lampung, and West Sulawesi, have no recorded net profit, highlighting potential gaps in market coverage.


_Filled map chart visualizing profit variations across all provinces in Indonesia_




























