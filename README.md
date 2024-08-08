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

![image](https://github.com/user-attachments/assets/caf01419-3adb-4a62-b465-7f726bf4e233)


You may wonder why I don’t put “OrderID”, “Order Date”, “Ship Date”, “Ship Mode” together and make a new “Dim_order” table. We can see that “OrderID” is not doing a good job as a primary key because with 1 primary key in “OrderID”, we will have 2 different information. For example, you can see in line 1, 2 and 3, the “OrderID” are both “CA-2019-160304” but “ProductId”, “Sales”, and “Quantity” are different. So we can be sure that with “OrderId” is not unique, and it should  not be the primary key. To ensure the consistency and precise of data, I keep “OrderDate”, “ShipDate” and “ShipMode” in fact table.

**Illutration about “Dim_product” table.**

Content: The table will provide all information about product.
Note: Remember to delete duplicate data in “ProductID”

![image](https://github.com/user-attachments/assets/d4c03bf6-1f13-4e51-8d42-bc16c5688390)


**Illustation about “Dim_location” table**
Content: The table will provide all information about location.
Note: Remember to delete duplicate data in “City”


![image](https://github.com/user-attachments/assets/511a9d90-1a3a-41ee-bd14-0b28f7e06c4d)


**Illustation about “Dim_customer” table**

Content: The table will provide all information about customer.
Note: Remember to delete duplicate data in “Customer ID”

![image](https://github.com/user-attachments/assets/8e95a142-ab0e-4677-922f-f54451177e90)










