# PowerBI_Practical_Exam_Weldesenbet_Aregay

## Problem Summary
The retail sales organization needed a comprehensive and interactive reporting solution to analyze sales performance, product trends, customer behavior, and geographic distribution. The data was spread across multiple tables (Sales, Products, Customers, Dates, Geography), making it difficult to extract actionable insights quickly.  
The main challenge was to clean, transform, and model the dataset into a robust star schema and then build clear, interactive visualizations to support business decision-making.

## Purpose
The purpose of this project was to:
- Import, clean, and transform raw retail sales data to ensure accuracy and consistency.
- Create a star schema data model for efficient reporting and analysis in Power BI.
- Develop interactive visualizations and dashboards to monitor KPIs such as total sales, profit margin, top-selling products, and sales trends over time.
- Implement advanced DAX calculations for deeper insights, such as year-over-year growth, running totals, and dynamic top product filtering.
- Apply Row-Level Security (RLS) to control data access for different regional managers.
- Publish and share the report for decision-making accessibility in Power BI Service.

---

### Power Query Screenshots   
**Shows the transformations applied to each table during the transformation stage and the calculated tables or aggregated tables used as a reference of the original tables for storage optimization.**     
<img width="330" height="450" alt="image" src="https://github.com/user-attachments/assets/0bcc2337-fd46-4241-b842-2c61e666e68f" />
<img width="330" height="450" alt="image" src="https://github.com/user-attachments/assets/2d6cf721-0105-4345-8658-d8edeee25b79" />
<img width="330" height="450" alt="image" src="https://github.com/user-attachments/assets/8e8e942f-2887-4ff5-bb43-f23ef6a184ce" />


<img width="230" height="450" alt="image" src="https://github.com/user-attachments/assets/9894177b-93ed-4038-9e07-9abd938b1678" />
<img width="230" height="450" alt="image" src="https://github.com/user-attachments/assets/976ec992-2723-4c3f-a48c-75caedee9b23" />
<img width="230" height="450" alt="image" src="https://github.com/user-attachments/assets/acea587f-e670-4c61-afc1-89e149f4e80a" />
<img width="230" height="500" alt="image" src="https://github.com/user-attachments/assets/1835adea-f751-47ec-968d-b6b262e89269" />

---

### Star Schema Model View
**I have used the Sales table as a fact table surrounded by the dimension tables. Some of the relationships are not active purposefully since they are aggregated table results which are used only for analysis purposes, not for logical relationships in the Model.**   
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/67a6a29c-4bd1-4d7e-b4db-341ba77e9d69" />

---

### Report Page and Dashboard pages
**Shows all the visuals created for the sales retail store.**   
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/b1201a75-e207-4535-a0eb-b3de81144d4c" />
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/3688d218-5711-47a2-80f4-bc252c941510" />
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/4d864032-c0d7-451d-a496-1d1c21af99f5" />
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/4ef6b0ea-8405-4e37-b586-63bdc970c8da" />

---

### Row-Level Security implementation
**Below is the RLS implementation in the Power BI Service. Managers are assigned access according to their country and region, ensuring data visibility is restricted to relevant geographic areas.**  
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/b1b6d1fd-44fc-482a-aeee-85d3aa889d37" />

---

## Top 5 Sales DAX Measure 

This DAX measure returns the total sales amount for only the **top 5 products** based on sales.

### DAX Code
```DAX
Top 5 Sales = 
IF (
    RANKX (
        ALL ( Products[ProductName] ),
        [Total Sales]
    ) <= 5,
    [Total Sales]
)
