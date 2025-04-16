# Sentiment-Analysis-of-Nigeria-s-Economic-News-2021-Present-
This research project aims to extract and analyze articles tagged under **BDLead** from **BusinessDay Nigeria’s website**. The main goal is to perform sentiment analysis on editorial content, focusing on economic narratives in Nigeria from **2021 to present**. The project involves scraping article titles and links across **812 pages**, extracting article content, and storing the data for further sentiment and textual analysis.


## Project Objectives & Methodology
- Identifying the structure of the target webpage
- Extracting article links from multiple pages
- Scrape news articles tagged with economic relevance from a specified data source.
- Accessing each article to retrieve full text
- Clean and preprocess the text data for effective sentiment analysis.
- Classify the sentiment of each article as positive, negative, or neutral.
- Storing data in structured format (DataFrame)
- Assign polarity scores to quantify emotional tone.
- Performing sentiment analysis




## Key Tasks
Data Collection – Web scrape articles across all pages of the target source.

Text Preprocessing – Perform tokenization, remove noise (punctuation, stop words), and apply lemmatization.

Sentiment Analysis – Analyze sentiment and compute polarity scores.

## Tools and Libraries Used

| Tool / Library   | Purpose                                                   |
|------------------|-----------------------------------------------------------|
| Selenium         | Automated web browsing and dynamic page loading           |
| BeautifulSoup    | Parsing and navigating HTML structure                     |
| requests         | Sending HTTP requests (not actively used in current version) |
| pandas           | Storing and processing tabular data                       |
| time             | Adding delays between requests to avoid rate limiting     |
| re               | Regular expressions for text cleanup                      |
| IPython.display  | Output handling for Jupyter                               |
| tqdm             | Progress bar for loops (planned improvement)              |

## Process and Implementation
**1. Setting Up Selenium and Web Driver**
- Selenium WebDriver was used to load dynamic content.

- ChromeDriver was configured with appropriate options (--headless, --disable-gpu) to run without UI.

- Website pagination was handled dynamically by incrementing the page number in the URL.

**2. Scraping Article Links**
- For each of the 812 pages, Selenium loaded the page, and **BeautifulSoup** parsed the page source.

- Specific div elements containing article titles and links were selected using class selectors like td_module_10.

- Each article's title and link were extracted and appended to a list of dictionaries.

**3. Article Content Extraction**
- After gathering article URLs, each page was accessed.

- Main text content was scraped from the **div** with class **td-post-content tagdiv-type**.

- Regular expressions were used to remove excess whitespace and newline characters.

**4. Data Storage**
- The collected data was stored in a pandas DataFrame with columns:

  - Title
  - Author
  - Pblication Date
  - Article Excerpt
  - url
  - Content

- DataFrame was later exported to a .csv file for further analysis (sentiment, NLP, etc.).

## Research Summary & Key Findings
### Sentiment Analysis Report on BusinessDay 'BDLead' Articles (2021–2024)
**Sentiment Classification Used**
I employed the VADER SentimentIntensityAnalyzer, which is well-suited for social media and news data. I classified sentiment based on the **compound** score into:

- Positive (compound ≥ 0.05)

- Neutral (−0.05 < compound < 0.05)

- Negative (compound ≤ −0.05)
