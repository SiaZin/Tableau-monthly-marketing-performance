# Tableau-monthly-marketing-performance
Tableau dashboard and analysis of monthly marketing performance by channel, country, and device using ROAS, CAC, ARPU, ARPPU, payer conversion, and 90-day revenue metrics

<img src="/screenshots/dashboard.png" width="700" height="500">

## Repository Structure

##🔡Data
Source: SKELAR Data Analytics Intensive (2026) 

Data description:

[`spend.csv`](spend.csv) — expenses by channel
| Field | Type | Example  |        Description        |
| ----- | ---- | -------- | ------------------------- |
|date   | date |2025-03-14|	     Date of expenses     |
|channel|string| 	 Meta   |Meta, Google, TikTok, Email|
|  geo  |string|	  US	  |     UA, PL, DE, US, UK    |
| spend	|float |	 324.55 |	       Expenses in $      |

[`users.csv`](users.csv) — users and revenue
|      Field      | Type  | Example  |               Description            |
| --------------- | ----- | -------- | ------------------------------------ |
|     id_user     |	string|U00012345 |	            Unique user ID          |
|registration_date|	date  |2025-04-02|	          Registration date         |
|     channel     |	string|	 Google  |	        Acquisition channel         |
|       geo       |	string|	   DE    |	              User's geo            |
|    device_os    |	string| 	 iOS   |    	      iOS, Android, Web         |
|     is_payer    |	 0/1  |	    1	   |  Has the user become a paying user?  |
|    revenue_7d	  | float |	  12.40  |Revenue from registration over 7 days |
|   revenue_90d   |	float |   48.90  |Revenue from registration over 90 days|

## 📃Overview 


> [!NOTE]
> Опис дашборду та висновки українською [ukr_marketing_channels_performance.pdf](ukr_marketing_channels_performance.pdf) 
> 
> My dashboard is published here [Tableau Public](https://public.tableau.com/views/MonthlyMarketingPerformanceReport_17792191120910/Dashboard1?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) 
>
> Tableau Packaged Workbook here [Monthly_marketing_performance](Monthly_marketing_performance.twbx)  

# Data preparation
Before visualizing, I joined two tables. To perform the join, I aggregated `users.csv` to the day × channel × geo level (using `registration_date`) and joined it with `expenses.csv`. Used BigQuery and then connected it to Tableau.

<details>
<summary>Joining and aggregating</summary>
  
```
WITH users_agg AS (
  SELECT
    registration_date AS date,
    channel,
    geo,
    COUNT(DISTINCT id_user) AS registrations,
    SUM(is_payer) AS payers,
    ROUND(SUM(revenue_7d), 3) AS revenue_7d,
    ROUND(SUM(revenue_90d), 3) AS revenue_90d
  FROM `Tableau_homework.users`
  GROUP BY date, channel, geo
)
SELECT
  s.date,
  s.channel,
  s.geo,
  s.spend,

  COALESCE(u.registrations, 0) AS registrations,
  COALESCE(u.payers, 0) AS payers,
  COALESCE(u.revenue_7d, 0) AS revenue_7d,
  COALESCE(u.revenue_90d, 0) AS revenue_90d

FROM `Tableau_homework.spend` AS s
LEFT JOIN users_agg AS u
  ON s.date = u.date
  AND s.channel = u.channel
  AND s.geo = u.geo
ORDER BY s.date, s.channel, s.geo;
```
</details>

The results were saved to [`joined_tables.csv`](joined_tables.csv)

## Results


