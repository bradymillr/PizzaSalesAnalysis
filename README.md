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
``` SQL
SELECT 
name,
COUNT(*) as "times_ordered"
FROM pizza.sales
GROUP BY name
order by times_ordered desc
LIMIT 5;

```

### Potential Recommendations

1. Suggestion
2. Suggestion
3. Suggestion
