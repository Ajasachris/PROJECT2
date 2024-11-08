# CUSTOMER SEGMENTATION FOR A SUBSCRIPTION SERVICE ANALYSIS

### PROJECT OVERVIEW
---
Customer segmentation is a powerful strategy for understanding and catering to different customer needs, preferences, and behaviors within a subscription service. By dividing the customer base into distinct groups, or "segments," a subscription business can tailor its marketing, product offerings, and customer engagement strategies to maximize satisfaction, reduce churn, and drive growth. Here’s an overview of the key aspects of customer segmentation for a subscription service:


# MS EXCEL

 ### PROJECT OBJECTIVE
---
This project was designed to address the following analysis goals.

-  Analyze Customer Data and using pivot tables to find Subsription Patterns

- To calculate average Subcription duration and identify most popular subscription types.

### FORMULAR USED
---
```
Average Subscription = Total Subscription / no of customers
```

### TOOLS AND METHOD USED
---
- Data Analysis: the data was analyzed using Microsoft excel using pivot tables to organize, summarize and filter data for easier interpertation.
- Data Visualization: Bar chart were created in excel to visually represent key insights.

### VISUAL ANALYSIS

### SUBSCRIPTION PATTERN 

![Screenshot 2024-11-05 082154](https://github.com/user-attachments/assets/4f9e0466-5a2a-472c-ad8e-9caaa4a85577)

### AVERAGE DURATION

![Screenshot 2024-11-05 082723](https://github.com/user-attachments/assets/c23ecdc5-0c70-491c-92fb-697c4e9583dc)

### MOST POPULAR SUBSCRIPTION TYPES
![Screenshot 2024-11-05 082930](https://github.com/user-attachments/assets/b447ac06-2460-44d6-805c-b97f30494f00)








# STRUCTURED QUERY LANGUAGE

### SKILLS
---
The set of skills were used for the optimization of the analysis, which were:
- Create  database (new schema)
- Create a table based on the field name,
- Populate the data into the table created at each field,
- Verify that data populated in the field,
- Analyse the data,

### DATA TRANSFORMATION
---
- Data was opened into Excel to study the data pattern which was later profiled, sorted and filtered to ensure the data types, remove nulls, duplicates, and empty cells and to ensure the data was ready for use.
Analysis
- SSMS were used to run the analysis including the data manipulation.

### PROJECT OBJECTIVE
---
Use the resources to answer the following business questions.
### retrieve the total number of customers from each region.
```
SELECT Region, COUNT(CustomerID) AS Numbers_customer
FROM [dbo].[CustomerData]
GROUP BY Region;
```

### find the most popular subscription type by the number of customers.

```
SELECT SubscriptionType, COUNT(CustomerID) AS number_custormers 
FROM [dbo].[CustomerData]
GROUP BY SubscriptionType
ORDER BY number_custormers;
```

### find customers who canceled their subscription within 6 months.
```
SELECT CustomerName, Canceled, SubscriptionEnd, SubscriptionStart
FROM [dbo].[CustomerData]
WHERE DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) <= 180
ORDER BY Canceled;
```
### calculate the average subscription duration for all customers.
```
SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) AS avg_subscription_duration
FROM [dbo].[CustomerData]
WHERE SubscriptionEnd IS NOT NULL;
```
### find customers with subscriptions longer than 12 months.
```
SELECT CustomerID, SubscriptionEnd, SubscriptionStart
FROM [dbo].[CustomerData]
WHERE DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) > 365;
```
### calculate total revenue by subscription type. 
```
SELECT SubscriptionType, SUM(Revenue) AS Total_revenue 
FROM [dbo].[CustomerData]
GROUP BY SubscriptionType
ORDER BY Total_revenue;
```
### find the top 3 regions by subscription cancellations.
```
SELECT TOP 3 Region, COUNT(Canceled) AS CanceledCount
FROM [dbo].[CustomerData]
GROUP BY Region
ORDER BY COUNT(Canceled) DESC;
```
### find the total number of active and canceled subscriptions.
```
SELECT 
    COUNT(CASE 
            WHEN SubscriptionEnd IS NULL OR SubscriptionEnd > GETDATE() THEN 1 
          END) AS Active_Subscriptions,
    COUNT(CASE 
            WHEN SubscriptionEnd IS NOT NULL AND SubscriptionEnd <= GETDATE() THEN 1 
          END) AS Canceled_Subscriptions
FROM [dbo].[CustomerData];
```


# POWER BI

### PROJECT OBJECTIVE
Build a POWER BI dashboard that visualizes key customer segments, cancellations, subscription trends. include slicers for interative analysis.

![Screenshot 2024-11-05 083145](https://github.com/user-attachments/assets/3a3580fd-cf65-4605-add3-8eb3fb8b5073)



