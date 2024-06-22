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
2. What pizza has brought the (by revenue)?
3. What is the average price of pizza by size?
4. What is the total revenue generated from pizza sales each month?

### Findings
**The Most Popular Pizza By Order is Classic Deluxe**
``` SQL
SELECT 
name,
COUNT(*) as "times_ordered"
FROM pizza.sales
GROUP BY name
order by times_ordered desc
LIMIT 5;
```
The intended goal of the query above was to count the frequency of each type of pizza occuring within the large dataset to determine the most popular pizza type. I decided to limit this query to five results as there are originalyl 32 types of pizza on the menu, making the results from the query a bit overwhelming. As we can see in the table below, the Classic Deluxe Pizza is the most popular pizza from this dataset with 2453 orders, followed by barbeque chicken, hawaiian, pepperoni, and thai chicken.

| Pizza Name   | Total |
|:-------------|------:|
| classic_dlx	 | 2453  |
| bbq_ckn	     | 2432  | 
| hawaiian	   | 2422  |
| pepperoni	   | 2418  |
| thai_ckn	   | 2371  |

### Potential Recommendations

1. Suggestion
2. Suggestion
3. Suggestion
