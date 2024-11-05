### PROJECT TITLE: CUSTOMER-SEGMENTATION-ANALYSIS

[PROJECT OVERVIEW]
[DATA SOURCES]
[TOOLS USED]
[DATA CLEANING AND PREPARATION]
[EXPLORATORY DATA ANALYSIS]
[DATA ANALYSIS]
[DATA VISUALIZATION]
[RECOMMENDATION AND CONCLUSION]

### PROJECT OVERVIEW
This project involves analyzing customer data for a subscription service to identify 
segments and trends. The goal is to understand customer behavior, track subscription types, 
and identify key trends in cancellations and renewals. The final deliverable is a Power BI 
dashboard that presents the analysis.

### DATA SOURCES
The Primary source of Data used is the Customer Segmentation for a Subscription service downloaded from the Learning Management System of the Ladies in Tech Africa.

### TOOLS USED
* Microsoft Excel [Download here](https://www.microsoft.com)

  a. Check for Duplicates

  b. Remove Duplicates (data cleaning)

  c. Added Column to show End of Subscription

  d. Visualization

* SQL- Structured Query Language for querying the Customer Subscription

* PowerBI- for creating Visualization

### DATA CLEANING AND PREPARATION
For Data cleaning and preparation, I carried out the following:

* Data loading and inspection
* Checked for Duplicates
* Removed duplicates
* Data cleaning using column profile 

### EXPLORATORY DATA ANALYSIS
This involved exploring the data to answer some questions such as:

* understanding customer behavior
  
*  track subscription types
  
*  identify key trends in cancellations and renewals
  
### DATA ANALYSIS
some basic lines of codes and queries used:

```
SELECT * FROM[dbo].[CustomerProject]

-----1----- retrieve the total number of customers from each region.------
SELECT Region,count(customerID) as total_customers
FROM[dbo].[CustomerProject]
GROUP BY Region;

----2----- find the most popular subscription type by the number of customers------
SELECT Top 1 SubscriptionType, Count(distinct customerId) as Total_customers
FROM[dbo].[CustomerProject]
GROUP BY SubscriptionType
ORDER BY total_customers DESC;

-----3---find customers who canceled their subscription within 6 months-----
SELECT CustomerID, SubscriptionStart, SubscriptionEnd 
FROM [dbo].[CustomerProject]
WHERE datediff(MONTH,Subscriptionstart,Subscriptionend) <= 6;

-----4-------calculate the average subscription duration for all customers-------
SELECT AVG(Datediff(day,SubscriptionStart,SubscriptionEnd)) as avg_subscription_duration
FROM [dbo].[CustomerProject];

-----5-----find customers with subscriptions longer than 12 months----
SELECT CustomerID
FROM[dbo].[CustomerProject]
WHERE datediff(day,SubscriptionStart,SubscriptionEnd) > 12;

SELECT * FROM [dbo].[CustomerProject]

-----6-----calculate total revenue by subscription type-----
SELECT SubscriptionType,
SUM(Revenue) as total_revenue
FROM [dbo].[CustomerProject]
GROUP BY SubscriptionType;

-----7-----find the top 3 regions by subscription cancellations-----
SELECT TOP 3 Region,
count (SubscriptionEnd) as SubscriptionEnd
FROM[dbo].[CustomerProject]
WHERE SubscriptionEnd is NOT NULL
GROUP BY Region
ORDER BY SubscriptionEnd DESC;

-----8------find the total number of active and canceled subscriptions----
SELECT SUM(CASE WHEN SubscriptionEnd is NULL THEN 1 ELSE 0 END) as total_active_Subscriptions,
SUM(CASE WHEN SubscriptionEnd is not null THEN 1 ELSE 0 END) as total_canceled_Subscriptions
FROM [dbo].[CustomerProject];

```









### DATA VISUALIZATION
### RECOMMENDATION AND CONCLUSION
