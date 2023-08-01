# Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT
![uber_logo_linkedin_post](https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/2f929820-68b1-4b3c-9d66-87bdc3f757bf)

Hello Everyone, I am excited to share my first complete end-to-end Data Engineering Project, Uber Data Analysis Project, from creating data pipelines to finally creating the dashboard. 

### Step 1: Creating a Process Flow
<img width="861" alt="process" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/df1b947a-7a3c-498e-8bc5-fcac182da3f4">

### Step 2: Data Modeling and creating an ER Diagram to get a better understanding of the data
![Uber Data Model](https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/629e317a-7deb-48dc-9afa-f920f89ae636)

### Step 3: Writing the Transformation code in Python
https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/4208599f-c0a2-4747-ae1b-87751a37de6f

## Step 4: Create a project and a bucket on the Google Cloud Platform, upload the data, select the server and set the appropriate permissions.
<img width="711" alt="gcp_start" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/95721865-1d94-45af-88ba-ec51c9b78d95">

Note: Project ID and Project Number are hidden.

## Step 5: Create a Virtual Machine Instance in GCP using GCP Compute Engine.

![comput_engine_logo](https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/83e73e1f-8956-4caf-8a9b-904e506fada1)
<img width="278" alt="google_compute_instance_SSH_code_b4_we_start" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/71453ee7-c6be-48ae-a605-07d2689b207d">
<img width="402" alt="converting_tables_to_dictionary_in_mage" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/b6f0f33d-ff71-4b3c-ad59-1189e1070203">

## Step 6: Connect the VM to Mage Project using SSH Linux Terminal and create a mage project (also download the necessary dependencies).
<img width="944" alt="mage_ai" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/e51a9516-c506-4d35-8c56-71bdc2edc378">

### Step 7: Create a data pipeline using Mage Blocks like data loader, transformer, and exporters. Add your transformation code to the data transformer with the necessary changes.

### Step 8: Once, the pipeline is ready, add GCP credentials credentials to the configuration 'io_config.yaml' file. You can easily get the credentials from the APIs and Services tab from Google Console.

### Step 9: Using BigQuery to query the data, perform ETL operations so that data can be used for Data Analysis like creating dashboards, reporting, etc. 
https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/7d03f9af-28c2-405c-a7ea-55dd45cffa1f

### Step 10: Finally, create a dashboard using any dashboarding/reporting software, I used Looker Studio but we can also use other tools like Power BI, Tableau, Qlik, etc.
<img width="816" alt="bttom_snap" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/02b5af9e-1684-4a96-abae-629e877038a8">

<img width="815" alt="cab_map" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/9a6656dd-8594-4fbf-b324-2a17a10e486e">

<img width="816" alt="bttom_snap" src="https://github.com/UmairThakur/Uber-Data-Analysis-ETL-PIPELINE-DATA-ANALYSIS_PROJECT/assets/81063457/db9b9fe1-859f-4179-b8eb-93f87d397e06">

## View Live Dashboard Here: https://lookerstudio.google.com/s/nQI06ax2wMY

### SQL Query Solution to the questions asked:
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
