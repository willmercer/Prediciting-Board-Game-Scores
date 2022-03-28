# Predicting the average user Board game rating


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
