# Analyzing Electric Vehicle Charging Habits
As electronic vehicles (EVs) become more popular, there is an increasing need for access to charging stations.
In this introductory project, you will use a dataset containing information on station usage to help apartment building managers better understand their tenants’ EV charging habits.

## Project Instructions
Write three SQL queries to answer the following questions:

1. Find the number of unique individuals that use each garage’s shared charging stations. The output should contain two columns: **garage_id** and **num_unique_users**. Sort your results by the number of unique users from highest to lowest. Save the result as **unique_users_per_garage**.

1. Find the top 10 most popular charging start times (by weekday and start hour) for sessions that use shared charging stations. Your result should contain three columns: **weekdays_plugin**, **start_plugin_hour**, and a column named **num_charging_sessions** containing the number of plugins on that weekday at that hour. Sort your results from the most to the least number of sessions. Save the result as most_popular_shared_start_times.

1. Find the users whose average charging duration last longer than 10 hours when using shared charging stations. Your result should contain two columns: **user_id** and **avg_charging_duration**. Sort your result from highest to lowest average charging duration. Save the result as **long_duration_shared_users**.

Three SQL cells have been created for you in the workbook. To access the data, you will need to select data using the syntax FROM charging_sessions.
