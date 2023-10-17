# data-512-homework_2
Considering bias in data

## Goal
This project aims to explore the concept of bias in data using Wikipedia articles, specifically articles about cities in different US states. We'll combine datasets containing Wikipedia articles, and state populations, and utilize the ORES machine learning service to estimate the quality of these articles.

## Data Source and License
This project utilizes data from various sources under different licenses:

1. **Wikipedia Articles**: We access Wikipedia articles through the MediaWiki REST API.
2. **US Census Data**: Population data for US states is sourced from the US Census Bureau.
3. **Regional Division Data**: The regional divisions within the US are defined by the US Census Bureau.

## Data Sources
[US Cities Wikipedia Dataset
US Census Bureau Population Data
US Census Bureau Regional Division Data]([url](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv))

## API Documentation
MediaWiki REST API
ORES API
LiftWing Documentation

## Hard-Coded Variables
Before running this code, you need to adjust the following variables:

ACCESS_TOKEN: You must obtain a Wikimedia Access Token as described in the documentation.
File paths: Ensure that file paths match your working environment.

## Data Processing
The code performs the following data processing steps:

Accesses Wikipedia page information using the MediaWiki REST API.
Retrieves quality scores for Wikipedia articles using the ORES API.
Combines datasets and standardizes data.
Conducts data analysis to calculate articles per capita and high-quality articles per capita.

## Data Files
article_1.csv: Contains Wikipedia article data.
quality_1.csv: Contains quality scores for articles.
wp_scored_city_articles_by_state.csv: Merged dataset with state, regional division, population, article title, revision ID, and article quality.
Output files based on analysis results.

## Known Issues and Special Considerations
Authentication: Ensure that you have obtained the required access token for the Wikimedia APIs.
Data Quality: Be aware that Wikipedia data can vary in quality, and the quality scores are estimations.
API Throttling: Take into consideration API throttling and latency when making requests.
