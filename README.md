User Sentiment Analysis on Facebook

Priority Notice

For a better understanding of this project, we recommend watching the presentation video first:

Presentation Video: Watch Now

Presentation Slides: View Here

Introduction

This project aims to analyze user sentiment on Facebook by collecting and processing data from posts, comments, and reactions in groups and pages.

The project consists of three main parts:

Developing a data scraping source code.

Deploying the scraping tool on a website.

Implementing a Natural Language Processing (NLP) system for sentiment analysis.

1. Developing the Data Scraping Source Code

This project includes a source code using Selenium to scrape posts and pages.

Data Scraping Guide using Selenium

Note: This is only the source code and has not been deployed. It demonstrates how the backend functions. Storage and deployment on a web platform are handled separately.

Steps to Scrape Data

Step 1: Download Files

Download the folder "Data Scraping Source Code".

Step 2: Run the Program

Run the fanpage.ipynb or group.ipynb file, starting from the 'Login using cookies' section.

If you want to log in using your account, replace "your account" and "your password" in the code.

Adjust the number of posts to scrape in the following code section:

#------> #Select the number of posts to scrape here

Note: The generated CSV file is only for viewing the scraped content. The scraped content can also be checked in the cell output. Any printed errors are due to missing content, not a program malfunction.

2. Deploying the Scraping Tool on a Website

This project deploys an automated scraping system to a website. See the details at:

Automated Scraping System: Scraping Facebook Scheduler

Facebook Scraping Tool: Tool Scraping Facebook

3. Natural Language Processing (NLP) Sentiment Analysis System

Sentiment Analysis Model Guide Using NLP

Step 1: Load data from the root folder (train and test), where each folder contains neg and pos subfolders.

Step 2: Preprocess the data: convert to lowercase, remove numbers, special characters, extra spaces, and tokenize Vietnamese text.

Step 3: Vectorize using Sentence-BERT (distiluse-base-multilingual-cased-v1).

Step 4: Train the model and evaluate it on the test dataset.

Step 5: Save the trained model (model_save_path/sentiment_classifier.pkl).

Step 6: Preprocess and predict on new test data.

Step 7: Retrieve data from MongoDB and analyze the sentiment of comments in groups/pages.

Note: If you want to run the analysis without retraining the model, follow these steps:

Run steps 1 and 2.

Adjust the path model_save_path/sentiment_classifier.pkl in step 6.

Run step 7 to retrieve data from MongoDB and view the sentiment analysis results.

Sentiment Analysis Model Based on Post Reactions on Pages

Since posts on pages are created by page owners, analyzing them using NLP always results in positive sentiment. To assess user sentiment towards a post, we use the following formula based on reactions:

 / (TotalReactions)

Note: The Sentiment Score ranges from -1 to 1. The closer to -1, the more negative the sentiment; the closer to 1, the more positive the sentiment. A score of 0 indicates a balance between positive and negative reactions.
Additional Resources

Presentation Slides: View Here

Presentation Video: Watch Now
