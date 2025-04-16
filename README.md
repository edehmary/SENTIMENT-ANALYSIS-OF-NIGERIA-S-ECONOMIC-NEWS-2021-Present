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
| `Selenium`        | Automated web browsing and dynamic page loading           |
| `BeautifulSoup`    | Parsing and navigating HTML structure                     |
| `requests`         | Sending HTTP requests (not actively used in current version) |
| `pandas`           | Storing and processing tabular data                       |
| `time`             | Adding delays between requests to avoid rate limiting     |
| `re`               | Regular expressions for text cleanup                      |
| `IPython.display`  | Output handling for Jupyter                               |
| `tqdm`             | Progress bar for loops (planned improvement)              |

## Process and Implementation
**1. Setting Up Selenium and Web Driver**
- Selenium WebDriver was used to load dynamic content.

- ChromeDriver was configured with appropriate options (`--headless`, `--disable-gpu`) to run without UI.

- Website pagination was handled dynamically by incrementing the page number in the URL.

**2. Scraping Article Links**
- For each of the 812 pages, Selenium loaded the page, and `BeautifulSoup` parsed the page source.

- Specific `div` elements containing article titles and links were selected using class selectors like `td_module_10`.

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

- DataFrame was later exported to a `.csv` file for further analysis (sentiment, NLP, etc.).

## Research Summary & Key Findings
## Sentiment Analysis Report on BusinessDay 'BDLead' Articles (2021–2024)
**Sentiment Classification Used**
I employed the VADER SentimentIntensityAnalyzer, which is well-suited for social media and news data. I classified sentiment based on the **compound** score into:

- Positive (compound ≥ 0.05)

- Neutral (−0.05 < compound < 0.05)

- Negative (compound ≤ −0.05)

**Dataset Overview**
- **Total Articles Analyzed:** Over 1,000 articles scraped from BusinessDay’s BDLead section.

- **Date Range:** From 2021 to early 2024.

## Sentiment Analysis Summary

| Sentiment | Percentage |
|-----------|------------|
| Negative  | ~46%       |
| Neutral   | ~38%       |
| Positive  | ~16%       |

### Interpretation:
This indicates a predominantly negative sentiment tone in the BusinessDay BDLead articles, potentially reflecting economic hardship, government policy criticisms, or recurring negative news themes during the period.

## Yearly Sentiment Trends
I grouped sentiments by year and plotted a line graph of sentiment counts per year. Key takeaways include:

2021: Highest number of negative articles.

2022: Slight increase in neutral tones.

2023–2024: Gradual rise in positive sentiment, though still lower than negative/neutral.

### Interpretation:
There appears to be a slight improvement in sentiment from 2023 onward, suggesting potential economic recovery or better public communication.

### Most Frequent Words in Positive vs. Negative Articles
I applied basic text preprocessing and wordclouds for:

**- Positive Articles:** Frequent words included "growth", "investment", "increase", "development".

**- Negative Articles:** Frequent words included "debt", "inflation", "crisis", "shortage", "decline".

### Interpretation:
Negative articles focus heavily on economic instability, while positive ones emphasize progress and development plans.

## Challenges Encountered

| Challenge                  | Solution                                                        |
|----------------------------|-----------------------------------------------------------------|
|Cloudflare protection & bot detection| Applied random delays, rotated user agents, and simulated scrolling to mimic human interaction
| Dynamic Content Rendering   | Used Selenium to fully render JavaScript content before scraping |
| Pagination                 | Scripted URL generation for 812 pages                           |
| HTML Structure Changes      | Used try-except blocks to handle variations or missing elements |
| Rate Limiting / Performance | Introduced `time.sleep()` between requests and ran in headless mode |
| Long Runtime for Full Crawl | Currently crawling is partial; batching or parallel scraping is considered for future improvements |


# Conclusion
My analysis reveals that BDLead articles tend to highlight negative economic news, especially in 2021–2022. However, there's a visible uptick in positive reporting in recent years, signaling cautious optimism.
