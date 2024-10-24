# Approach to the Solution 

**Google Drive Mounting** 

The project files, including the positive and negative word dictionaries, stopword lists, input Excel file, and output file, are stored on Google Drive. To access these files, Google Drive was mounted within the environment, allowing seamless interaction between the Python code and the data. 

**Libraries and Dependencies** 

For this task, several libraries were necessary: 
 
- nltk (Natural Language Toolkit): Used for text tokenization, sentence segmentation, and accessing standard stopwords. 
- requests: Used to send HTTP requests to web pages and retrieve article content. 
- BeautifulSoup (from bs4): Used to parse HTML content from the retrieved web pages, extracting the article body and title. 
- pandas: Utilized for handling input and output Excel files efficiently, allowing for easy data manipulation. 
- re (Regular Expressions): Used for finding personal pronouns and other text patterns. 
 
Additional Requirements: Before using the functions from the nltk library, essential components like tokenization and stopwords needed to be downloaded within the environment. 

**Loading Dictionaries** 

To perform sentiment analysis, pre-compiled word lists of positive and negative words were utilized. These lists are standard in sentiment analysis and are used to identify and count occurrences of positive and negative sentiments in the text. 

**Stopwords Management** 

Stopwords are common words that do not contribute significantly to the analysis, such as 'the', 'is', 'and'. In this case, both standard English stopwords from nltk and custom stopwords lists from various domains (e.g., currencies, dates, auditor-related terms) were loaded and combined into a single set to be removed during text cleaning. 

**Text Cleaning** 

After loading the article text, it was essential to clean it by removing unnecessary characters, symbols, and stopwords. Only the words contributing to sentiment and readability analysis were retained. This step involved tokenizing the text into individual words and filtering out words that are either non-alphanumeric or present in the stopwords list. 

**Sentiment Analysis** 

The sentiment analysis involved calculating the following metrics: 
 
- Positive Score: Counts the number of positive words present in the cleaned text. 
- Negative Score: Counts the number of negative words. 
- Polarity Score: Reflects the overall sentiment, calculated as the difference between positive and negative scores, normalized by the total number of sentiment-related words. 
- Subjectivity Score: Measures how subjective or opinion-based the text is by comparing the total positive and negative words to the overall word count. 

**Readability Metrics** 

The readability analysis was aimed at understanding the complexity of the text by computing: 
 
- Average Sentence Length: The total number of words divided by the number of sentences. 
- Percentage of Complex Words: The proportion of words with more than two syllables, indicating text complexity. 
- Fog Index: A common readability formula based on sentence length and complex words, indicating the educational level needed to understand the text. 

**Word-Level Analysis** 

The word analysis focused on: 
 
- Sentence Count and Word Count: Basic metrics that help assess the structure of the text. 
- Personal Pronouns Count: Identifies the frequency of personal pronouns like 'I', 'we', 'my', etc., which can indicate a more personal tone in the writing. 
- Average Word Length: The sum of the lengths of all words divided by the total number of words. 

**Article Extraction** 

To analyze an article, the text needed to be extracted from a given URL. This was done by sending a web request to retrieve the webpage, followed by parsing the HTML structure to extract the title and body of the article. These were combined into a single text string for further processing. 

**Data Processing Workflow** 

Once all functions were in place, the input Excel file containing a list of URLs was processed. For each URL: 
 
- The article text was extracted. 
- The text was cleaned and analyzed for sentiment, readability, and word-based metrics. 
- The results were compiled into a DataFrame and, once all URLs were processed, exported as an Excel file for easy access and further analysis. 

**Requirements Management** 

To ensure the environment is properly set up for running this project, a `requirements.txt` file was generated. This file lists all necessary libraries and their versions so that they can be easily installed in a new environment. 
