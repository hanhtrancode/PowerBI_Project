

<h1>Project Introduction</h1> 
In this project, i mainly use PowerBi to analyze. To complete project, i did these steps:
1.Loading Excel Workbook to Power BI <br>
2.Cleaning Data <br>
3.Modeling Data <br>
4.Visualizing Data <br>
5.Personal Observation <br>
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

Content: The table will provide all information about product. <br>
Note: Remember to delete duplicate data in “ProductID”

![image](https://github.com/user-attachments/assets/d4c03bf6-1f13-4e51-8d42-bc16c5688390)


**Illustation about “Dim_location” table**
Content: The table will provide all information about location.  <br>
Note: Remember to delete duplicate data in “City”


![image](https://github.com/user-attachments/assets/511a9d90-1a3a-41ee-bd14-0b28f7e06c4d)


**Illustation about “Dim_customer” table**

Content: The table will provide all information about customer.  <br>
Note: Remember to delete duplicate data in “Customer ID”

![image](https://github.com/user-attachments/assets/8e95a142-ab0e-4677-922f-f54451177e90)


**Last step, I will create “Dim_date” via dax language in “table mode”**

I create it via using “Calendar” function in dax language. <br>
The code is: Date_dim = calendar(min(Fact_sale[Order Date]), max(Fact_sale[Order Date])) <br>
Then, I will make more columns about year, quarter, month, day <br>
The code are: <br>
Year = year(Date_dim[Date]) <br>
Quarter = quarter(Date_dim[Date]) <br>
Month = Month(Date_dim[Date]) <br>
Day = Day(Date_dim[Date]) <br>
(Note: we need mark as date table to create a “Date_dim” table)

Lastly, I turn off “Auto date” in setting to improve query performance.

And this is date model, it is Star Schema as I expected

![image](https://github.com/user-attachments/assets/4dce392f-5fe2-402c-ab7b-453eaa689fd9)

<h4>I use DAX to calculate to visualize graphs and come up insights.</h4>

Here are my code using in this  file to calculate: <br>
Total Sales: Total = CALCULATE(sum(Fact_sale[Sales]), all(Fact_sale)) <br>
Total Quantity: Total Quantity = sum(Fact_sale[Quantity]) <br>
To calculate sale percentage: %Sales = Divide(sum(Fact_sale[Sales]),[Total]) <br>

<h3>IV.Visualize results</h3>

![image](https://github.com/user-attachments/assets/4c19c26b-7b6b-44cd-bada-a24edfb5dc3b)

<h3>V.Personal Observation</h3>

This report mainly is made for sales manager, so we mainly focus on sale performance. 
There are some general observation we can have:
-In category, Office Supplies and Technology are 2 main categories that account for 80% of total sales. <br>
-In segment, this store has two main types of customers, which are Corporate and Home Office account for more than 80% of total sales. As results, we can conclude our main customers are bussiness, our main work are B2B bussiness. <br>
-Two largest markets are West and East. <br>

Moreover, we can go to detail parts:
-Because Technology and Office Supplies are accounted for 80% of sales, so we care about which specific of products are sold most. Top 5 products are: “3D Systems,2nd Generation, Magenta”; “Canon ImageClass 2200 Advanced Copier”; “Hewlett Packard LaserJet3310 Copier”, “GBC DocuBind Tl300 Electric Binding System”. <br>

-Most of top-sale products whose category are Technology and Office Supplies are sold in East Location. Interestingly, the top one of selling, “3D Systems, 2nd Generation, Magenta”, are just sold in East Location.  <br>
-In East market, from January to May, people mostly buy Electric Open Letter, so it is a good information to prepare inventory. From June to December, customers start to buy more products which are in top 5 selling products. <br>

Now, we care more about customer behaviors.
-Top 5 products that 80% of customers buy are  <br>
•	“3D Systems Cube Printer, 2nd Generation, Magenta”; 
•	“GBC Docubind TL300 Electric Binding System”;
•	“Martin Yale Chadless Opener Electric Letter Opener”; 
•	“HON 5400 Series Talk Chairs for Big and Tall”; 
•	“ Canon imageClass 2200 Advanced Copier”; 
•	“Cubify CubeX 3D Printer Double Head Print”
-Peak period is from August to December and peak season is December.

<h3>VI.Suggestion </h3>

1.	From August to December, the store should prepara larger inventor to adapt customer needs.
2.	Total Cost are concerning issues, as we can see the sum of sales is 1.57 million dollars, while it is 0.18 million in profit. The net margin is 11%. It is not a good number according to retail index in 2019. Because of the lack of information, I can not find out more, but I can suggest that the store should focus more on Technology and Office supplies category to ultilize costs.













