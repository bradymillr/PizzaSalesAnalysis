# Pizza Sales Analysis

## Table of Contents
- [Overview](overview)
- [Questions](questions)
- [Findings](findings)
- [Potential Recommendations](potential-recommendations)

### Overview

Example Text

### Questions
1. What is the most popular pizza (by orders)?
2. What pizza has brought the most revenue?
3. What is the average price of pizza by size?
4. What is the total revenue generated from pizza sales each month?

### Findings
1. **The Most Popular Pizza By Order is Classic Deluxe**
``` SQL
SELECT 
name,
COUNT(*) as "times_ordered"
FROM pizza.sales
GROUP BY name
order by times_ordered desc
LIMIT 5;
```
The intended goal of the query above was to count the frequency of each type of pizza occuring within the large dataset to determine the most popular pizza type. I decided to limit this query to five results as there are originally 32 types of pizza on the menu, making the results from the query a bit overwhelming. As we can see in the table below, the Classic Deluxe Pizza is the most popular pizza from this dataset with 2453 orders, followed by barbeque chicken, hawaiian, pepperoni, and thai chicken.

| name         | times_ordered |
|:-------------|--------------:|
| classic_dlx	 | 2453          |
| bbq_ckn	     | 2432          | 
| hawaiian	   | 2422          |
| pepperoni	   | 2418          |
| thai_ckn	   | 2371          |

2. **The Most Ordered Pizza Did Not Bring in The Most Revenue**
``` SQL
SELECT 
name,
COUNT(*) as "times_ordered",
SUM(price) as "total_revenue"
FROM pizza.sales

GROUP BY name
ORDER BY total_revenue DESC
LIMIT 5;
```
Since we had previously determined the pizza that had sold the most volume in this dataset, it caused me to wonder whether or not these high volume items lead to a large drive in revenue. The goal of this query was the total the revenue while still displaying the times ordered for easy comparison to the last query. As we can see in our new table below, Thai Chicken which was the pizza at the bottom of the top 5 sales query, brought in the most revenue in our dataset. While some of the previous results are also contained in this query, there are new pizzas such as the Spicy Italian which was purchased 400 times less than the number one spot.

| name         | times_ordered |  total_revenue |     
|:-------------|--------------:|---------------:|
| classic_dlx	 | 2453          | 43434.25       |
| bbq_ckn	     | 2432          | 42768          |
| hawaiian	   | 2422          | 41409.5        |
| pepperoni	   | 2418          | 38180.5        |
| thai_ckn	   | 2371          | 34831.25       |
### Potential Recommendations

1. Suggestion
2. Suggestion
3. Suggestion
