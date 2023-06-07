# Cyclistic Bike Share: A Google Data Analytics Capstone Project

## Scenario :
In this case study I will be a data analyst working for a bike-share company called Cyclistic. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, our team will design a new marketing strategy to convert casual riders into annual members.

## Company : 
Cyclistic is a Chicago bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The bikes can be unlocked from one station and returned to any other station in the system anytime.
Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

# ASK
## Business Task : 
Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, the marketing director believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, she believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.
The marketing director has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. She and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.
Three questions will guide the future marketing program: 
	1. How do annual members and casual riders use Cyclistic bikes differently? 
	2. Why would casual riders buy Cyclistic annual memberships? 
	3. How can Cyclistic use digital media to influence casual riders to become members?

## Mission :
I was assigned the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

# PREPARE
For this project, I used 12 months of Cyclistic's 2022-2023 bike ride data from the Divvy database here. The trip data used is from Mar 2022 to Feb 2023, and has been made available by Motivate International Inc. under this license.
They are CSV files with 13 columns and more than 500 000 rows for each files. Each rows represent one ride with a unique ride id while the columns are as follows : 
- ride_id
- rideable_type
- started_at
- ended_at
- start_station_name
- start_station_id
- end_station_name
- end_station_id
- start_lat
- start_lng
- end_lat
- end_lng
- member_casual 
With some inspection of the file using excel we can right of the bat realise that multiple blank values are present.

## Does the data ROCCC ?
	- Reliable - YES, data is accurate, complete, and unbiased
	- Original - YES, we can locate the original, public data source
	- Comprehensive - YES, information is complete and extensive
	- Current - YES, data is updated monthly
	- Cited - YES

# PROCESS
I chose to first peaked at the different datasets through Excel and then to aggregate everything in SQL, it was far simpler to access quickly to the data with excel but once combined the datasets would have been too large (more than 6 millions rows) so I needed a system that could handle such large amount of data like Microsoft SQL Server. I named appropriately the 12 CSV files depending on the month (for eg: cyclistic_07_2022 for the month of July) and imported them into SQL SERVER. The aggregated sataset is called cyclistic_yearly_total.
```
CREATE TABLE cyclistic_yearly_total
	( 
		ride_id nvarchar(255),
		rideable_type nvarchar(255),
		started_at datetime,
		ended_at datetime,
		start_station_name nvarchar(255),
		start_station_id nvarchar(255),
		end_station_name nvarchar(255),
		end_station_id nvarchar(255),
		start_lat float,
		start_lng float,
		end_lat float,
		end_lng float,
		member_casual nvarchar(255)
			)
```
```
INSERT INTO
	cyclistic_yearly_total

-- ALL YEAR COMBINED -- RAW DATA TABLE
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, CONVERT(nvarchar(255),start_station_id) AS start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2023_03$']
-- March 2023
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2023_02$']
-- February 2023
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2023_01$']
--January 2023
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, CONVERT(nvarchar(255), end_station_id) AS end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_12$']
-- December 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, CONVERT(nvarchar(255),start_station_id) AS start_station_id, end_station_name, CONVERT(nvarchar(255), end_station_id) AS end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_11$']
-- November 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, CONVERT(nvarchar(255),start_station_id) AS start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_10$']
-- October 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_legnth AS ride_length, day_of_week, start_station_name, start_station_id, end_station_name, CONVERT(nvarchar(255), end_station_id) AS end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_09$']
-- September 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_08$']
-- August 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, CONVERT(nvarchar(255),start_station_id) AS start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_07$']
-- July 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_06$']
-- June 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_05$']
-- May 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, CONVERT(nvarchar(255),start_station_id) AS start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_04$']
-- April 2022
UNION
SELECT ride_id, rideable_type, started_at, ended_at, ride_length, day_of_week, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, member_casual
FROM dbo.['2022_03$']
-- March 2022
ORDER BY 3
```

