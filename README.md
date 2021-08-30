# Project: Data Modeling with Postgres
## Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

I being a data engineer created a Postgres database with tables designed to optimize queries on song play analysis. I created a database schema and ETL pipeline for this analysis.

I defined fact and dimension tables for a star schema for a particular analytic focus, and wrote an ETL pipeline that transfered data from files in two local directories into these tables in Postgres using Python and SQL.

## Star Schema
Star schemas are denormalized, meaning the typical rules of normalization applied to transactional relational databases are relaxed during star-schema design and implementation. The benefits of star-schema denormalization are:
- Simpler queries 
- Simplified business reporting logic 
- Query performance gains
- Fast aggregations

## Schema for Song Play Analysis

### Fact Table
 - ##### songplays
 
| Column          | Type     |
|-----------------|----------|
| songplay_id(PK) | InT      |
| start_time      | timestamp|
| user_id         | int      |
| level           | varchar  |
| song_id         | varchar  |
| artists_id      | varchar  | 
| session_id      | int      |
| location        | varchar  |
| user_agent      | varchar  |



### Dimension Tables
 - ##### users - users in the app
 
| Column      | Type    |
|-------------|---------|
| user_id(PK) | int     |
| firstname   | varchar |
| lastname    | varchar |
| gender      | char    |
| level       | varchar |

 - ##### songs - songs in music database
 
| Column      | Type    |
|-------------|---------|
| song_id(PK) | varchar |
| title       | varchar |
| artist_id   | varchar |
| year        | int     |
| duration    | numeric |

 - ##### artists - artists in music database

| Column        | Type    |
|---------------|---------|
| artist_id(PK) | varchar |
| name          | varchar |
| location      | varchar |
| latitude      | numeric |
| longitude     | numeric |

 - ##### time - timestamps of records in songplays broken down into specific units

| Column         | Type      |
|----------------|-----------|
| start_time(PK) | timestamp |
| hour           | int       |
| day            | int       |
| week           | int       |
| month          | int       |
| year           | int       |
| weekday        | int       |

## Project Template

- `test.ipynb` displays the first few rows of each table to let you check your database.

- `create_tables.py` drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.

- `etl.ipynb` reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.

- `etl.py` reads and processes files from song_data and log_data and loads them into your tables.

- `sql_queries.py` contains all your sql queries, and is imported into the last three files above.

- `README.md` provides discussion on this project.

## Project Steps

### Create Tables
  - Run `create_tables.py` to create your database and tables.
  
### Build ETL Pipeline
  - Run `etl.py` notebook to develop ETL pipeline.
  
### Test
  - Run queries in `test.ipynb` to confirm results.
  
