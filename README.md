# Baseball Stars: Are They Worth All That $$?

## Purpose
The purpose of this project was to get some hands-on experience with the ETL (extract, transform, and load) process. We collected various data on baseball players to analyze if there's a relationship between a player's WAR (wins above replacement) and their salary. In other words, are the highest-paid players worth the money?

WAR has quickly become one of the best ways to compare players and measure a value add to a win. This stat combines and weights a wide range of stats to truly reflect a players ability to generate wins over a replacement. What makes the stat popular is how applicable it is in its “replacement player” comparison. For more information on WAR, check out: [FanGraph War Description](https://library.fangraphs.com/misc/war/)


## Summary

#### Questions to Answer

1. In 2019, did the players with the highest salaries have the highest WAR (wins above replacement)?
2. Was there any correlation between player position and WAR/salary?
3. How does age play a role in both salary and WAR?
3. Did position players or pitchers have a higher average WAR?


#### Data Sources
1. For data source one, I went to [FanGraph Leaderboard](https://www.fangraphs.com/leaders.aspx?pos=all&stats=bat&lg=all&qual=y&type=8&season=2019&month=0&season1=2019&ind=0) and exported data to CSV to pull the players stats for the 2019 season. 

1. The second data source was a web scrape from [Sportrac](https://www.spotrac.com/mlb/rankings/2019/salary/) to pull player name, salary,team, position, and age for top 100 highest-paid baseball players for 2019. Please see the 'Creating_Salaries_Table' jupyter notebook file for more information on how this data was extracted and processed.



#### Data Cleaning

For the CSV file, the first step was to turn the table into a pandas data frame. The players were then split into positions (position palyer and pitcher). For the tables, PA was dropped for pitchers and IP was dropped for position player. 

A handful of steps were done to clean up the data before loading it into the databases. For the second data source, we filtered to get the top 100 highest salary players and had to split some data into the correct columns (player and team name were being merged). We incorporated a mapping file to update the team names from abbreviations to full names (ex: 'WSH' to 'Nationals') so that it'd be able to join successfully on the first data source. For more information, please refer to the jupyter notebook files.

From there, we created sql relational tables for each of the two data sources by player name. Our sql tables are  called 'salaries', 'position_players', and 'pitchers'.



## Instructions

1. Creating Database
   - Create a database titled 'baseball_db' in pgAdmin

2. Creating the Salaries Table
   - Run 'Creating_Salaries_Table' jupyter notebook file

3. Creating the Player Position and Pitchers Tables
   - Run 'Creating_Position_and_Pitchers_Table' jupyter notebook file

4. Updating Schemas
   - Run 'schema.sql' file to update the table metadata

5. Digging in
   - The data is set up and ready to go. Feel free to use the 'example_queries.sql' file to start digging in yourself!
