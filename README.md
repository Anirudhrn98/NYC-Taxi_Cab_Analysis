# NYC-Taxi_Cab_Analysis
This repository is a collection of the code use to analyse and extract information from the following NYC taxiCab dataset. The project utilizes 3 out of the 4 data files 
from the following link:
https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data?resource=download&select=yellow_tripdata_2016-01.csv

These files include: 
`yellow_tripdata_2016-01.csv`
`yellow_tripdata_2016-02.csv`
`yellow_tripdata_2016-03.csv`

The file `yellow_tripdata_2015-01.csv` was discarded and is not utilized in this project since
we are only loading our database with taxi trip data from 2016.


STEP 1: Make sure file paths in `cctables.sql` are accurate for each data file.
	
	`yellow_tripdata_2016-01.csv`
	`yellow_tripdata_2016-02.csv`
	`yellow_tripdata_2016-03.csv`
	
STEP 2: To load the database and execute queries, run the loader script in terminal with:

    `python loader.py`

** Specify the file paths on your local system to the following sql files in `loader.py`: **
	`cctables.sql`
	`updtables.sql`

These are the files to be aware of:

	`preprocess.py` -- Renames the headers of each .csv so that they correctly correspond to the MongoDB schema established in the writeup.
	`mongo.py` -- Loads our MongoDB database with the appropriate data and creates the Trips collection.
	`psql_queries.py` -- Contains all five queries written for this phase
	`run_sql.py` -- Script that connects to our Postgres database and runs each query (reports timings via terminal)
	`data_cleaning.sql` -- Sql file that perform all the data cleaning on the database. 
  	`itemset.py` -- Script that performs itemset mining to find out relation between pickup coordinates and drop off coordinates. 


STEP 1: Make sure file paths in `preprocess.py` and `mongo.py` are accurate for each data file.
	
	`yellow_tripdata_2016-01.csv`
	`yellow_tripdata_2016-02.csv`
	`yellow_tripdata_2016-03.csv`
	
STEP 2: To load the MongoDB database, run the loader script in terminal with:

    `python mongo.py`
    

NOTE BEFORE STEP 3 MAKE SURE TO:

	Install earthdistance module for PostgreSQL since it is utilized in our second query.
	This can be done by executing the following SQL on your existing PostgreSQL db:
		
		`CREATE EXTENSION cube`
		`CREATE EXTENSION earthdistance`
		
	These must be executed in this order with `cube` being created first.
	
STEP 3: To execute all five sql queries, `run_sql.py` with:

	`python run_sql.py`

STEP 4: Data Cleaning 
      Run `data_cleaning.sql` file to perform all the data cleaning on the database.

STEP 5: Itemset Mining 
    Run `itemset.py` to create coordinates table and then perform itemset mining on the table.
Code will printout the information from the last level of the lattice. 

	
Libraries used:
`time`
`pymongo`
`pandas`
