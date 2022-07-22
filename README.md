# NFL-Gambling-2.0

## Overview
----------------------------------------------------------------------------------------------------------------------------------
   Papa Needs a New Stereo was founded to help avid gamblers be successful, by creating a statistical model that predicts the outcome of sporting events based on past data. Kappa Alpha Order, a fraternity at Birmingham Southern College, reached out to our company and requested we pruduce a model to predict the winner of NFL matches for this upcoming season. More specifically, the goal of this data analysis is to determine if the favored team will win the game. We used a data set found on Kaggle with information on every NFL game from 1966 to present day. This dataset contains gambling info such as the spread, the favored team, and the outcome; as well as conditional data such as the temperature and wind speed during the game. Overall, we used 10,484 NFL games out of the 13,232 games originally in the data set. These losses are a result of pesky nulls and the dropping of NFL games from 1966-1978 due to a complete lack of gambling information. We do not consider this to be a huge loss as football is a SIGNIFICANTLY different sport than it was in 1966. The methods we used to clean our data and create our models were removing irrelevant data, and handling missing data, a train-test-split, a DecisionTree Model, a Logistic Regression Model, and a Bayesian Model. Our work showed that a DecisionTree Model reaped the best results with a 68% prediction accuracy score. 
   
## Business Understanding 
----------------------------------------------------------------------------------------------------------------------------------
    The Kappa Alpha Order Fraternity wants a statistical model that predicts the outcome of NFL games. By providing the fraternity with this model, we will be compensated with 10% of their overall winnings, if there are winnings. There is no financial risk on our end in this parntership. If the fraternity loses money, we lose nothing. If they win money, we make money. Overall, the only thing at stake for us is our reputation going forward. If the Kappa Alpha Order is overall successful in their bets, more clients will sign up to use our model. If they lose overall, it may be hard to find new clients.  
    
    
## Data Understanding
----------------------------------------------------------------------------------------------------------------------------------
The data that we are using came from a database put on Kaggle. The data relates to our analysis question because it provides gamling and conditional information on every possible dataset you could examine (Every football game since 1979). The main target variable is if the team favored to win the game actually won the game. Other variables in the dataset are schedule_date(Date of the game), schedule_week(What # week is it in the season), weather_humidity(The hunmidity level during the game),  weather_detail(Did the game take place within a dome), schedule_season(Year season took place), schedule_playoff(Was it a playoff game or not), team_home (Name of the Home Team), score_home (Final score of Home Team), score_away(Final score of Away Team) team_away(Name of the away Team), team_favorite_id (Name of the team favored to win), spread_favorite(the amount of points the favored team is expected to win by), over_under_line(How many points are expected to be scored in the entire game), stadium(Name of the Stadium the match takes place in), stadium_neutral(Is the match at a neutral site), weather_temperature(What was the temperature in the arena during the match), weather_wind_mph (the windspeed during the game), favorite_wins (Did the favored team win the game), month(The numeric month the match took place). We cleaned up the data by removing pesky nulls, filling nulls, and removing games that took place before 1979, as these games lacked gambling data.

What variables were kept?
schedule_season	schedule_playoff
team_home
score_home
score_away
team_away
team_favorite_id
spread_favorite
over_under_line
stadium	stadium_neutral
weather_temperature
weather_wind_mph
favorite_wins


Were there variables you dropped or created?
favorite_wins - Our main target, created by comparing the home score to the away score and which team was favored to win. 
schedule_date - We changed this just to the month 
month - We broke the date down to just the numeric month. As the weather changes through the season, so do teams chances of winning. 
weather_detail - 11,000 Nulls
schedule_week - We did not consider this significant so we eliminated the noise.


-How did you address missing values or outliers?

We were able to save all of the data points with missing values in weather_temperature and weather_wind_mph by changing the nulls to the mean of the temperature and windspeed at each stadium. We thought it appropiate to drop weather_detail entirely as it had over 11,000 nulls. We also dropped <100 data points to rid our dataset of some unique values(Superbowl). Lastly, we removed all games that took place before 1979 because they did not have gambling data to asses. 


-Why are these choices appropriate given the data and the business problem?

It was appropiate to keep temperature and wind speed for our model because weather is a contributing factor in the outcome of games. We thought it appropiate to drop weather_detail entirely as it had over 11,000 nulls. We dropped the superbowl matches as these events are outliers. And we felt it neccessary to drop all games before 1979, as we do not believe games without gambling data can help us to create a gambling model. 

-How much of the data have we dropped?

-Overall, after the cleaning process we were left with 10,484 NFL games out of the 13,232 games. We dropped 2,748 games.

## Modeling
----------------------------------------------------------------------------------------------------------------------------------
Describe and justify the process for analyzing or modeling the data.

First, we conducted a baseless model to see how often favored team actually won the game. The Baseless model had an accuracy score of 66%. Then, we analyzed the data by looking at the relationship between our data and if the favored team won the game in order to create a model that would attempt to predict this in the future. We tried three different types of models: A DecisionTree, a Logistic Regression, and a Bayesian. Lastly, we performed a GridSearch to identify the best hyperparameters for a model. Overall, the Decision Tree model with "random_state = 42" and "max_depth=10" hyperparamaters proved the most accurate at 68%. 

## Interpretation
Our Decision Tree Model had a 68% accuracy score. The accuracy score was the most important measurement for us as both a true positive and a true negative can be used to place a bet. If the model says the favored team will win, then vote for them to win. If the model says the favored team will lose, then vote on the underdog team. We seem to be overfitting and adjusted the hyperperameter "random_state = 42" and "max_depth=10" in an attempt to help this problem. 

## Conclusion
----------------------------------------------------------------------------------------------------------------------------------
We have created a decision tree model that is probably still overfitted with an accuracy score of 68%. While we don't condone the illegal gambling of minors in the state of Alabama, we do encourage those who make the personal choice to gamble illegally to use our model. It's just the smart thing to do. If we were to continue with this project, the next steps we would take would center around grabbing more data and adding to our current dataset. For example, adding the power rankings to the data set could be extremely valuable. #1 vs #2 is expected to be a much closer game than #1 vs #32. We would also look into adding the specific offensive and defensive systems each team uses. There are many different styles and each style does better against some techniques than it does others. Ultimatley, our goal would be to continue improving our model until we reached an accuracy score of +75%. A model that accurate would be worth a lot of money. 
