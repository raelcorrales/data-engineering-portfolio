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

- **Cantidad de requests por hora y día**: Calcula la cantidad de solicitudes por cada hora y día.
- **Top 5 URLs más visitadas**: Identifica las cinco URLs más visitadas en los logs.
- **Cantidad de errores 4xx y 5xx**: Cuenta la cantidad de errores HTTP 4xx y 5xx.
- **Tiempo de respuesta promedio por URL**: Calcula el tiempo de respuesta promedio por cada URL.
- **Optimizar DataFrame usando Repartition**: Optimiza el DataFrame usando la función de repartición de Spark.
- **Crear Temporal View**: Crea una vista temporal para ejecutar consultas en Spark SQL.
- **Usando Spark SQL para obtener las vistas de las URLs**: Utiliza Spark SQL para obtener vistas detalladas de las URLs.

## Output

The project generates various visualizations and reports that provide insights into server performance and usage patterns. These outputs can help in monitoring server health and identifying potential issues early.
