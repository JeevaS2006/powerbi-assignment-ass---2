# Power BI E-Commerce Sales Analysis Using DAX

## 📌 Project Overview

This project focuses on analyzing an e-commerce sales dataset using **Microsoft Power BI, DAX (Data Analysis Expressions), and interactive data visualizations**.

Building on the data preparation and modeling completed in the previous assignment, this project involves creating calculated columns and measures to derive meaningful business metrics. These metrics are used to analyze sales performance, profitability, order trends, target achievement, and regional sales distribution.

The project demonstrates my practical understanding of DAX calculations, business intelligence, and data visualization as part of my journey as an **Aspiring Data Analyst**.

## 🎯 Project Objectives

* Create calculated columns using DAX.
* Develop measures to calculate important business metrics.
* Analyze order counts, sales, and profitability.
* Calculate Year-to-Date (YTD) sales performance.
* Compare actual sales against sales targets.
* Identify sales trends across months and product categories.
* Analyze profit and quantity relationships.
* Visualize geographic sales performance.
* Build interactive reports to support data-driven decision-making.

## 📂 Dataset Description

The project uses three related datasets from an e-commerce business.

### 1. List of Orders

Contains order-level information, including customer details, order dates, locations, sales amounts, and profits.

**Key Columns:**

* Order ID
* Order Date
* Customer Name
* City
* State
* Category
* Amount
* Profit

### 2. Order Details

Contains product-level information about categories, sub-categories, quantities, sales amounts, and profits.

**Key Columns:**

* Order ID
* Category
* Sub-Category
* Quantity
* Amount
* Profit

### 3. Sales Target

Contains sales targets defined by product category and month.

**Key Columns:**

* Category
* Month of Order Date
* Target

## 🛠️ Tools and Technologies

* **Microsoft Power BI Desktop** – Data modeling and interactive report development.
* **DAX** – Calculated columns and measures.
* **Power Query Editor** – Data preparation and transformation.
* **Data Visualization** – Charts, cards, matrices, and geographic maps.
* **GitHub** – Project documentation and portfolio management.

## 🧮 DAX Calculations

### 1. Calculated Columns

#### Category Type

Combined the Category and Sub-Category columns into a single column named `Category Type` to provide a more detailed product classification.

#### Revenue per Order

Created a calculated column to calculate revenue using Amount and Quantity.

**DAX Formula:**

```dax
Revenue per Order =
'Order Details'[Amount] * 'Order Details'[Quantity]
```

*Note: This formula follows the assignment requirement. If Amount already represents the total line-item sales value, multiplying it by Quantity again would overstate revenue. The meaning of Amount should be verified before using this metric in business reporting.*

#### Sales Category

Created a calculated column named `Sales Category` to classify records as Above Average or Below Average based on their Amount value.

**DAX Formula:**

```dax
Sales Category =
IF(
    'Order Details'[Amount] >
        CALCULATE(
            AVERAGE('Order Details'[Amount]),
            REMOVEFILTERS('Order Details')
        ),
    "Above Average",
    "Below Average"
)
```

This calculation compares each row's Amount with the overall average Amount in the Order Details table. Records equal to the average are classified as Below Average by this formula.

### 2. Calculated Measures

#### Order Count

Created a measure to calculate the total number of order records.

```dax
Order Count =
COUNTROWS('Order Details')
```

This measure counts rows in the Order Details table. If the business requirement is to count unique orders rather than order-detail records, `DISTINCTCOUNT('Order Details'[Order ID])` can be used instead.

#### Average Profit in Delhi

Created a measure to calculate the average profit for orders associated with Delhi.