To help the analysis of the data I need to create a column which will indicate the duration of each trip  :
```
ALTER TABLE cyclistic_yearly_total
ADD ride_length_second bigint

UPDATE cyclistic_yearly_total
SET ride_length_second = CAST(DATEDIFF(second, started_at, ended_at) AS bigint)
```
I will then create a column which will state in which day of the week did the trip started :
```
ALTER TABLE cyclistic_yearly_total
ADD day_of_week VARCHAR(20)

UPDATE  cyclistic_yearly_total
SET day_of_week = DATENAME(dw, started_at)
```

I will now proceed to do some checking, cleaning and get rid of impossible values (earlier ended time than started time and longer than 24 hrs trip for casual rider).
Checking if there a more type of customers than 2 (member or casual) which would be an error 
Check OK (only 2 values returned)
```
SELECT COUNT(DISTINCT member_casual)
FROM cyclistic_yearly_total
```

Checking if there a more than 3 types of bikes 
Check OK (only 3 values returned)
```
SELECT DISTINCT rideable_type
FROM cyclistic_yearly_total
```

Checking if there are started time later than end time for the same trip
```
SELECT *
FROM cyclistic_yearly_total
WHERE started_at >= ended_at
```

Checking if there are trip longer than 24 hours for casual customers (impossible)
```
SELECT *
FROM cyclistic_yearly_total
WHERE DATEDIFF(minute, started_at, ended_at) > 1440 AND member_casual = 'casual'
```
Deleting values unusable
```
DELETE FROM cyclistic_yearly_total
WHERE started_at >= ended_at

DELETE FROM cyclistic_yearly_total
WHERE DATEDIFF(minute, started_at, ended_at) > 1440 AND member_casual = 'casual'
```

There seems to be numerous null values particularly in the start_station_name,  start_station_id, end_station_name, end_station_id.
Based on our business task I believe indicating the most popular bike stations could be useful , I will measure how many rows have important missing datas and delete them
```
SELECT *
FROM cyclistic_yearly_total
WHERE end_station_name IS NOT NULL AND end_station_id IS NULL

SELECT *
FROM cyclistic_yearly_total
WHERE start_station_name IS NOT NULL AND start_station_id IS NULL
```

Since only start_station_id and end_station_id have NULLs values I will delete the unusable rows (Where the name AND id are null)
But before I do it, I will count how many rows it would represent

```
SELECT COUNT(*)
FROM cyclistic_yearly_total
WHERE start_station_name IS NULL AND start_station_id IS NULL 
	OR end_station_name IS NULL AND end_station_id IS NULL
```
```
-- 1 384 237 of nulls
-- 6 082 371 rows total
-- 22% of total rows
```
Deleting
```
DELETE
FROM cyclistic_yearly_total
WHERE start_station_name IS NULL AND start_station_id IS NULL 
	OR end_station_name IS NULL AND end_station_id IS NULL
  ```

# ANALYSIS
Business tasks : Compare how casual and members differs in cyclistic
Comparaison of average length of ride between casual and members
```
SELECT AVG(ride_length_second)/60 AS Avg_ride_length_member
FROM cyclistic_yearly_total
WHERE member_casual = 'member'

SELECT AVG(ride_length_second)/60 AS Avg_ride_length_casual
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
```
The average ride_length in minute for member customers is 12 mins
The average ride_length in minute for casual customers is 23 mins


Comparaison of number of rides between casual and members
```
SELECT COUNT(ride_id) AS mem_number_of_ride
FROM cyclistic_yearly_total
WHERE member_casual = 'member'

SELECT COUNT(ride_id) AS casu_number_of_ride
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
```
The number of rides for member customers is 2 858 705
The number of rides for casual customers is 1 839 429


