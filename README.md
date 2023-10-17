# DATA512 HW2
# Considering bias in data

## Goal
This project aims to explore the concept of bias in data using Wikipedia articles, specifically articles about cities in different US states. We'll combine datasets containing Wikipedia articles, and state populations, and utilize the ORES machine learning service to estimate the quality of these articles.

## Data Source and License
This project utilizes data from various sources under different licenses:

1. **Wikipedia Articles**: We access Wikipedia articles through the MediaWiki REST API.
2. **US Census Data**: Population data for US states is sourced from the US Census Bureau.
3. **Regional Division Data**: The regional divisions within the US are defined by the US Census Bureau.
4. Some code examples were developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.0 - August 15, 2023   

## Data Sources
[US Cities Wikipedia Dataset](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv)  
[US Census Bureau Population Data](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html)  
[US Census Bureau Regional Division Data](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv)  

## API Documentation
[MediaWiki REST API](https://www.mediawiki.org/wiki/API:Main_page)  
[ORES API](https://ores.wikimedia.org/docs)  
[LiftWing Documentation](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing/Usage)  

## Hard-Coded Variables  
Before running this code, you need to adjust the following variables:  
- `ACCESS_TOKEN`: You must obtain a Wikimedia Access Token as described in the documentation.  
- `Data Mounting`: This notebook was executed in Google Colab, and the data was obtained from [this](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv?usp=sharing) Google Drive folder and mounted into the notebook as per the code.

## Data Processing   
The code performs the following data processing steps:  
1. Accesses Wikipedia page information using the MediaWiki REST API.
   
3. Retrieves quality scores for Wikipedia articles using the ORES API.
   a. There are articles in which we were unable to extract quality scores. These have been saved and listed within the notebook.
    
5. Combines datasets and standardizes data.
   
7. Conducts data analysis to calculate articles per capita and high-quality articles per capita.
   
9. Results from the analysis showcasing the following answers:   
   a. Top 10 US states by coverage: The 10 US states with the highest total articles per capita (in descending order)   
   b. Bottom 10 US states by coverage: The 10 US states with the lowest total articles per capita (in ascending order)    
   c. Top 10 US states by high quality: The 10 US states with the highest high quality articles per capita (in descending order)   
   d. Bottom 10 US states by high quality: The 10 US states with the lowest high quality articles per capita (in ascending order)   
   e. Census divisions by total coverage: A rank ordered list of US census divisions (in descending order) by total articles per capita   
   f. Census divisions by high quality coverage: Rank ordered list of US census divisions (in descending order) by high quality articles per capita   


## Data Files  
`article_1.csv`: Contains Wikipedia article data.  
`quality_1.csv`: Contains quality scores for articles.  
`wp_scored_city_articles_by_state.csv`: Merged dataset with state, regional division, population, article title, revision ID, and article quality.  
Output files based on analysis results.  

## Known Issues and Special Considerations  
Authentication: Ensure that you have obtained the required access token for the Wikimedia APIs.  
Data Quality: Be aware that Wikipedia data can vary in quality, and the quality scores are estimations.  
API Throttling: Take into consideration API throttling and latency when making requests.  

## Research Implications   
Your README should include a section header called “Research Implications” after which you will include your write-up paragraphs. One of your paragraphs should reflect on what you have learned, what you found, what (if anything) surprised you about your findings, and/or what theories you have about why any biases might exist (if you find they exist). In addition to any reflections you want to share about the process of the assignment, also, please respond (briefly) to at least three of the questions below:  
What biases did you expect to find in the data (before you started working with it), and why?  
What (potential) sources of bias did you discover in the course of your data processing and analysis?  
What might your results suggest about (English) Wikipedia as a data source?  
Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data?  
Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might still be appropriate and useful, despite its inherent limitations and biases?  
How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?  

