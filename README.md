# Pizza Sales Analysis

## Table of Contents
- [Overview](#overview)
- [Questions](#questions) 
- [Findings](#findings)
- [Potential Recommendations](#potential-recommendations)

## Overview

Example Text

## Questions
1. What is the most popular pizza (by orders)?
2. What pizza has brought the most revenue?
3. What day of the week brings in the most and least amount of revenue?
4. What size of pizza is ordered the least?

## Findings
**1. The Most Popular Pizza By Order is Classic Deluxe**
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

**2. The Most Ordered Pizza Did Not Bring in The Most Revenue**
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
| thai_ckn	   | 2371          | 43434.25       |
| bbq_ckn	     | 2432          | 42768          |
| cali_ckn	   | 2370          | 41409.5        |
| classic_dlx  | 2453          | 38180.5        |
| spicy_ital	 | 1924          | 34831.25       |

**3. Friday is The Busiest Day of The Week and Sunday Is The Slowest**
``` SQL
SELECT 
    DATE_FORMAT(date, '%W') AS weekday,
    ROUND(AVG(price) ,2) AS average_price,
    COUNT(type) as total_sales,
	ROUND(SUM(price) ,2) AS total_revenue
FROM 
    pizza.sales
GROUP BY 
    weekday
ORDER BY 
    total_revenue DESC;
```
Moving beyond answering potential inquiries as an analyst, I wanted to move to an example scenario where we must determine what is the busiest day of the week and more importantly, what is the slowest day of the week. In the query above, I wanted to include the average price of a purchase when a customer orders at our pizza place, additionally I wanted to total the revenue over the life of the dataset to determine historically, where the days of the week rank. Lastly, I included the frequency of orders for a familar output. I formatted the date for a simplistic name result and rounded our average price into an easy-to-understand dollar amount. Lastly I grouped our results by the weekday to see the table below.

| weekday         | average_price |  total_sales | total_revenue |   
|:----------------|--------------:|-------------:|--------------:|
| Friday	        | 16.51         | 8242         | 136073.9      |
| Thursday	      | 16.52         | 7478         | 123528.5      |
| Saturday	      | 16.44         | 7493         | 123182.4      |
| Wednesday       | 16.47         | 6946         | 114408.4      |
| Tuesday	        | 16.55         | 6895         | 114113.8      |
| Monday          | 16.55         | 6485         | 107329.55     |
| Sunday	        | 16.44         | 6035         | 99203.5       |

**4. The XXL Size Is Ordered Infrequently And Could Be Replaced With a Better Offering**
``` SQL
SELECT 
    size,
    COUNT(*) AS times_ordered,
    ROUND(SUM(price),2) AS total_revenue
FROM 
    pizza.sales
GROUP BY 
    size
ORDER BY 
   times_ordered ASC;
```
Finally, I wanted to look at something potentially negative to be discovered when analyzing the data, which in this case is a size of pizza that is not ordered frequently to drive enough revenue, and therefore should be replaced with a better offering. In this query, I select the size along with the count of all entries paired with the total revenue which is calculated by summing all the prices when grouped by size. As we can see in the table below, the XXL is ordered very infrequently, and only drove 1000 dollars in revenue. But what are we supposed to do about this? More in the Potential Reccomendations Section.

| size         | times_ordered | total_revenue |   
|:-------------|--------------:|--------------:|
| XXL	         | 28            | 1006.6        |
| XL	         | 552           | 14076         | 
| S	           | 14403         | 178076.5      | 
| M            | 15635         | 249328.25     |
| L            | 18956         | 375318.7      |


## Potential Recommendations

***1. Run A Special on Sunday's To Boost Sales***

  As we can see from my findings for the third question we established that Sunday's a far less busy than any other day of the week, especially when compared to the top performing days. Therefore, I it would be fiscally advantageous to have a special such as buy one pizza get another 50% off of Sunday's to help faciliate more sales, and drive more revenue.
  
***2. Replace the XL Pizza With Breadsticks/Cheesesticks***

  Based on this dataset, the offerings within this restaurant are limited to only pizza, which causes the restaurant to miss out on other markets or add-on purchases. Therefore, I suggest adding breadsticks/cheesesticks to the menu to help facilate a potential special on Sunday's as mentioned above, along with more sales overall. All the equipment, tools, and ingredients to make these two new offerings are already owned and utilized by this restaurant. This means there is no realized price tag on this endeavor, other than making more dough to compensate for more orders. However this cost is already included inside of the margin of creating and cooking orders.

