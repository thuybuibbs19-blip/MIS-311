# MIS-311: Introduction to Business Analytics
## Project: An Exploratory Data Analysis (EDA) of *Supermarket Sales Data*

This project was implemented using the **Python** language on **Google Colab**. I was able to practice more with Python through this small dataset analysis project, and also wanted to utilize **Python** for using various commands, syntax processing, and creating dynamic visualizations.
It includes the following sections:
1. Overviewing the dataset
2. Checking and processing data types
3. Cleaning the dataset
4. Clarifying the insights
5. Conclusion

### 1. Overviewing the dataset
This analysis aims to explore the sales revenue of a supermarket, with information encompassing different brands, regions, and customer segments, along with a diverse range of products. Furthermore, the dataset clearly shows the quantity of items sold and the total revenue generated from those items.

This is a **brief description** of the variables included in the data table, along with their correct data types:
* Sale_id (object): Unique identifier
* Branch (object): brand of the supermarket
* City (object): City of the supermarket
* Customer_type (object): Type of customers
* Product_name (object): Name of product
* Product_category (object): Category of product
* Quantity (int): Amount sold
* Total_price (float64): Amount of sales in USD

---

### 2. Checking and processing data types
First, check the number of rows and columns. By using `.shape`, we can see that this dataset has a total of **253 rows and 8 columns**.

<img width="389" height="103" alt="image" src="https://github.com/user-attachments/assets/54d927e5-c255-45be-a88e-1776bb7672f3" />

---

Then, it's necessary to check the data types of the available dataset and process them to ensure consistency.

<img width="266" height="450" alt="image" src="https://github.com/user-attachments/assets/5396511c-50fe-4269-88ca-93b1d7e267bf" />
<img width="1080" height="147" alt="image" src="https://github.com/user-attachments/assets/cb54a84d-9dbf-47f8-950c-6e14a6cc70e2" />

---

After processing with `.astype(object)` (this syntax is used to convert numerical values ​​to object values), check again to make sure it matches the data description.

<img width="251" height="470" alt="image" src="https://github.com/user-attachments/assets/c3e07a50-25ab-4138-a70f-cabead616f5a" />

---

### 3. Cleaning the dataset
By using `.isna()` to find missing values.

For example, I used `.iloc[27:37]`, which means requesting to display the results from **row 27 to row 36**.

**True** indicates a missing value (appears in rows 31,32, 33 36), and **False** indicates no missing value.

<img width="943" height="484" alt="image" src="https://github.com/user-attachments/assets/7c339be3-cddb-4b03-baf3-24d9c42d08d2" />

---

Then, use the `.sum()` syntax to count how many missing values ​​there are in each column.

<img width="374" height="476" alt="image" src="https://github.com/user-attachments/assets/64afc91b-5869-4bf5-98ed-cbf7eb1d4835" />

---

Once I identified the missing values, I chose to completely remove them using the `.dropna()` syntax, **removing them row by row**.

<img width="990" height="574" alt="image" src="https://github.com/user-attachments/assets/fe45be08-d278-4b22-af5b-becca486e9c6" />

Rows 31, 32, 33, and 36, which contained missing values, have been completely removed.

---


After that, I saved these results into a new Excel data file to continue cleaning the data, ensuring consistency in the discovered data.

<img width="606" height="63" alt="image" src="https://github.com/user-attachments/assets/fa51c9c3-14ab-462e-84f7-c72301dcd09b" />

---

Next, I proceeded to find duplicate rows, using the `.value_counts()` syntax to find the total number of duplicate rows.


<img width="999" height="607" alt="image" src="https://github.com/user-attachments/assets/64bfbbf0-6c8e-4f17-9cf9-20095a330f33" />

**True** indicates a duplicate value, and **False** indicates no duplicate rows.

<img width="318" height="214" alt="image" src="https://github.com/user-attachments/assets/012c3d40-83bf-4aed-a27d-b023647fafa4" />


Output results: **False** indicates rows with no duplicate values, comprising 241 rows. **True** indicates rows with duplicate values, consisting of 3 rows.

I will remove these 3 rows using the `.drop_duplicates` syntax.

Then, I saved it as a new data file, which is also a complete data file for data analysis and idea generation tasks.

---

### 4. Clarifying the insights
#### *4.1. The 1st insight*
Find the product category with the highest total revenue.

The `.groupby` syntax helps group the values ​​of the *"product_category"* column with the *"total_price" column*, and then applies the sum calculation to determine the total revenue.
`.sort_values(ascending=False)` is used to sort the results in descending order.

<img width="1104" height="426" alt="image" src="https://github.com/user-attachments/assets/488f614c-122f-4bee-840f-b820f4cd5605" />

<img width="998" height="598" alt="image" src="https://github.com/user-attachments/assets/cd3ecaa6-4ef0-443a-b2de-9ec019f6923c" />

*Figure 1. Total sales by Product Category*

According to the chart, there are 5 types of products in the supermarket, measured in dollars. Of these, **Fruits had the highest total revenue**, bringing in nearly **$7,500**, indicating that it is the most popular product in the supermarket. Following closely behind are **Beverages** and **Stationery** with **over $6,000** each; while **Household** and **Personal Care** products both generated **less than $6,000** in revenue.

#### *4.2. The 2nd insight*
Find the city that generates the most profit.

Similarly, I continued to use the `.group_by` function to group the two value columns, *"city"* and *"total_price"*, and then calculated the total revenue to determine which city had the highest revenue. Finally, I converted it into percentages to represent the information more clearly.

<img width="947" height="341" alt="image" src="https://github.com/user-attachments/assets/1536d62b-7774-4ea9-a3a1-6d5c47774215" />
<img width="537" height="346" alt="image" src="https://github.com/user-attachments/assets/0e0dd04b-117f-4dc3-bd21-40b86426a7a0" />


<img width="640" height="586" alt="image" src="https://github.com/user-attachments/assets/4f598b9a-0840-49cd-ab89-9c4ac0b12609" />

*Figure 2. Total Sales by City*

Looking at the pie chart, it can be seen that the three regions do **not have a significant difference** in revenue. **Chicago** is the city that generates the most revenue for this supermarket, accounting for **nearly 36%** of total revenue. The **New York** area is also strong, accounting for **nearly 35%** of revenue, while **Los Angeles** is the lowest, accounting for **less than 30% **of total revenue.

---

### 5. Conclusion
Through the process of analyzing sales data for this supermarket, I have identified two key insights. Firstly, **Fruits** are the most popular and sought-after item, indicating that customers are very interested in maintaining their **health** with organic foods. Secondly, **Chicago** was identified as the area generating the highest revenue, but overall, all three areas had roughly equal percentages of revenue. This suggests that the supermarket **needs effective development strategies** such as diversifying product offerings, understanding customer needs, and so on, in order to increase profitability.








