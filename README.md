# Bitcoin Sentiment and Topic Analysis Over Time

I was always interested in Bitcoin as an investment and its underlying technology, blockchain. From an investment perspective, Bitcoin is one of history's best performing financial assets. If you bought just $100 in Bitcoin in early 2011, you would be 2 million dollars richer when bitcoin was at its peak! Bitcoin is very different from typical investments such as stocks, bonds, and commodities and many of these differences contribute to how people value it and why it has so much volatility.

## Business Problem/Motivation
This is a dual-sided problem that many New Yorkers and visitors to New York have. So I created a linear regression model that predicts the price of Manhattan Airbnb rentals and show which features of the apartment influences the price. So that hosts can maximize their return on investment on their idle space and guests find the cheapest accommodations given their needs.

## Methodology
**1. Data Collection**
I utilized Beautiful Soup and Selenium to extract Airbnb Data from Airbnb.com. The listing data included the target, price and features such as number of guests that can be accomodated, number of beds, number of bathrooms, review rating, and neighboorhood of the listing.

**2. Data Cleaning**
I conducted data cleaning of the listing data. The raw data from the listings was pretty messy, I utilized ReGex and other text cleaning techniques to standardize and clean data. After cleaning data I had to remove outliers and set proper bounds on what listings I wanted to look at. Steps I took included removing expensive listings and listings with 0 reviews. I wanted to focus on 'moderately priced' Airbnb rentals that have reviews. 

**3. Exploratory Data Analysis**
I created plots and visualizations to find relationships between features, between the features and plot. Details and charts found below. These relationships between features helped me create interaction terms between features such as total number of stars (number of review * average number of stars).

**4. Model Training and Validation**
After conducting EDA, I split of data to create a train and test set and created a base linear regression model. I ran different regressions, cross validated them with different cuts of the data, and compared the models against each other.  

**5. Testing**
I tested the best performing model: Linear Regression with Lasso Regularization

## Exploratory Data Analysis

**Price Per Night = Accomodations + Location + Listing Type + Reviews**

Removing Outliers:

![Before](pricedistoutliers.png)

The dataset has listings that had extremely high prices. One listing cost $4000 per night. Listing like these skew the distribution of the target making predictions less accurate.

![After](priceoutliersremoved.png)

After removing these outliers, the distribution is far less skewed, and the predictive power of the model increased.

**Correlation Heatmap**

![Important Features](Heatmap.png)

Diving deeper into the dataset, I created a correlation heatmap where I found that some features have strong negative and positive correlations with price.

![Important Features](importantfeatures.png)

Features such as Number of Guests, Beds, and Review ratings have the strongest positive correlation with price whereas the feature Shared Baths have strongest negative correlation with price. Other important features include neighborhood and listing space type. 


![Neighborhood](neighborhood_boxplot.png)

As you can see from this box plot, the neighborhood influences price as well. Downtown listings are far more expensive than average than uptown listings.


![Type of Listing](Listing_type_boxplot.png)

From this box plot, it shows that listings that rent out the entire space are more expensive than average than private or shared rooms.

![Type of Listing](shared_bath_boxplot.png)

In the last boxplot, shared bathrooms listings are cheaper than average than listings with private bathrooms.

![Reviews](reviews.png)

Lastly, in this heatmap cutout, Reviews are shown to be also important in determining how much a host can charge for his/her space. The most important components of Overall Review are Accuracy and Cleanliness, which contribute most to the overall review than any other component.


## Modeling

The next step is to find the model that best generalizes the relationships between the features and the target, price. After splitting the data into train and test parts, I decided to use a number of linear regression models starting from a base line Linear Regression towards more advanced models such as polynomial regressions with lasso and ridge regularization. Below is a table of the performance of each model. 


| Algorithm           | R^2                                    | Notes                         |
| ----------------- | --------------------------------------- | ---------------------------- |
| Base Linear Regression               | 0.67                    | Removed New Listings and added Engineered Features |
| Second Degree PolyReg                |  0.05                 | Overfit the test data significantly|
| Linear Regression with Lasso | 0.71                        | Performed Reasonably well       |
| Linear Regression  with Ridge  | 0.70| Performed well                   |
| Polyreg Model with Lasso  | 0.68| Performed well, however after CV, LinReg with Lasso performed better                   |
| Polyreg Model with Ridge  | 0.70| Performed well, however after CV, LinReg with Lasso performed better                   |


![Best Model](finalmodel.png)

## Take Aways

There are a number of key take aways from the project I want hosts and guests to benefit from. 

If you are a host, focus on accomodating as many guests as you can comfortably fit in your space increasing the number of beds in your space. Focus on getting good reviews, cleanliness, accuracy of description, and communication are the most important components in getting a good review. Lastly, if you can give your guests a private bathroom, that will also increase the amount you can charge for your space.

If you are a guest, look for private or shared listings and be willing to venture out uptown near Harlem for better deals on spaces. If you are also willing to share a bathroom, that would also lower the price of your stay.

At the end of the day, a night's stay in the city of Manhattan during the holidays is really expensive but using these strategies can help you maximize the rent you could charge or minimize your cost of staying.