```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('List of Orders'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

This measure filters the List of Orders table to Delhi and calculates the average profit.

#### Year-to-Date (YTD) Sales

Created a measure to calculate cumulative sales from the beginning of the year through the selected date.

```dax
YTD Sales =
TOTALYTD(
    SUM('List of Orders'[Amount]),
    'List of Orders'[Order Date]
)
```

This measure supports year-to-date sales analysis when used with an appropriate date context. For reliable time intelligence, a dedicated Date table with a valid relationship to the order date is recommended.

## 📊 Data Visualizations

The report includes the following visualizations to analyze different aspects of e-commerce performance.

### 1. Sales Target Achievement by Category

**Visual:** Clustered Column Chart

* Compares actual sales with sales targets for each category.
* Helps identify categories that meet, exceed, or fall short of their targets.

### 2. Maximum Profit Margin by Sub-Category

**Visual:** Donut Chart

* Displays the maximum profit margin for each sub-category.
* Helps compare the highest observed profit margins across product groups.

### 3. Monthly Sales Trend

**Visual:** Line Chart

* Shows changes in sales over time.
* Helps identify monthly trends and periods of increased or decreased sales.

### 4. Profit and Quantity by Sub-Category

**Visual:** Scatter Chart

* Compares profit with quantity sold across sub-categories.
* Helps identify relationships between sales volume and profitability.

### 5. Total Sales Amount and Sales Target

**Visual:** Cards

* Displays total sales amount.
* Displays the total sales target.
* Enables a quick comparison of actual performance against planned targets.

**Multi-Row Card:**

* Displays the minimum sales target for each segment or category, depending on the available model fields and assignment requirements.

### 6. Sales Performance Matrix

**Visual:** Matrix

* Organizes actual sales and targets by category and month.
* Helps identify performance differences across categories and reporting periods.

### 7. Geographic Sales Analysis

**Visual:** Map

* Displays total sales by city.
* Helps identify regional sales patterns and high-performing locations.

### 8. Sales Distribution by Sub-Category

**Visual:** Treemap

* Represents sales distribution across product sub-categories.
* Helps identify sub-categories contributing the most to overall sales.

### 9. Order Count Analysis by State

**Visual:** Funnel Chart

* Visualizes order counts across different states.
* Supports comparisons of order activity between regions.

## 📈 Business Analysis Areas

The report supports analysis of:

* **Sales Performance:** Comparison of actual sales with sales targets.
* **Profitability:** Evaluation of average profit and profit margins.
* **Product Performance:** Analysis of sales and profit across categories and sub-categories.
* **Time-Based Trends:** Monthly sales patterns and cumulative YTD performance.
* **Geographic Performance:** Comparison of sales and order activity across cities and states.
* **Target Monitoring:** Identification of differences between actual sales and planned targets.

## 💡 Key Learning Outcomes

Through this project, I gained practical experience in:

* Writing DAX calculated columns and measures.
* Applying aggregation and filter context.
* Using `CALCULATE`, `IF`, `AVERAGE`, `SUM`, `COUNTROWS`, and `TOTALYTD`.
* Comparing actual sales with business targets.
* Creating analytical visualizations in Power BI.
* Understanding the importance of relationships between tables.
* Applying time-intelligence calculations.
* Presenting business metrics through interactive reports.
* Translating raw data into meaningful business information.

## 📁 Project Structure

The repository can be organized as follows:

```text
PowerBI-Ecommerce-DAX-Analysis/
│
├── README.md
│
├── Dataset/
│   ├── List of Orders.csv
│   ├── Order Details.csv
│   └── Sales target.csv
│
├── PowerBI/
│   └── Ecommerce_Sales_DAX_Analysis.pbix
│
├── Screenshots/
│   ├── Sales_Target_Achievement.png
│   ├── Monthly_Sales_Trend.png
│   ├── Sales_Performance_Matrix.png
│   └── Geographic_Sales_Analysis.png
│
└── Documentation/
    └── PowerBI_DAX_Assignment_Report.pdf
```

*This is a suggested structure. Update the file names and folders according to the actual files you upload.*

## 🏁 Conclusion

This project strengthened my practical understanding of DAX calculations and interactive data visualization using Microsoft Power BI. By developing calculated columns, analytical measures, and business-focused visualizations, I explored sales performance, profitability, target achievement, product trends, and geographic distribution.

The project demonstrates how DAX and data visualization can transform structured e-commerce data into meaningful business metrics that support informed decision-making.

As an **Aspiring Data Analyst**, I am continuously improving my skills in data analysis, SQL, Python, Microsoft Excel, and Power BI through hands-on projects.

## 👨‍💻 Author

**Jeeva S**

Aspiring Data Analyst

**Skills and Interests:**

* Microsoft Power BI
* DAX
* Microsoft Excel
* SQL
* Python
* Data Cleaning
* Data Visualization
* Business Intelligence

---

⭐ Thank you for visiting my project repository!
