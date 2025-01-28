# Consumer Behavior and Revenue Insights



1. What are the top categories generating the highest revenue?

2. Are customers who use promo codes spending less on average than those who don't?

3. What is the average review rating by product size and color?

4. Which season has the highest sales volume, and does it vary by location?

5. What is the purchasing frequency of subscription vs. non-subscription customers?



``` SQL
#  What are the top categories generating the highest revenue?
SELECT 
    Category, 
    SUM("Purchase_Amount_(USD)") AS Total_Revenue
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Category
ORDER BY 
    Total_Revenue DESC;
```

