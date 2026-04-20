# 📊 Freelancer Market Analysis

## 📖 Project Overview
This project analyzes a global dataset of freelancers to uncover insights into earnings, performance, and market trends. 

The goal is to understand how factors such as experience, skill category, and client satisfaction influence freelancer income and success.

---

## 🎯 Business Problem
Freelancing platforms are highly competitive, and it is often unclear what drives higher earnings and better client outcomes.

This project answers:
- What factors influence freelancer earnings?
- Which skills are most profitable?
- Does experience significantly impact income?
- How does client satisfaction relate to ratings?

---

## 🛠️ Tools & Technologies
- Python
- Pandas
- Excel (for initial exploration)
- (Add Power BI or SQL here if you use them later)

---

## 📂 Dataset Description
The dataset contains global freelancer data, including:
- Freelancer ID
- Job category / skill
- Experience level
- Hourly rate / earnings
- Client satisfaction (%)
- Ratings
- Gender (cleaned)

---

## 🧹 Data Cleaning Process
The dataset required several preprocessing steps to ensure accuracy:

- Removed duplicates to avoid skewed analysis  
- Standardized text fields (e.g., gender: male/female → m/f)  
- Converted `client_satisfaction` from percentage strings to numeric values  
- Handled missing values using group-based imputation (median by rating)  
- Corrected data types for numerical analysis  

These steps ensured the dataset was consistent and ready for analysis.

---

## 🔍 Exploratory Data Analysis
Key analysis performed includes:

- Distribution of freelancer earnings  
- Relationship between experience level and hourly rate  
- Comparison of earnings across different skill categories  
- Analysis of client satisfaction vs ratings  
- Identification of high-performing freelancer segments  

---

## 📊 Key Insights
- High-income skills dominate earnings across the platform  
- Freelancers with more experience tend to earn higher hourly rates  
- Strong correlation observed between ratings and client satisfaction  
- Certain categories consistently outperform others in terms of income  
- Data cleaning significantly improved reliability of insights  

---

## ⚠️ Challenges & Solutions
**Challenge:** Missing values in key columns like client satisfaction  
**Solution:** Used group-based median imputation based on rating  

**Challenge:** Inconsistent categorical data (e.g., gender variations)  
**Solution:** Standardized values for consistency  

---

## 📈 What I Learned
- Importance of data cleaning before analysis  
- How to handle missing data effectively  
- Using Pandas for real-world data transformation  
- Extracting meaningful insights from raw datasets  

---

## 🚀 Future Improvements
- Add data visualizations (Matplotlib / Seaborn / Power BI)  
- Perform deeper statistical analysis  
- Build a dashboard for interactive insights  
- Incorporate SQL for data querying  

---

## 📁 Project Structure
```
├── data/
│   ├── raw_dataset.csv
│   ├── cleaned_dataset.csv
├── notebooks/
│   ├── analysis.ipynb
├── README.md
```

---

## 📌 Conclusion
This project demonstrates how raw freelancer data can be transformed into actionable insights through proper data cleaning and analysis. It highlights key drivers of success in the freelancing market and provides a foundation for further data exploration.
