# Full-data-analyst-project
this will allow us to compare the sales performance of different pizza categories 

6 top 5 best sellers by revenue, total quantity and total orders
create a bar chart highliting the top 5 best selling pizzas based on revenue total quantity total orders
this chart will help us identify the most popular pizza options 

7 bottom 5 best sellers by revenue total quantity and total orders

create a bar chart show casing the bottom 5 worst selling pizzas based on revenue total quantity total orders this chart will ensble 
us to identify underperforming
or less popular pizza options



ANSWERSS FOR QUSTIONS

1 select SUM(total_price) as total_revenue from pizza_sales

2 select sum(total_price)/count(distinct order_id) as Average_order from pizza_sales

3 select sum(quantity) AS pizza_sold  from pizza_sales

4 select sum(distinct order_id) as total_orders from pizza_sales

5 select cast( Cast(sum(quantity) as decimal(10,2))/CAST(COUNT(distinct order_id) as decimal(10,2))
as decimal(10,2)) as AVG_pizza_pre_order from pizza_sales

CHART ANSWERS 
DAIL TREND
6 SeLect DATENAME(DW,order_date) as order_day,count(distinct order_id) as total_orders from pizza_sales 
group by DATENAME(DW,order_date)

7 -----HOURLY TREND
SELECT DATEPART(HOUR,order_time) AS order_hours,count(distinct order_id) as total_orders from pizza_sales 
group by DATEPART(HOUR,order_time)

8------ percentage of sales by pizza category
SELECT pizza_category,sum(total_price)*100/(select sum(total_price) from pizza_sales
 where MONTH(order_date)=1) as perc_of_category_sales 
from pizza_sales where MONTH(order_date)=1  group by pizza_category
