# Engineer Data for Predictive Modeling with BigQuery ML: Challenge Lab

## Task 1. Clean your training data
You've already completed the first step, and have created a dataset `taxirides` and imported the historical data to table, `historical_taxi_rides_raw`. This is data prior for rides to 2015.

> **Note**: You may need to wait 1-3 minutes for the data to be fully populated in your project.

To complete this task you will need to:
- Clean the data in `historical_taxi_rides_raw` and make a copy to **taxi_training_data_938** in the same dataset. You can use BigQuery, Dataprep, Dataflow, etc. to create this table and clean the data. Make sure your target column is called **fare_amount_828**.

Some helpful hints:
- You can see the source dataset in the BQ UI - familiarize yourself with the source schema first.
- As a hint for the data available at prediction time, familiarize yourself with the table `taxirides.report_prediction_data` which shows the format data will arrive at prediction time.

Data cleaning tasks:
- Ensure `trip_distance` is greater than **4**.
- Remove rows where `fare_amount` is very small (less than $**3** for example).
- Ensure that the latitudes and longitudes are reasonable for the use case.
- Ensure `passenger_count` is greater than **4**.
- Be sure to add `tolls_amount` and `fare_amount` to **fare_amount_828** as the target variable since total_amount includes tips.
- Because the source dataset is large (>1 Billion rows), sample the dataset to less than 1 Million rows.
- Only copy fields that will be used in your model (`report_prediction_data` is a good guide).

## Task 2. Create a BigQuery ML model
1. Based on the data you have in taxirides.taxi_training_data_938, build a BigQuery ML model that predicts fare_amount_828.
1. Call the model taxirides.fare_model_736.

> Note: Your model will need an RMSE of 10 or less to complete the task.

Some helpful hints:
- You can encapsulate any additional data transformations in a **TRANSFORM()** clause
Keep in mind, only features in the **TRANSFORM()** clause will be passed to the model. You can use a `* EXCEPT(feature_to_leave_out)` to pass some or all of the features without explicitly calling them
- `ST_distance()` and `ST_GeogPoint()` GIS functions in BigQuery can be used to easily calculate euclidean distance (i.e. how far pickup to dropoff did the taxi travel):

```sql
ST_Distance(ST_GeogPoint(pickuplon, pickuplat),
ST_GeogPoint(dropofflon, dropofflat)) AS euclidean
```

## Task 3. Perform a batch prediction on new data
Leadership is curious to see how well your model performs over new data, in this case, all of the data they've collected in 2015. This data is in `taxirides.report_prediction_data`. Only values known at prediction time are included in the table.

- Use `ML.PREDICT` and your model to predict **fare_amount_828** and store your results in a table called `2015_fare_amount_predictions`.