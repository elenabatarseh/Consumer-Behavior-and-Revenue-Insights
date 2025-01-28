# Consumer Behavior and Revenue Insights



1. What are the top categories generating the highest revenue?

2. Which season has the highest sales volume, and does it vary by location?

3. Which demographics (age, gender, income) are most valuable to the business?

4. How do preferred payment methods vary by region?

5. What are the spending patterns based on age groups, and how does this correlate with product preferences?

6. What are the top-performing locations, and what factors contribute to their success?






#### What are the top categories generating the highest revenue?

``` SQL
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

#### Which season has the highest sales volume, and does it vary by location?

 ``` SQL
SELECT 
    Season, 
    Location, 
    COUNT(Item_Purchased) AS Total_Sales
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Season, location
ORDER BY 
    Total_Sales DESC;
```

#### Which demographics (age, gender) are most valuable to the business?

``` SQL
SELECT 
    Age, 
    Gender, 
    AVG("Purchase_Amount_(USD)") AS Avg_Spend, 
    SUM("Purchase_Amount_(USD)") AS Total_Spend
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Age, Gender
ORDER BY 
    Total_Spend DESC;
```

#### How do preferred payment methods vary by region?

``` SQL
SELECT 
    Location, 
    Preferred_Payment_Method, 
    COUNT(*) AS Total_Transactions
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Location, Preferred_Payment_Method
ORDER BY 
    Total_Transactions DESC;
```

#### What are the spending patterns based on age groups, and how does this correlate with product preferences?

``` SQL
SELECT 
    CASE 
        WHEN Age < 25 THEN 'Under 25'
        WHEN Age BETWEEN 25 AND 40 THEN '25-40'
        WHEN Age BETWEEN 41 AND 60 THEN '41-60'
        ELSE 'Above 60'
    END AS Age_Group,
    Category, 
    SUM("Purchase_Amount_(USD)") AS Total_Spending, 
    COUNT(*) AS Total_Transactions
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Age_Group, Category
ORDER BY 
    Total_Spending DESC;
```

#### What are the top-performing locations, and what factors contribute to their success?

``` SQL
SELECT 
    Location, 
    SUM("Purchase_Amount_(USD)") AS Total_Revenue, 
    AVG(Review_Rating) AS Avg_Review, 
    COUNT(DISTINCT Customer_ID) AS Total_Customers
FROM 
    SHOPPINGTRENDS
GROUP BY 
    Location
ORDER BY 
    Total_Revenue DESC;
```






