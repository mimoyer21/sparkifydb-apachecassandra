# Readme.md for Apache Cassandra sparkifydb ETL pipeline

## Purpose:
The purpose of this database is to create an Apache Cassandra database and provide datasets that enable answering questions about user behavior in the (fictional)
Sparkify music streaming app (especially user song listening behavior). To do so we ingest the app logs of user behavior into a newly created
Apache Cassandra db, 'sparkify_db', from where we can run queries to answer such questions.

## An explanation of the files in the repository:
* sparkify_cassandra_etl.ipynb: the Jupyter Notebook file that contains the full pipeline for cleaning the data, creating an Apache Cassandra db, and creating/populating db tables with the cleaned data
* event_data/: a directory that contains each daily event log CSV file in the form of '2018-11-01-events.csv'
* event_datafile_new.csv: (**only exists after sparkify_cassandra_etl.ipynb script is run**) contains the aggregated, cleaned data from all of the event_data files
* images/image_event_datafile_new.jpg: contains an example image of what the cleaned data in event_datafile_new.csv should look like

## How to create and populate the 'sparkify_db' Apache Cassandra database:
Simply run the sparkify_cassandra_etl.ipynb notebook. Note that the last few cells drop the tables and shut down the session, so avoid running those cells if you want the database to persist for additional analysis

## Database schema design and ETL pipeline:
We create 3 tables to answer the various types of (fictional) questions the analytics team has:
Tables:
* session_items: session_id, item_in_session, artist, song, length
* user_sessions: user_id, session_id, item_in_session, artist, song, user_name
* song_listeners: song, user_name
