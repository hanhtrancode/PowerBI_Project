![image](https://github.com/user-attachments/assets/3c52c599-8c81-4833-b0e2-57bf30064624)# PowerBI_Project

<h1>Project Introduction</h1> 
In this project, i mainly use PowerBi to analyze. To complete project, i did these steps:
1.Loading Excel Workbook to Power BI
2.Cleaning Data
3.Modeling Data
4.Visualizing Data
5.Personal Observation
6.Suggestion

<h1>Data Introduction</h1> 
This data recored sales figures in one big organization in 2019 and 2020. They are domestic corporation that have operated in America. They are open on all regions of America and main sell in East. Their main products are Office Supplies, Technology, Furniture. Their customers are Consumer, Corporate and Home Office.

<h2>Implementation Process </h2>

<h3>I.	Loading Excel Workbook to PowerBI</h3>

Because our data source is Excel format, so we will choose “Import data from Excel”. After choosing right data source, i will click on “Transform data” to manipulate data.

![image](https://github.com/user-attachments/assets/6ca8df63-b500-4eba-9170-3563c228c9e7)

<h3>II.	Cleaning data in PowerBi</h3>

Because this data is quite clean, so I just need to adjust each column to right data type to make sure no error will happen. By clicking on “Detect Data Type” in “Transform” tap, I  can quickly define data type of each column.
Everything seems fine, so I just need to delete unnessary columns. There are 3 unnecessary columns in here: “Returns”, “Ind1”, “Ind2”.

Then, I delete “Row ID+O6G3A1:R6” to make a better one, change its name to “Row ID”. The functionality of this row is to help query faster.

<h3>III.	Modeling data in PowerBi</h3>
In this data, I decided to have 1 fact tables and 4 dimension tables, which are “Dim_product”, “Dim_location”, “Dim_customer”, “Dim_date”.

**In fact table, the table look like this.**
![image](https://github.com/user-attachments/assets/3badd534-ad74-4d60-add0-7bd4507567f6)

You may wonder why I don’t put “OrderID”, “Order Date”, “Ship Date”, “Ship Mode” together and make a new “Dim_order” table. We can see that “OrderID” is not doing a good job as a primary key because with 1 primary key in “OrderID”, we will have 2 different information. For example, you can see in line 1, 2 and 3, the “OrderID” are both “CA-2019-160304” but “ProductId”, “Sales”, and “Quantity” are different. So we can be sure that with “OrderId” is not unique, and it should  not be the primary key. To ensure the consistency and precise of data, I keep “OrderDate”, “ShipDate” and “ShipMode” in fact table.

**Illutration about “Dim_product” table.**
Content: The table will provide all information about product.
Note: Remember to delete duplicate data in “ProductID”
![image](https://github.com/user-attachments/assets/6abd6750-e44b-416b-a1c8-1ca1a54596ae)

**Illustation about “Dim_location” table**
![image](https://github.com/user-attachments/assets/9aeefa44-dac5-484a-b6aa-14951ca1fc61)




