# 🚀 Introduction
📊 **Kimia Farma Business Performance Analysis**

📌 **Description:**

In today's data-driven world, **business performance analysis** plays a crucial role in making informed decisions. This project focuses on analyzing **Kimia Farma's** business performance **from 2020 to 2023** using **Google Big Query** as part of a **Rakamin Academy** program in collaboration with **Kimia Farma**. 🎓🏥

This repository contains the complete **workflow**, from **data processing** to **final insights**. By leveraging **SQL queries** and **data visualization tools**, this project will transform raw data into **meaningful business intelligence** and uncover **key insights**. 💡

The final results will be presented through an **interactive dashboard in Google Looker Studio**, making it easier to interpret trends and patterns in **Kimia Farma's financial and operational performance**. 💰📈

# 📖 Background

Driven by a quest to gain deeper insights into **Kimia Farma's business performance**, this project was initiated as a part of a **Big Data Analytics program by Rakamin Academy** in collaboration with **Kimia Farma**. The goal is to analyze key business metrics from **2020 to 2023**, providing valuable insights for decision-making.

The dataset is obtained directly from **Kimia Farma's internal records**. Due to the **sensitive and confidential** nature of the data, the dataset will not publicly shared. This analysis aims to generate a **comprehensive dashboard in Google Looker Studio**, allowing stakeholders to visualize **Kimia Farma's business trends** effectively.

Through SQL queries and data visualization, the project seeks to answer:

📈 **How has Kimia Farma's revenue evolved from 2020 to 2023?**

🌍 **Which provinces have the highest total transactions?**

💰 **What are the top 10 branches with the highest net sales?**

⭐ **Which top 5 branches have the highest ratings but lowest transaction volumes?**

🗺️ **How does Kimia Farma’s total profit distribution look across Indonesia’s provinces?**

🔎 **What additional insights can be derived to optimize business performance?**

By developing this project, I aim to enhance my **data analytics skills**, particularly in **SQL, BigQuery, and Google Looker Studio**, while delivering valuable insights for **Kimia Farma’s business strategy**. 📊

# 🛠️ Tools I Used

For this project analyzing Kimia Farma's business performance, I utilized several key tools:

- **Google BigQuery**: The backbone of my analysis, enabling efficient querying and processing of large datasets.
- **Google Looker Studio**: Used to create interactive dashboards, transforming raw data into visual insights for better decision-making.
- **Git & GitHub**: Essential for version control, tracking progress, and sharing my work in a structured and collaborative manner.

These tools allowed me to streamline data analysis, visualization, and project management effectively. 🔍

# 📂 Data Understanding

In this project, I worked with **four CSV files** containing key business data from **Kimia Farma**:

- **kf_final_transaction** 🧾: Contains transactional records, including sales and revenue details.
- **kf_inventory** 📦: Tracks product stock levels and inventory movement.
- **kf_kantor_cabang** 🏢: Provides information about branch locations and operational details.
- **kf_product** 🏷️: Lists product details, including categories and pricing.

After uploading these files into **Google BigQuery**, I created a new table called 'analyze' within the same dataset. This table serves as a **centralized data source**, combining the four CSV files to facilitate a more streamlined and efficient analysis process.

The next step involved **merging these** datasets using SQL queries to ensure a structured and cohesive dataset for further analysis. Below is the SQL code used to create the 'analyze' table:

# 📑 The Analysis

Each query in this project was designed to explore key aspects of **Kimia Farma’s business performance**.

Here's how I approached the analysis:
