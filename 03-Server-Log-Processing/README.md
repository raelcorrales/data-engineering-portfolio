# Server Log Processing

This project involves processing server log data to extract insights and monitor server performance. The project includes tasks such as cleaning, transforming, and analyzing log entries to identify patterns and anomalies.

## Project Overview

Server logs are essential for monitoring and understanding the performance and health of servers. This project aims to process and analyze server log data to gain valuable insights into server usage and detect any potential issues.

## Files

- **notebook.ipynb**: This Jupyter Notebook uses PySpark to process the server logs. It performs tasks such as parsing, cleaning, and analyzing the log data to extract meaningful insights.
- **pandas-log-creation.ipynb**: This Jupyter Notebook creates the `logs.parquet` file, which is used by `notebook.ipynb` for processing. It uses pandas to create the parquet file from raw log data.

## Log Data Structure

The logs are structured with the following columns:
- **datetime**: The timestamp when the log entry was created.
- **ip**: The IP address from which the request originated.
- **url**: The URL that was requested.
- **status_code**: The HTTP status code returned for the request.
- **response_time**: The time taken to respond to the request.
- **user_agent**: Information about the client's browser or device.

## Technologies Used

- **Jupyter Notebook**: For interactive data analysis and visualization.
- **Python**: The primary programming language used for log processing and analysis.
- **Pandas**: For data manipulation and creation of the parquet file.
- **PySpark**: For processing large-scale log data.

2. **Install Dependencies:**
   Ensure you have the required Python libraries installed:
   ```bash
   pip install pandas pyspark
   ```

3. **Create the Parquet File:**
   Open the `pandas-log-creation.ipynb` notebook and run the cells to create the `logs.parquet` file from the raw log data.

4. **Process the Logs:**
   Open the `notebook.ipynb` notebook and run the cells to process the `logs.parquet` file using PySpark. 

## Analysis Performed

In the `notebook.ipynb`, the following analyses are performed:
- **Number of requests per hour and day**: Calculates the number of requests per hour and day.
- **Top 5 most visited URLs**: Identify the five most visited URLs in the logs.
- **Number of 4xx and 5xx errors**: Counts the number of 4xx and 5xx HTTP errors.
- **Average response time per URL**: Calculates the average response time for each URL.
- **Optimize DataFrame using Repartition**: Optimize the DataFrame using Spark's repartitioning feature.
- **Create Temporal View**: Create a temporary view to run queries in Spark SQL.
- **Using Spark SQL to get views of URLs**: Use Spark SQL to get detailed views of URLs.

## Output

The project generates various visualizations and reports that provide insights into server performance and usage patterns. These outputs can help in monitoring server health and identifying potential issues early.
