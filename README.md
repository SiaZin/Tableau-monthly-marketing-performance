# monthly-marketing-performance-tableau
Tableau dashboard and analyis of monthly marketing performance by channel, country, and device using ROAS, CAC, ARPU, ARPPU, payer conversion, and 90-day revenue metrics

## Repository Structure

## Data
Source: SKELAR Data Analytics Intensive (2026) 

Data description:

spend.csv — expenses by channel
| Field | Type | Example  |        Description        |
| ----- | ---- | -------- | ------------------------- |
|date   | date |2025-03-14|	       Дата витрат        |
|channel|string| 	 Meta   |Meta, Google, TikTok, Email|
|  geo  |string|	  US	  |     UA, PL, DE, US, UK    |
| spend	|float |	 324.55 |	        Витрати у $       |

users.csv - usesrs and revenue
|      Field      | Type  | Example  |            Description          |
| --------------- | ----- | -------- | ------------------------------- |
|     id_user     |	string|U00012345 |	      Унікальний ID юзера      |
|registration_date|	date  |2025-04-02|	        Дата реєстрації        |
|     channel     |	string|	 Google  |	       Канал залучення         |
|       geo       |	string|	   DE    |	           Гео юзера           |
|    device_os    |	string| 	 iOS   |    	   iOS, Android, Web       |
|     is_payer    |	 0/1  |	    1	   |      Чи став юзер платником     |
|    revenue_7d	  | float |	  12.40  |Виручка за 7 днів від реєстрації |
|   revenue_90d   |	float |   48.90  |Виручка за 90 днів від реєстрації|


