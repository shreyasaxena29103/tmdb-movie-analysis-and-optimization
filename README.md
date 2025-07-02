# tmdb-movie-analysis-and-optimization
This project explores the TMDB movie dataset (1M+ records) using PySpark and Spark SQL in Databricks. It focuses on performance optimization and analysis

## Tools & Tech
- PySpark, Spark SQL
- Databricks (Community Edition)
- Parquet (for optimized storage)

##  Dataset
- Source: [TMDB Kaggle Dataset](https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies)
- Records: 1.2 million (after cleaning)
- Format: CSV (optimized to Parquet)

##  Data Cleaning Summary

- Dropped irrelevent columns for analysis
- Dropped columns with few null values
- Trimmed all string columns using 'trim()'
- Dropped all duplicate rows 
- Removed special characters, emojis, and noise from 'original_title' column
- Filled null 'genres' with 'Unknown'
- Split and exploded multi-genre values into individual rows for granular analysis
- Saved cleaned dataset to Parquet: 'movies_parquet

- ## Optimization Techniques Used

-  Explicitly defined schema for faster load and fewer type inference issues
-  Performed data cleaning before analysis to reduce transformation cost
-  Cached the cleaned DataFrame for reuse in multiple queries
-  Converted CSV to Parquet format (compressed & columnar)
-  Created a reusable SQL table from the Parquet file for faster quering 
-  Used ".select()" to avoid unnecessary column reads
-  No partitioning applied to avoid over-partitioning due to high genre overlap

##  Analysis Highlights
### Top Titles 
- movies with highest vote count and revenue
- Top genres
### Language & Popularity
- Most used languages
- Most popular movie per genre
### Budget vs. Runtime
- Explored correlation between budget and runtime
- Identified most expensive movies in English
- Average budget per genre

