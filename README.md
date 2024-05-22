![4](https://github.com/mounishvatti/web-scraping-and-sentiment-analysis/assets/76279858/8a958497-e0fd-4ad7-aeae-31fd87231058)

## SteamScraper Web scraping and Sentiment Analysis on Steam

> [!NOTE]
> Web scraping can be a powerful tool for extracting information from websites, but it's crucial to approach this practice with caution and adhere to ethical and legal guidelines.

Indeed, many websites explicitly mention in their `Terms of Service` that `web scraping is not allowed`. It's essential to respect these terms and adhere to ethical standards when engaging in web scraping activities. Some common reasons why websites prohibit scraping include:

1. `Server Load`: Scraping can put a strain on a website's servers, especially if done aggressively or without rate limiting. Excessive requests can slow down the website and impact the user experience for others.

2. `Protecting Intellectual Property`: Websites may want to protect their content, images, and data from being copied or used without permission. They may have invested time and resources in creating unique and valuable information.

3. `Competitive Concerns`: Websites may be concerned about competitors scraping their data for various purposes, such as price monitoring, market analysis, or content duplication.

4. `Privacy Concerns`: Websites that handle sensitive or private information may restrict scraping to protect user privacy. Unauthorized access to such data can lead to legal issues.

5. `Terms of Service Compliance`: Websites often outline specific rules in their Terms of Service regarding automated access, scraping, or data extraction. Violating these terms can result in legal consequences.

To navigate this, always check a website's `robots.txt` file and its `Terms of Service` before attempting to scrape. If scraping is prohibited, respect these rules and seek alternative ways to access the information you need, such as using public APIs when available or obtaining permission from the website owner.

Since I am not `pinging` the servers constantly at a high rate and `scraping` only a `partial amount of data` for `project purposes` related to `sentiment analysis` of `customer reviews`, there is no big deal. 

### AIM: 
To Build an end-to-end `machine learning` project to conduct `sentiment analysis` on `Steam` game reviews. 

### Here are some specific details of the project:

- The project uses Selenium to scrape reviews from the [`Steam`](https://store.steampowered.com/) website for the game [Counter Strike 2](https://www.counter-strike.net/).
- The data is cleaned and transformed using `NLTK`, including removing stop words and tokenizing the text.
- `VADER` is used to perform `sentiment analysis` on the reviews, and the results are stored in a new column called "polarity scores".
- A box plot is created to show the distribution of `polarity scores` for recommended and not recommended reviews.
- A word cloud is created to show the most common words used in the reviews.

### INTRODUCTION

This project aims to conduct `sentiment analysis` on `Steam` game reviews using an end-to-end `machine learning` pipeline. The process involves `web scraping`, `data cleaning`, exploratory data analysis (EDA), `natural language processing (NLP)`, and `sentiment analysis`. The sentiment analysis is performed using the `NLTK` library, and the results are visualized using various plots.

### Tech Stack

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Selenium](https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white) ![Safari](https://img.shields.io/badge/Safari-000000?style=for-the-badge&logo=Safari&logoColor=white)

### LIBRARIES USED

- [`Selenium`](https://www.selenium.dev/): For web scraping Steam game reviews.
- [`Pandas`](https://pandas.pydata.org/): For data manipulation and analysis.
- [`NLTK`](https://www.nltk.org/): For natural language processing tasks, such as tokenization, part-of-speech tagging, and sentiment analysis.
- [`WordCloud`](): For generating word clouds from the review text.
- [`Plotly Express`](https://plotly.com/python/plotly-express/) and [`Matplotlib`](https://matplotlib.org/): For data visualization.
- OS: For operating system-related functionalities.

![image](https://github.com/mounishvatti/SteamScrape/assets/76279858/b910beca-8c00-48c3-bf59-dff44df48e90)

## Stepwise implementation

### Getting started with Selenium
1. Install Selenium:
```bash
!pip install selenium
```
2. Install a WebDriver: You'll need to install a WebDriver for the browser you want to use.

But since Safari has a built-in webdriver, I’ll be using Safari.
```bash
!pip install webdriver-manager
```
4. Write your Python script:

Here's a basic example of a Python script that uses Selenium to scrape the title of a web page:
  
`Python`
```python
from selenium import webdriver # Create a webdriver instance
driver = webdriver.Safari() # I am using Safari

# Open the URL
driver.get("https://www.example.com")

# Get the title of the page
title = driver.title

# Print the title
print(title)

# Close the browser
driver.quit()
```
### Make Sure You Have Safari’s WebDriver

Safari and Safari Technology Preview each provide their own safaridriver executable. 
Make sure you already have the executable on your device:

Safari’s executable is located at: `/usr/bin/safaridriver`.

### Safari Technology Preview's executable is part of the application bundle’s contents.

Each safaridriver is capable of launching only the Safari version it’s associated with, and the two can run simultaneously. Although you can launch safaridriver manually by running a safaridriver executable, most Selenium libraries launch the driver automatically. See the documentation for your preferred client library to learn how to specify which browser to use.

### To manually run a safaridriver executable:
1. Navigate to `/usr/bin/safaridriver` in Finder
2. Click on it
3. A terminal window will open where you have to give your system `pwd`.
4. Done, now you have manually launched a safariwebdriver


> [!TIP]
> To use other web browsers with Selenium, you need to download the appropriate web driver for each browser. 


Here are examples for Chrome, Firefox, and Microsoft Edge:
[`Selenium documentation for different browsers`](https://www.selenium.dev/documentation/webdriver/browsers/)

### Chrome:
```python
from selenium import webdriver

# Download and install the ChromeDriver from https://sites.google.com/chromium.org/driver/
# Make sure to provide the correct path to the chromedriver executable
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')
```
### Firefox:
```python
from selenium import webdriver

# Download and install the geckodriver from https://github.com/mozilla/geckodriver/releases
# Make sure to provide the correct path to the geckodriver executable
driver = webdriver.Firefox(executable_path='/path/to/geckodriver')
```
### Microsoft Edge:
```python
from selenium import webdriver

# Download and install the Microsoft Edge WebDriver from https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/
# Make sure to provide the correct path to the MicrosoftEdgeDriver executable
driver = webdriver.Edge(executable_path='/path/to/MicrosoftEdgeDriver')
```

> [!NOTE]
> We can also use Selenium with other libraries like BeautifulSoup to parse the HTML content we scrape.

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


> [!WARNING]
> NO SSL CERTIFICATE FOUND ‼️
 
  ### To resolve the issue:

> [!TIP]
> You can pause the certificate verification temporarily, but it is not suggested for building huge resources.

  Step 1: Importing NLTK
  ```python
  import nltk
  from nltk.corpus import stopwords

  ```
  Step 2: Importing ssl and temporarliy pausing certificate verification
  Note: Not recommended if you are building any resource
  ```python
  import ssl

  try:
      _create_unverified_https_context = ssl._create_unverified_context
  except AttributeError:
      pass
  else:
      ssl._create_default_https_context = _create_unverified_https_context

  nltk.download('stopwords')
  ```
  ### For tokenizing

  ```python
  nltk.download('punkt')
  ```

  ### For tagging

  ```python
  nltk.download('averaged_perceptron_tagger')
  ```

  ### For using Vader

  ```python
  nltk.download('vader_lexicon')
  ```

### 5. Visualization
- Box plots are created to visualize the distribution of polarity scores for Recommended and Not Recommended reviews.
-	Word cloud is generated to visually represent the most frequent words in the cleaned review text.

### 6. Documentation and Output
-	Proper documentation is provided throughout the code.
-	Generated outputs include a CSV file containing cleaned data and visualizations like bar plots, box plots, and a word cloud image.

