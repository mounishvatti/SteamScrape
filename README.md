# Web scraping and Sentiment Analysis on Steam

### AIM 
To Build an end-to-end `machine learning` project to conduct `sentiment analysis` on Steam game reviews. 

### Here are some specific details of the project:

- The project uses Selenium to scrape reviews from the [`Steam`]() website for the game [Counter Strike 2].
- The data is cleaned and transformed using `NLTK`, including removing stop words and tokenizing the text.
- `VADER` is used to perform `sentiment analysis` on the reviews, and the results are stored in a new column called "polarity scores".
- A box plot is created to show the distribution of `polarity scores` for recommended and not recommended reviews.
- A word cloud is created to show the most common words used in the reviews.

### INTRODUCTION

This project aims to conduct `sentiment analysis` on `Steam` game reviews using an end-to-end `machine learning` pipeline. The process involves `web scraping`, `data cleaning`, exploratory data analysis (EDA), `natural language processing (NLP)`, and `sentiment analysis`. The sentiment analysis is performed using the `NLTK` library, and the results are visualized using various plots.

### Tech Stack

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Selenium](https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white) ![Safari](https://img.shields.io/badge/Safari-000000?style=for-the-badge&logo=Safari&logoColor=white)

### LIBRARIES USED

- [`Selenium`](): For web scraping Steam game reviews.
- [`Pandas`](): For data manipulation and analysis.
- [`NLTK`](): For natural language processing tasks, such as tokenization, part-of-speech tagging, and sentiment analysis.
- [`WordCloud`](): For generating word clouds from the review text.
- [`Plotly Express`]() and [`Matplotlib`](): For data visualization.
- OS: For operating system-related functionalities.

## Stepwise implementation

### 1. Web Scraping
- The code starts by importing necessary libraries and defining the game ID and URL template.
- Selenium is used to automate the web browser for navigating to the Steam game reviews page and scraping the data.

### 2. Data Cleaning
- Extracted information includes review text, review rating, review length, play hours, and date posted.
- The data is cleaned by removing unnecessary elements, converting date format, and saving it to a CSV file.

### 3. Exploratory Data Analysis (EDA)
- Conducted EDA using bar plots to visualize the count of recommendations.

### 4. NLP and Sentiment Analysis
- Text data is pre-processed by removing stopwords and tokenizing using NLTK.
- Sentiment analysis is performed using the SentimentIntensityAnalyzer from NLTK.
- Correlation between review sentiment and recommendation status is analysed.

### 5. Visualization
- Box plots are created to visualize the distribution of polarity scores for Recommended and Not Recommended reviews.
-	Word cloud is generated to visually represent the most frequent words in the cleaned review text.

### 6. Documentation and Output
-	Proper documentation is provided throughout the code.
-	Generated outputs include a CSV file containing cleaned data and visualizations like bar plots, box plots, and a word cloud image.

