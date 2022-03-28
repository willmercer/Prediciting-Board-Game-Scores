# Predicting the average user Board game rating

Image

Board games are an ever increasingly popular way for people to spend their free time, as they seek to get value for their money with a tangible item that has a lot of replayability. The tabletop game market was worth $11.3bn in 2020 and the Compound Annual Growth Rate up to 2026 is expected to be 9.59%.

## Goal

As an avid player of board games, I wondered if I could predict how highly a game would be scored by users by simply using ‘on the box’ factors, such as number of players and game mechanics. Not only would this information be useful to help inform me whether to buy a new game or not, but also for potential developers. The cost of transportation and production have also been steadily increasing and insights into which, if any, elements of a game contribute to a stronger audience response.

By web-scraping information found on the website, BoardGameGeek.com, I wanted to create a machine learning algorithm that would be able to accurately predict the average rating that a game would receive from all of its registered users on the website. 

## Hypothesis and Evaluation Methods

_“Using information available on the website; boardgamegeek.com, we can predict the average user rating using machine learning.”_

I used statistical evaluation methods to quantify how well this was achieved: 
- R2 Score
- Mean Squared Error
- Mean Absolute Error

## Project Approach

1. Getting the data:
- Web scraping
- Kaggle dataset

2. Cleaning and Exploratory Data Analysis (EDA):
- Removing rogue values and unnecessary columns
- Imputing values
- Understanding relationships between predictors graphically

3. Modelling and Evaluation.
- Comparing different types of models
- Tuning for the best possible score

### Getting the Data

Unfortunately the website itself would not allow text to be scraped directly with BeautifulSoup. I switched to using their own API to do this. Although this proved to be a more successful endeavour, the Category and Mechanics elements could not be extracted. 

Furthermore the BoardGameGeek server could not handle a large amount of requests at any one time, meaning that data was lost unless sleep intervals were put in place.

Ultimately in the interest of saving time, the decision was taken to use a premade Kaggle dataset. 

### Data Cleaning and Exploratory Data Analysis (EDA)

While the dataset was quite clean, further cleaning was required. Minimum age was changed to the object type, while Rating Average (the target variable) and Complexity had commas changed to periods and were both converted to be floats.

Preliminary data engineering created extra predictors which were; game age, Mechanics count and Category count.

Initial findings when examining the values of the data came up with the following:
- Oldest game is 5500 years old!
- There were some 0 minimum player games.
- There were some 0 maximum player games.
- There was a 999 Maximum player game.
- Min play time for some games was 0 mins.
- Max play time was 60000 mins.

Image

Appropriate action was taken for each finding, such as imputing average values for the maximum number of players and replacing minimum player values of 0 with 1, as a game cannot have no players!

When deciding how to deal with outliers, two datasets were produced, one where only the most extreme ones were removed, and another dataset where about half of them were removed. This was out of curiosity on my part, as I wanted to see which would produce greater scores (if at all). Only around half were removed because I wanted to maintain a relatively high number of values, to reduce overfitting and improve accuracy.

Image

The graph above describes the strength of the correlations between each predictor and the target. Perhaps surprisingly the difficulty of a game is strongly associated with the score, indicating that players enjoy harder games. Unsurprisingly the more difficult a game, the longer it takes to play. It would also seem that newer games tend to be rated more favourably, showing perhaps some recency bias. 

Image

Image

Image

An initial overview of the Categories and Mechanics revealed that despite there being 192 unique Mechanics, dice rolling and playing card usage were the most prevalent. This shows that humans have not changed their habits much in the last few thousand years! With Categories, War games and Family Games were the most popular.

A selection of regression models were used to predict the average user score, each came with its own pros and cons which have been outlined below.
- Linear Regression
  \+ Computationally quick
  
  \− Prefers linear relationships
  
- Ridge Regression
  \+ Compensates multicollinearity
  
  \− Outliers given more importance
  
 - Decision Tree
  \+ creates a pathway to an outcome
  
  \− tend to overfit on data
  
- Random Forest
  \+ reduces overfitting of decision tree
  
  \− Computationally complex and slow

Since all of these models were used on 2 data sets, a pipeline was created to streamline the process of scoring each scenario. The way this worked is outlined below.
