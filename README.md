# Tweets Sentimental Analysis

## sentiment_analysis_ using_ VADER

The provided code performs sentiment analysis on a given dataset of tweets using the VADER (Valence Aware Dictionary and sEntiment Reasoner) sentiment analysis tool. It calculates the polarity, positive, negative, and neutral scores for each tweet and displays the results in a table format. The code also generates a pie chart to visualize the distribution of sentiments (positive, negative, and neutral) in the dataset. This code can be used as a starting point for analyzing sentiment in textual data.


#### To run the code described in the previous response, you will need to follow these steps

1. Install the necessary dependencies: Ensure that you have installed the required modules such as pandas, numpy, nltk, and matplotlib. You can use pip, the package installer for Python, to install them. For example:
   ```
   pip install pandas numpy nltk matplotlib
   ```

2. Import the required modules: At the beginning of your script or notebook, include the import statements for the necessary modules:
   ```python
   import pandas as pd
   import numpy as np
   import nltk
   import matplotlib.pyplot as plt
   from nltk.sentiment import SentimentIntensityAnalyzer
   ```

3. Load your dataset: Assuming you have a dataset of tweets stored in a DataFrame named `df`, make sure to have it loaded or read from a file before applying sentiment analysis.

4. Perform sentiment analysis: Use the VADER sentiment analyzer from NLTK to calculate sentiment scores for each tweet in the DataFrame. Here's the code snippet:
   ```python
   sia = SentimentIntensityAnalyzer()
   df['polarity'] = df['Tweet'].apply(lambda x: sia.polarity_scores(x)['compound'])
   df['positive'] = df['Tweet'].apply(lambda x: sia.polarity_scores(x)['pos'])
   df['negative'] = df['Tweet'].apply(lambda x: sia.polarity_scores(x)['neg'])
   df['neutral'] = df['Tweet'].apply(lambda x: sia.polarity_scores(x)['neu'])
   ```

5. Display the result table: Create a new DataFrame containing the calculated sentiment scores and select the desired columns to display. Use the following code snippet:
   ```python
   result_df = df[['polarity', 'positive', 'negative', 'neutral']]
   print(result_df)
   ```

6. Visualize the sentiment distribution: Calculate the count of each sentiment category (positive, negative, neutral) based on the polarity scores. Then, create a pie chart to visualize the distribution. Here's the code:
   ```python
   sentiments = ['positive', 'negative', 'neutral']
   counts = [
       len(result_df[result_df['polarity'] > 0]),
       len(result_df[result_df['polarity'] < 0]),
       len(result_df[result_df['polarity'] == 0])
   ]

   plt.pie(counts, labels=sentiments, autopct='%1.1f%%')
   plt.title('Sentiment Analysis')
   plt.show()
   ```

7. Run the code: Once you have the dataset loaded and the code implemented, execute the script or notebook cell to see the results. Make sure that you have provided the correct path to the dataset or modify the code accordingly if needed.

By following these steps, you can run the code and perform sentiment analysis on your tweet dataset, visualizing the sentiment distribution using a pie chart.