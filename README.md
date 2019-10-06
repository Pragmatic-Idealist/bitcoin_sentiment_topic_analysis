# Bitcoin Sentiment and Topic Analysis Over Time

I was always interested in Bitcoin as an investment and its underlying technology, blockchain. From an investment perspective, Bitcoin is one of history's best performing financial assets. If you bought just $100 in Bitcoin in early 2011, you would be 2 million dollars richer when bitcoin was at its peak! 

Bitcoin is also very different from typical investments such as stocks, bonds, and commodities and many of these differences contribute to how people value it and why it has so much volatility.

**Bitcoin price is driven by two main factors:**

Unlike other financial assets such as Stocks, Bonds, or Commodities, there are no earnings reports, revenue, cost, or any many of the other traditional financial metrics to track how well an asset is doing. Only the verifiable fixed supply/scarcity and the level of social acceptance and confidence drives price.

Verifiable Fixed Supply/Scarcity -- Programmed Fixed Supplied and Blockchain technology to verify transactions.

Social Acceptance/Confidence -- Measured by Sentiment and Topics over time.

## Business Problem/Motivation
Bitcoin's largest gains happen in a very short amount of time. (Insert Tom Lee Quote). Knowing the sentiment and composition of topics being talked about in cryptosphere can help investors position themselves for large positive and negative price movements. **I decided to analyze the sentiment and topic composition over time to see if they can be used as reliable indicators of price movement.** 

## Methodology
**1. Data Collection**

I utilized an API that pulls data from various crypto news websites. The data that I gathered included the open and close prices of Bitcoin as well as the article name and text body from news articles from 2016-2018.

**2. Data Cleaning and PreProcessing**
I conducted data preprocessing for natural language processing and sentiment analysis. I lemmatized news article text, cleaned the text, created custom stop words, and then used Tfidfvectorizer to tokenize and vectorize words placing more weight on less common words.

**3. Sentiment Analysis**
I then utilized Texblob and Vader to generate sentiment scores and then averaged the two scores together for a composite score per document. I then charted Bitcoin's % Price Change and the 7 day moving average of sentiment over time.

**4.Topic Modeling**
I utilized Non-Negative Matrix Factorization (NMF) and Latent Dirichlet allocation (LDA) to generate topics from the articles. In the process, to improve the topics generated, I adjusted the stopwords and number of components in the model.

**5. Final Model**
I eventually generated 5 meaningful topics and tracked these topics and the BTC price over time to observe patterns.

## Findings


**Sentiment Analysis:**

![sentiment](sentiment.png)

The chart above shows the 7 day moving average of sentiment along side with percentage change in BTC price. As you can see many times negative movement in sentiment precedes negative percentage change in BTC price. The red circles in the chart highlights these instances. Although promising, as a standalone tool it may not be robust enough to be utilized as a indicator; however, when combined with fundamental and technical analysis it could be very helpful in making an short-term transcation.

**Topic Modeling: **

Utilizing LDA, I was able to generate 5 topics that dynamically changed over time as BTC's price changed.


| Topic Name           | Words                                   | Notes                         |
| ----------------- | --------------------------------------- | ---------------------------- |
|             |                 |  |
|               |                | |
|  |                     |      |
|   | |              |
|  ||                 |


![Best Model](finalmodel.png)

## Take Aways

There are a number of key take aways from the project I want hosts and guests to benefit from. 

If you are a host, focus on accomodating as many guests as you can comfortably fit in your space increasing the number of beds in your space. Focus on getting good reviews, cleanliness, accuracy of description, and communication are the most important components in getting a good review. Lastly, if you can give your guests a private bathroom, that will also increase the amount you can charge for your space.

If you are a guest, look for private or shared listings and be willing to venture out uptown near Harlem for better deals on spaces. If you are also willing to share a bathroom, that would also lower the price of your stay.

At the end of the day, a night's stay in the city of Manhattan during the holidays is really expensive but using these strategies can help you maximize the rent you could charge or minimize your cost of staying.

