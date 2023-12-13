# BiasCheckCityWiki
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
[US Cities Wikipedia Dataset](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv)  - `us_cities_by_state_SEPT.2023.csv`  
[US Census Bureau Population Data](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html)  - `NST-EST2022-POP.xlsx`  
[US Census Bureau Regional Division Data](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv)  - `US States by Region - US Census Bureau.xlsx`  
These have also been saved in the `data` folder of this repository with their corresponding names above.  

## API Documentation
[MediaWiki REST API](https://www.mediawiki.org/wiki/API:Main_page)  
[ORES API](https://ores.wikimedia.org/docs)  
[LiftWing Documentation](https://wikitech.wikimedia.org/wiki/Machine_Learning/LiftWing/Usage)  

## Hard-Coded Variables  
Before running this code, you need to adjust the following variables:  
- `ACCESS_TOKEN`: You must obtain a Wikimedia Access Token as described in the documentation.  
- `Data Mounting`: This notebook was executed in Google Colab, and the data was obtained from [this](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv?usp=sharing) Google Drive folder and mounted into the notebook as per the code.

## Data Processing   
The code has been saved in the folder `src` in the notebook `data_512_homework_2.ipynb`. This notebook follows these following two phases:  
1. We will delve into the process of accessing page information data from the English Wikipedia through the MediaWiki REST API. Our aim is to obtain **concise page info data summaries for a variety of article pages.**  

2. The next phase is where we leverage the **LiftWing ML Service API** to obtain **ORES scores** . By utilizing the LiftWing version of ORES, we can generate estimations of article quality for any changes made to articles.  
   
In more detail, the code performs the following data processing steps:  
1. **Accesses Wikipedia page information using the MediaWiki REST API.**  
   
3. **Retrieves quality scores for Wikipedia articles using the ORES API.**      
   a. There are articles in which we were unable to extract quality scores. These have been saved and listed within the notebook.
    
5. **Combines datasets and standardizes data.**   
   
7. **Conducts data analysis to calculate total-articles-per-population (a ratio representing the number of articles per person)  and high-quality-articles-per-population (a ratio representing the number of high-quality articles per person) on a state-by-state and divisional basis.**   
   
9. **Results from the analysis showcasing the following answers:**     
   a. Top 10 US states by coverage: The 10 US states with the highest total articles per capita (in descending order) - `analysis_1.csv`    
   b. Bottom 10 US states by coverage: The 10 US states with the lowest total articles per capita (in ascending order) - `analysis_2.csv`         
   c. Top 10 US states by high quality: The 10 US states with the highest high quality articles per capita (in descending order) - `analysis_3.csv`         
   d. Bottom 10 US states by high quality: The 10 US states with the lowest high quality articles per capita (in ascending order) - `analysis_4.csv`         
   e. Census divisions by total coverage: A rank ordered list of US census divisions (in descending order) by total articles per capita - `analysis_5.csv`       
   f. Census divisions by high quality coverage: Rank ordered list of US census divisions (in descending order) by high quality articles per capita - `analysis_6.csv`    
These results have been saved as csv's with their corresponding names above in the `results` folder of this repo.  


## Data Output Files  
`article_1.csv`: Contains Wikipedia article data. Saved in `data` folder.  
`quality_1.csv`: Contains quality scores for articles.  Saved in `data` folder.  
`wp_scored_city_articles_by_state.csv`: Merged dataset with state, regional division, population, article title, revision ID, and article quality.  Along with being uploaded to [Google Drive](https://drive.google.com/drive/folders/1qzJcMILGuf_GjvfjwXizN5B8T9VUGhLv?usp=drive_link), these have also been saved in `data` folder.  


## Known Issues and Special Considerations  
Authentication: Ensure that you have obtained the required access token for the Wikimedia APIs. Instructions on how to do so are provided in the code.    

## Research Implications   
### What biases did you expect to find in the data (before you started working with it), and why? 
Wikipedia editors are a key driving force behind the content on the platform. However, this editorial function brings with it the potential for biases, influenced by the interests, expertise, and potential personal biases of these editors. This aspect of bias can even extend to what are considered "high-quality" articles. Since the assessment of article quality is inherently **subjective**, topics and viewpoints that resonate more with the preferences of Wikipedia editors may receive higher ratings. I thought that since this assignment entailed working with Wikipedia data for research, there would be a lot of this **editorial bias**.   

I also noticed that Wikipedia is avaliable in multiple languages, and thus some kind of **language bias** may creep in. I expected that articles in widely spoken languages, such as English or Spanish, would have more comprehensive coverage compared to articles in less common languages. This bias could affect the representation of information from different regions of the world.

### What (potential) sources of bias did you discover in the course of your data processing and analysis?  
I definitely found it surprising to see that the Pacific Division had the fewest articles per capita. On the other hand, this region may have fewer towns than its population, which would explain the lower density of articles.

### What might your results suggest about (English) Wikipedia as a data source?  
I saw that Nebraska and Connecticut had no scraped content, which, in my opinion, points to possible issues with data completeness. Researchers like myself need to be ready for the possibility of data gaps and abnormalities while utilizing Wikipedia as a data source. They should investigate solutions for these problems, which can entail creating unique scraping algorithms made to fill in these gaps or applying statistical approaches to impute values into missing data.  

### How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?  
I definitely see scope to enhance the Wikipedia dataset by integrating external data sources, including census records, academic publications, and government documents. This integration serves to offer supplementary context and validation, effectively mitigating biases inherent in Wikipedia's content - and this data is also public. In order to account for data volatility, I also advise normalizing the data depending on regional parameters, such as population density or region-specific features.


