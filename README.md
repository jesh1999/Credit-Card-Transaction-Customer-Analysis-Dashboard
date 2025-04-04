---

# **📊 Credit Card Transaction & Customer Analysis Dashboard**  
### Real-Time Insights that Power Smarter Financial Decisions  

This project showcases an interactive **Power BI dashboard** designed to monitor **weekly credit card operations**, uncover **customer spending patterns**, and reveal **revenue-driving segments** across various demographics.

It bridges **business intelligence** with **customer insights**, enabling stakeholders to track transactions, analyze card performance, and personalize strategies for better engagement and profitability.

---

### 🎯 **Project Objectives**

**Credit Card Transaction Report**  
Provides a quick snapshot of:
- 💳 Transaction volume and revenue by card type (Gold, Silver, Blue, Platinum)  
- 💸 Spending categories (Bills, Entertainment, Fuel, Travel, etc.)  
- 📈 Quarterly transaction trends and revenue spikes  
- 🎓 Revenue breakdown by **education level** and **job roles**

![Card Type Revenue](https://github.com/user-attachments/assets/b6ef6a25-fa52-493a-bd08-7acf81f4cbe2)  
*Visual: Transaction Revenue by Card Type and Category*

---

**Customer Segmentation Report**  
Dives deeper into:
- 🧑‍🤝‍🧑 Customer income groups, age brackets, marital status, and dependents  
- 🏫 Education vs. revenue contribution  
- 👨‍💼 Job roles with highest earnings  
- 🗺️ Top 5 revenue-generating states  

![Customer Demographics Breakdown](https://github.com/user-attachments/assets/b4de88a6-e7a8-4ba9-ae49-f905e5fb45ee)  
*Visual: Revenue by Customer Age, Education, and Region*

---

### 📈 **Key Metrics Tracked**
| KPI                     | Description                                |
|------------------------|--------------------------------------------|
| 💰 **Total Revenue**         | From fees, interest, and transactions      |
| 📊 **Total Interest**        | Generated from credit usage               |
| 🔢 **Transaction Count**     | Total number of transactions              |
| 🏦 **Income**                | Aggregated across all customer groups     |
| ⭐ **CSS (Customer Satisfaction Score)** | Based on interactions and feedback |

---

### 🧮 **DAX Queries & Measures**

```DAX
AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
)

IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)
```

```DAX
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)

Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1)
)
```

---

### 🔍 **Key Insights Unlocked**
- 📌 **Gold cards** bring the highest revenue  
- 🎓 Graduates and **white-collar professionals** dominate earnings  
- 🧑‍🤝‍🧑 Income level *does* influence spending behavior  
- 🗺️ Top states reveal potential for targeted campaigns  
- 🔁 Seasonal revenue spikes show room for marketing optimization

---

### 🛠️ **Tools & Technologies Used**
- **Power BI** for building dashboards  
- **DAX** for dynamic filtering and calculations  
- **Data Transformation** using Power Query  

---

### 🎨 **Visual Highlights**
- 📊 **Bar Charts:** Revenue by card type, job roles  
- 📈 **Line Graphs:** Time-series patterns  
- 📋 **Tables:** Detailed breakdowns by age, education, income  
- 📲 **Cards & KPIs:** Snapshot of real-time performance  

---

### 📌 **Interactive Features**
- 🔍 Drilldowns by card type, income group, gender, region  
- 📅 Filter by quarter or transaction method  
- 🖱️ Hover tooltips for revenue comparisons  
- 📊 Dynamic views to compare performance across segments  

---

### 🚀 **Future Enhancements**
- 🔮 **Forecasting:** Use time-series models to predict transaction spikes  
- 👥 **Deeper Segmentation:** For hyper-personalized campaigns  
- 📊 **Granular Filters:** Add slicers for chip type, frequency, and lifestyle preferences  

---

### 📂 **Project Files**
- `.pbix` Dashboard File: Interactive with filters and DAX  
- 📄 Documentation: Data cleaning steps, transformations, measures  

---

### 🏁 **Conclusion**  
This dashboard simplifies complex credit card and customer data into an easy-to-navigate solution. With rich visual insights and drilldown features, decision-makers can **spot patterns**, **segment audiences**, and **optimize revenue strategies**—all in real-time.  

---
