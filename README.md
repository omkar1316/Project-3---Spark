# Summary of project

Startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

In order to enable Sparkify to parse and analyze their data in a distributed manner, a Spark ETL Pipeline was created, which reads the data stored inside S3.

# How to run the python scripts

To start the ETL pipeline, you have to run the following file below:

To fill tables via ETL:
```bash
python3 etl.py
```

# Files in the repository

* **[etl.py](etl.py)**: Python script to extract the needed information from Song and Log data inside the S3 buckets and parsing/inserting them to the local directory


# The database schema design and ETL pipeline.

In order to enable Sparkify to analyze their data, a Relational Database Schema was created, which can be filled with an ETL pipeline.

The so-called star scheme enables the company to view the user behaviour over several dimensions.
The fact table is used to store all user song activities that contain the category "NextSong". Using this table, the company can relate and analyze the dimensions users, songs, artists and time.

* **Fact Table**: songplays
* **Dimension Tables**: users, songs, artists and time.

# Dataset used

The data is queried from s3 buckets hosten at AWS

* **Song data**: ```s3://udacity-dend/song_data```
* **Log data**: ```s3://udacity-dend/log_data```

The first dataset is a subset of real data from the [Million Song Dataset](http://millionsongdataset.com/). Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings.