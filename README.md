# Project description
As an evolution of [Project 1](https://github.com/hedcler/udacity-dataengineer-project1) now we need to respond 3 questions querying on Apache Cassandra (A NoSQL database for big-data)

**1. Get the artist, song title, and song's length in the music app history that was heard during in a giving sessionId, and itemInSession**

**2. Get only the following: name of the artist, song (sorted by itemInSession), and user (first and last name) for a giving userId, and sessionId**

**3. Get every user name (first and last) in the music app history who listened to the given song**

We have some CSV files with a large volume of events data to be used to get the response to the questions above.

## Project structure

We have a simple *Jupyter Notebook* file `Project_1B_ Project_Template.ipynb`, that run all process for **ETL** and Apache Cassandra Queries.

### Step 1 - The ETL process

The steps below are executed in order:

1. Extract all pieces of information on event files and consolidate it in a single CSV file `event_datafile_new.csv`
2. Created an Apache Cassandra keyspace and tables
3. Transform and load data to the Apache Cassandra tables

## Step 2 - Reading the data

Based on the created data structure, the queries below was executed to test and get the responses:

**QUERY 1**
Get the artist, song title, and song's length in the music app history that was heard during in a giving sessionId, and itemInSession
```
SELECT 
	artist, 
	song, 
	length 
FROM listened_songs_events 
WHERE session_id = 338 
	AND item_in_session = 4
```

**QUERY 2**
Get only the following: name of the artist, song (sorted by itemInSession), and user (first and last name) for a giving userId, and sessionId
```
SELECT 
	artist, 
	song, 
	first_name, 
	last_name 
FROM listened_songs_by_user_by_session 
WHERE session_id = 182 
	AND user_id = 10
```

**QUERY 3**
Get every user name (first and last) in the music app history who listened to the given song
```
SELECT 
	first_name, 
	last_name 
FROM users_by_songs_listened 
WHERE song = 'All Hands Against His Own'
```
