## SQL Queries Used in This Project (with Output Snapshots)

- Daily Trend for Total Orders
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
```
Output:
<img width="367" height="325" alt="image" src="https://github.com/user-attachments/assets/bf395f2f-b242-4d26-9232-9847fd0662d2" />

- % of Sales by Pizza Category
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
```
Output:
<img width="601" height="275" alt="image" src="https://github.com/user-attachments/assets/0e017ac0-1214-44ac-a07b-0f8553a9acad" />

- % of Sales by Pizza Size
```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
```
Output:
<img width="549" height="318" alt="image" src="https://github.com/user-attachments/assets/abbb93f8-fa36-4092-9e9e-cbf8bfd35fcd" />

- Total Pizzas Sold by Pizza Category
```sql
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
```
Output:
<img width="565" height="271" alt="image" src="https://github.com/user-attachments/assets/d76d4f05-f532-4ba6-8b94-07f489dc3960" />

- Top 5 Pizzas by Revenue
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
```
Output:
<img width="516" height="242" alt="image" src="https://github.com/user-attachments/assets/eeb279e2-2665-46ad-8108-a66f9215ada7" />

- Bottom 5 Pizzas by Revenue
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
```
Output:
<img width="560" height="211" alt="image" src="https://github.com/user-attachments/assets/5f2b0ca7-1418-44c3-9f7c-f38ecb259b17" />

- Top 5 Pizzas by Quantity
```sql
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
```
Output
<img width="716" height="283" alt="image" src="https://github.com/user-attachments/assets/811ba708-a7c7-4954-8014-6fed069e0b32" />

- Bottom 5 Pizzas by Quantity
```sql
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
```
Output:
<img width="667" height="305" alt="image" src="https://github.com/user-attachments/assets/98def597-48ae-49ab-8a7d-5bb93ca1dff2" />

- Top 5 Pizzas by Total Orders
```sql
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
```
<img width="516" height="264" alt="image" src="https://github.com/user-attachments/assets/82781979-a290-4200-8c39-c66fbeaeae01" />
