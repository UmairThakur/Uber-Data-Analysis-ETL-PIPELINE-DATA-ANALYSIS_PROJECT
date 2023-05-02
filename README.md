# Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT
Hello Everyone, excited to share my Uber Data Analysis Project, an End-to-End Data Engineering Project from creating data pipelines to finally creating the dashboard. 

## Step 1: Creating a Process Flow
## Step 2: Data Modeling and creating an ER Diagram to get a better understanding of the data
## Step 3: Writing the Transformation code in Python
## Step 4: Create a project and a bucket on the Google Cloud Platform, upload the data, select the server and set the appropriate permissions.
## Step 5: Create a Virtual Machine Instance in GCP using GCP Compute Engine.
## Step 6: Connect the VM to Mage Project using SSH Linux Terminal and create a mage project (also download the necessary dependencies).
## Step 7: Create a data pipeline using Mage Blocks like data loader, transformer, and exporters. Add your transformation code to the data transformer with the necessary changes.
## Step 8: Once, the pipeline is ready, add GCP credentials credentials to the configuration 'io_config.yaml' file. You can easily get the credentials from the APIs and Services tab from Google Console.
## Step 9: Using BigQuery to query the data, perform ETL operations so that data can be used for Data Analysis like creating dashboards, reporting, etc. 
## Step 10: Finally, create a dashboard using any dashboarding/reporting software, I used Looker Studio but we can also use other tools like Power BI, Tableau, Qlik, etc.
## Final Dashboard: https://lookerstudio.google.com/s/nQI06ax2wMY

SQL Query Solution:

-- top 10 pickup locations based on number of trips
SELECT pickup_location_id, COUNT(trip_id) as No_of_Trips
FROM uber_dataset.fact_table
GROUP BY pickup_location_id
ORDER BY No_of_Trips DESC
LIMIT 10;

-- total number of trips by passenger count
SELECT passenger_count, COUNT(passenger_count) AS No_of_Trips
FROM uber-big-data-analysis.uber_dataset.passenger_count_dim 
GROUP BY passenger_count;

-- Average fare amount by hour of the day
SELECT d.pick_hour, AVG(f.fare_amount) AS Avg_Fare_Amt 
FROM uber-big-data-analysis.uber_dataset.datetime_dim d
JOIN uber-big-data-analysis.uber_dataset.fact_table f
ON d.datetime_id=f.datetime_id
GROUP BY d.pick_hour
ORDER BY AVG(f.fare_amount) DESC;