Comparaison of day of week between casual and member customers
```
SELECT COUNT(ride_id) AS mem_number_of_ride, day_of_week
FROM cyclistic_yearly_total
WHERE member_casual = 'member'
GROUP BY day_of_week
ORDER BY COUNT(ride_id) DESC

SELECT COUNT(ride_id) AS casu_number_of_ride, day_of_week
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
GROUP BY day_of_week
ORDER BY COUNT(ride_id) DESC
```
The biggest days for members are Tuesday, Wednesday and Thursday
The biggest days for casuals are Saturday, Sunday and Friday


Month / Seasonal comparaisons between casual and member customers
```
SELECT COUNT(ride_id) AS mem_number_of_ride, DATENAME(month, started_at) AS month
FROM cyclistic_yearly_total
WHERE member_casual = 'member'
GROUP BY DATENAME(month, started_at)
ORDER BY mem_number_of_ride DESC

SELECT COUNT(ride_id) AS casu_number_of_ride, DATENAME(month, started_at) AS month
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
GROUP BY DATENAME(month, started_at)
ORDER BY casu_number_of_ride DESC
```
The seasonal use of cyclistic for members and casual are very similar in terms of months


Type of bike comparaison between casual and member customers
```
SELECT COUNT(ride_id) AS mem_number_of_ride, rideable_type
FROM cyclistic_yearly_total
WHERE member_casual = 'member'
GROUP BY rideable_type
ORDER BY mem_number_of_ride DESC

SELECT COUNT(ride_id) AS casu_number_of_ride, rideable_type
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
GROUP BY rideable_type
ORDER BY casu_number_of_ride DESC
```
The members mainly use classic bikes (almost as twice than electric bikes) and no docked bikes
Casual use of classic bike is slightly more than electric bike and a significant part also use docked bike

I want to do a comparaison of the time of day use between casual and member customer, to achieve that purpose I will create 4 bins to categorize the different parts of the day. 
I need to cast the started_at as time
Member :
```
SELECT 
    COUNT(ride_id) AS mem_number_of_ride,
    CASE 
        WHEN CAST(started_at AS TIME) >= '00:00:00' AND CAST(started_at AS TIME) < '06:00:00' THEN 'Night'
        WHEN CAST(started_at AS TIME) >= '06:00:00' AND CAST(started_at AS TIME) < '12:00:00' THEN 'Morning'
        WHEN CAST(started_at AS TIME) >= '12:00:00' AND CAST(started_at AS TIME) < '18:00:00' THEN 'Afternoon'
        WHEN CAST(started_at AS TIME) >= '18:00:00' AND CAST(started_at AS TIME) <= '23:59:59' THEN 'Evening'
        ELSE 'Other'
    END AS time_bin
FROM 
    cyclistic_yearly_total
WHERE 
    member_casual = 'member'
GROUP BY 
    CASE 
        WHEN CAST(started_at AS TIME) >= '00:00:00' AND CAST(started_at AS TIME) < '06:00:00' THEN 'Night'
        WHEN CAST(started_at AS TIME) >= '06:00:00' AND CAST(started_at AS TIME) < '12:00:00' THEN 'Morning'
        WHEN CAST(started_at AS TIME) >= '12:00:00' AND CAST(started_at AS TIME) < '18:00:00' THEN 'Afternoon'
        WHEN CAST(started_at AS TIME) >= '18:00:00' AND CAST(started_at AS TIME) <= '23:59:59' THEN 'Evening'
        ELSE 'Other'
    END
ORDER BY 
    mem_number_of_ride DESC

- -- Casual
SELECT 
    COUNT(ride_id) AS casu_number_of_ride,
    CASE 
        WHEN CAST(started_at AS TIME) >= '00:00:00' AND CAST(started_at AS TIME) < '06:00:00' THEN 'Night'
        WHEN CAST(started_at AS TIME) >= '06:00:00' AND CAST(started_at AS TIME) < '12:00:00' THEN 'Morning'
        WHEN CAST(started_at AS TIME) >= '12:00:00' AND CAST(started_at AS TIME) < '18:00:00' THEN 'Afternoon'
        WHEN CAST(started_at AS TIME) >= '18:00:00' AND CAST(started_at AS TIME) <= '23:59:59' THEN 'Evening'
        ELSE 'Other'
    END AS time_bin
FROM 
    cyclistic_yearly_total
WHERE 
    member_casual = 'casual'
GROUP BY 
    CASE 
        WHEN CAST(started_at AS TIME) >= '00:00:00' AND CAST(started_at AS TIME) < '06:00:00' THEN 'Night'
        WHEN CAST(started_at AS TIME) >= '06:00:00' AND CAST(started_at AS TIME) < '12:00:00' THEN 'Morning'
        WHEN CAST(started_at AS TIME) >= '12:00:00' AND CAST(started_at AS TIME) < '18:00:00' THEN 'Afternoon'
        WHEN CAST(started_at AS TIME) >= '18:00:00' AND CAST(started_at AS TIME) <= '23:59:59' THEN 'Evening'
        ELSE 'Other'
    END
ORDER BY 
    casu_number_of_ride DESC
```
Members mainly use the service during afternoon and morning while casual mostly use it during afternoon and evening


