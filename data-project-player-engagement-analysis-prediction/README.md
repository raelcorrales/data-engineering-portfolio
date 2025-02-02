# Analyzing Online Gaming Behavior with ETL Pipeline

This project processes a dataset containing information about online gaming behavior to extract meaningful insights. The data undergoes cleaning, transformation, and analysis using an ETL (Extract, Transform, Load) pipeline. The processed data is stored in PostgreSQL, and clustering results are saved in MongoDB.

## Data Description

The dataset, **Online Gaming Behavior**, provides detailed information about the habits and characteristics of players, including:

- **Player Demographics**: Age, gender, location.
- **Gameplay Details**: Total playtime, average session duration, sessions per week.
- **Game Preferences**: Genre, difficulty level.
- **Achievements**: Player level, number of unlocked achievements.
- **Monetization**: Number of in-game purchases.
- **Engagement Level**: Low, Medium, or High.

The dataset consists of 40,034 rows and 13 columns. It is provided in a CSV file named `online_gaming_behavior.csv`.

## Project Instructions

This project focuses on cleaning, transforming, and analyzing the data to uncover insights about player behavior. Follow these steps to replicate the project:

### Cleaning and Transformation Steps

1. **Handle Missing Values**: Identify and handle any missing or inconsistent data.
2. **Generate Derived Metrics**:
   - Average playtime per session.
   - Sessions per month based on sessions per week.
3. **Cluster Players**:
   - Use Spark's MLlib to cluster players based on metrics like playtime, sessions, and purchases.
   - Save the clustering model and cluster assignments.
4. **Aggregate Insights**:
   - Total playtime by game genre.
   - Average engagement level by location.

### Splitting Data into Separate Outputs

The data is divided into three outputs:

- **player_demographics.csv**: Contains player demographic information.
- **gameplay_metrics.csv**: Includes derived gameplay metrics and cluster assignments.
- **aggregated_insights.csv**: Aggregates insights like total playtime and average engagement level.

## Running the ETL Pipeline

### Prerequisites

Ensure you have the following installed:
- Python 3.8+
- Docker and Docker Compose
- Required Python libraries: `pandas`, `numpy`, `pyspark`, `sqlalchemy`, `minio`, `pymongo`, `psycopg2`.

### Steps

1. **Set Up Environment**:
   - Clone the repository:
     ```bash
     git clone <REPO_URL>
     cd online-gaming-etl
     ```
   - Start the services using Docker Compose:
     ```bash
     docker-compose up
     ```

2. **Upload Dataset**:
   - Access MinIO at [http://localhost:9000](http://localhost:9000).
   - Upload the dataset `online_gaming_behavior.csv` to the `datasets` bucket.

3. **Run the Airflow DAG**:
   - Open Airflow at [http://localhost:8080](http://localhost:8080).
   - Trigger the `etl_pipeline` DAG.

4. **Query Results**:
   - Access PostgreSQL to query the cleaned and transformed data.
   - Use MongoDB to analyze the clustering results.

## Output

The ETL pipeline generates the following outputs:

1. **Cleaned and Transformed Data**:
   - Stored in PostgreSQL with structured tables for easy querying.
   - Includes new metrics like average session duration and player clusters.

2. **Clustering Model and Assignments**:
   - Saved in MongoDB for further analysis.

3. **Aggregated Insights**:
   - CSV file `aggregated_insights.csv` containing summarized metrics.

## Example SQL Queries

Here are some example queries to analyze the results:

1. **Find the most popular game genre by total playtime**:
   ```sql
   SELECT GameGenre, SUM(PlayTimeHours) AS TotalPlaytime
   FROM gameplay_metrics
   GROUP BY GameGenre
   ORDER BY TotalPlaytime DESC;
