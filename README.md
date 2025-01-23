# Restaurant-Order-Analysis

## Table of contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#Tools)
- [Exploratoy Data Analysis](#Exploratoy-Data-Analysis)
- [Data Analysis](#Data-Analysis)
- [Results/ Findings](#Results-Findings)
- [Recomendations](#Recomendations)
- [Limitations of the Analysis](#limitations-of-the-analysis)
  
## Project Overview

This project focuses on analyzing a dataset from a fictional restaurant stored in a database called restaurant_db. Using SQL queries, I explored and analyzed key tables (menu_items and order_details) to uncover valuable insights about the menu items, customer orders, and purchasing behavior.

Project Aim :
The main goal of this project is to provide actionable insights that can help improve restaurant management. This includes identifying the most popular dishes, understanding revenue patterns from orders, and analyzing customer behavior to support data-driven decision-making.

### Data Sources 

- The dataset used for this analysis comes from ([Maven Analytics](https://app.mavenanalytics.io/))  , a comprehensive platform designed for data professionals and aspiring analysts to develop their skills, showcase their work, and advance their careers.
  
### Tools

- SQL Server


### Exploratoy Data Analysis 

The EDA focused on the menu_items and order_details tables from the restaurant_db database. SQL queries were used to uncover key insights into menu items, customer orders, and purchasing behavior, providing a clear understanding of the data and answering critical questions such as:

- Menu Analysis:
What are the top-selling menu items across different categories, and how does this information impact menu optimization and pricing strategies?

- Order Analysis:
What were the top 5 orders by monetary value?

- Customer Behavior:
What were the least and most ordered items? What categories were they in?

### Data Analysis
Inclusion de algunos codigos utilizados para encontrar las respuestas a las preguntas. 

```SQL
select item_name, category, count(order_details_id) as num_purchases
from order_details od 
left join menu_items mi
on od.item_id = mi.menu_item_id
group by item_name, category
order by num_purchases DESC;
```

```SQL
select order_id, sum(price) as total_spend
from order_details od 
left join menu_items mi
on od.item_id = mi.menu_item_id
group by order_id
order by total_spend DESC
limit 5; 
```

```SQL
select item_name, category, count(order_details_id) as num_purchases
from order_details od 
left join menu_items mi
on od.item_id = mi.menu_item_id
group by item_name, category
order by num_purchases;
```

### Results/ Findings 

The analysis results are summarized as follows: 

-Menu Analysis:
The most ordered items, like the Hamburger (622 orders) and Edamame (620 orders), are clear customer favorites and should be highlighted in promotions or as signature dishes. Low-performing items, such as Chicken Tacos (123 orders), may need recipe adjustments, price changes, or removal to optimize the menu and improve profitability.

-High-Value Orders:
The top 5 highest-value orders reveal patterns in customer spending, such as popular item combinations and high-demand categories.

-Performance Insights:
The data reveals clear contrasts between top-performing items like Hamburgers and French Fries, which drive consistent revenue, and low-demand items like Chicken Tacos, which may need reformulation or removal. Optimizing the menu based on customer preferences enhances efficiency, reduces waste, and better aligns with market demands.

### Recomendations

-Based on the analysis , we recommend the following actions: 

-  Promote Top-Performing Items:
Highlight customer favorites like Hamburgers and French Fries through targeted promotions and feature them as signature dishes. This will boost sales and reinforce customer loyalty, driving consistent revenue.

-  Reevaluate and Optimize Low-Performing Items:
Revise or remove underperforming items, such as Chicken Tacos, to streamline the menu and reduce waste. This ensures that the menu is aligned with customer preferences, improving overall profitability.

-  Leverage High-Value Orders for Upselling:
Use insights from high-value orders to design attractive bundled offers and upselling strategies. By focusing on popular item combinations, the restaurant can increase the average order value and maximize revenue.


### Limitations of the Analysis

Lack of Customer Segmentation 
-   The analysis does not consider customer demographics or preferences in depth. More detailed segmentation (e.g., age, location, dining habits) could provide a better understanding of customer behavior and enhance the personalization of recommendations.


### References 

1- ([Maven Analytics](https://app.mavenanalytics.io/))