We want to find the most used station (start and end) for members and casual customers

Start stations :
```
SELECT COUNT(ride_id) AS Count_of_rides_member, start_station_name
FROM cyclistic_yearly_total
WHERE member_casual = 'member'
GROUP BY start_station_name
ORDER BY Count_of_rides_member DESC

SELECT COUNT(ride_id) AS Count_of_rides_casual, start_station_name
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
GROUP BY start_station_name
ORDER BY Count_of_rides_casual DESC
```
```
End stations :
SELECT COUNT(ride_id) AS Count_of_rides_member, end_station_name
FROM cyclistic_yearly_total
WHERE member_casual = 'member'
GROUP BY end_station_name
ORDER BY Count_of_rides_member DESC

SELECT COUNT(ride_id) AS Count_of_rides_casual, end_station_name
FROM cyclistic_yearly_total
WHERE member_casual = 'casual'
GROUP BY end_station_name
ORDER BY Count_of_rides_casual DESC
```
The most used station (end & start) for member is 'Kingsbury St & Kinzie St'
The most used station (end & start) for casual is 'Streeter Dr & Grand Ave'

# SHARE
In this stage, we engage stakeholders by presenting the outcomes of our analyses through intuitive visual representations. These visualizations effectively communicate the insights acquired from our SQL queries.

To present my findings, I utilized Tableau to develop an interactive dashboard. You can access the dashboard containing the results by visiting the following [link](https://public.tableau.com/app/profile/souleymane2008/viz/CapstoneProjectBikeSharing/Dashboard1)

# ACT
With the analysis we completed, we can see that both casual and member use of the service increases during summer, the busiest days for members are during the week while for casual it is the week end. Members mainly use it in morning and afternoon while casual mainly during afternoon and evening. The busiest stations are 'Kingsbury St & Kinzie St' for members and 'Streeter Dr & Grand Ave' for casuals.

## Recommendations :
In order to attract more casual riders and convert them into member riders, it is advisable to focus the marketing campaign on the summer season and specifically target the hours between 4pm to 6pm. Additionally, since casual riders tend to be more active on Saturdays, the campaign should emphasize weekend ridership. Introducing a summer membership option could be a compelling offer to entice casual riders who would typically opt for day passes.

An essential aspect of the marketing campaign should highlight the convenience of the bike-sharing system, emphasizing that bikes can be unlocked from one station and returned to any other station at any time. This information might persuade casual riders to consider an annual membership instead of one-time rides.

As member riders contribute more significantly to the company's profitability, it is recommended to incentivize them to promote the benefits of an annual membership to their friends and neighbors. For instance, providing a modest discount on membership fees for member riders who successfully refer a casual rider to join as a membe

