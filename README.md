# monthly-marketing-performance-tableau
Tableau dashboard and analysis of monthly marketing performance by channel, country, and device using ROAS, CAC, ARPU, ARPPU, payer conversion, and 90-day revenue metrics

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
> [ukr_marketing_channels_performance.pdf](ukr_marketing_channels_performance.pdf) - Full analysis in Ukrainian

## Results


