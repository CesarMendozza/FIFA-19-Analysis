### Context

This dataset will be familiar for those that love Soccer/Futbol and grew up playin the EA sports FiFA franchise. 

### Content

Every player featured in FiFA 19
Over 90 attributes
Player Data
Attributes based on actual data from EA’s FIFA ’19
I have engineered some attributes. 
Player personal data like age, nationality, club, wage etc… 


### Upcoming updates
Add the element of ‘Star Power’ into model
Chloropleth to show all nation represented in the dataset


### Data Source

https://github.com/jokecamp/FootballData

https://www.kaggle.com/karangadiya/fifa19

### Possible Explorations
	
Find the youngest players with the most potential
Analyze which national team or club has the best rated players
Find correlation between age and overall rating
Find correlation between age and composure
Find teams with the most 'homegrown' players

This analysis could be used for recruiting, fantasy teams, or managerial purposes. 

### Acknowledgements

Daria Czerniawko
Piyush 
Silvio Giancola

### Inspiration

I love soccer/futbol so it just came natural. I feel like I have good enough domain knowledge about the sport that my curiosity did most of the work in this project. 

### Introduction  

This project is for anyone that can find a link between data and their enthusiasm for any sport.  My sport is soccer, hence this capstone project that is helping me fulfill my curiosity of a players market value, what nation produces X position the most, what young players are out there for me to watch play, or rank the best players by their preferred foot. Using the EA sports FIFA 18 data fulfilled some of my curiosities . I was able to visualize insights and correlation between player value, wage, age, nationality etc… I was able to derive summary statistics for clubs, national teams, and players. 

Explorations Achieved using the data
World Stats
Cluster players by nationality
Predicted market value of player
Value of players with position
Variation in wages for top clubs
How many professional footballers are from each nation
The mean of all players’ overall stat
How many players are valued ≤ €30 million.


### The Data

I used a csv file provided by gaggle.  The data comes from the latest edition of FIFA 2019 which fives us ~ 90 attributes for about 15000 players from around the world. The data set has 4 major profiles (which I defined myself): Personal profile includes nationality, age, height, and weight. The Metal profile which is made up of aggression, composure, interceptions, marking, payoff, positioning, reactions, international reputation, penalties, vision. The Physical profile is made up of acceleration, agility, balance, jumping, reactions, sprint speed, stamina, strength, and body type. The Skills profile consists of ball control, crossing, curve, dribbling, finishing, free kick accuracy, heading accuracy, long passing, long shots, short passing, shot power, skill moves, sliding tackle, standing tackle, volleys, weak foot.  All of these attributes are measure from 0 to 100. These attribute are optimal indicators to determine a players market value from a particular nation or maybe we want to use a players position.

Content:






![Alt Text](Data%20Viz/Dybala.png)



### Data Cleaning and Feature Engineering

Overall this was a pretty clean data set. There were a couple of features that I dropped because they weren’t found to help me in my project. ’m all about saving time so I have found that lower casing all my columns saves me from remembering to use the shift key every time I’m filtering or what have you. There are a couple of manipulations that were needed for me to work with the dataset:
The weight attribute looked like this ‘168LBS’ I had to strip the lbs so that I could use it in my model
The Club attribute had np.nan that I replaced with N/A
The ‘body type’ attribute needed manipulation i.e Messi’s body type was Messi in the original dataset. I changed it to normal. I then one hot coded.
The work rate attribute was one hot coded. 
The  Value attribute had currency before it and K or M to symbol the entire integer: ‘€65M’. I turned that to 65,000,000.
The height attribute was formatted ‘5’8’. I turned that into inches for the purpose of my modeling. 
I created three genes where I itemized all the attributes to three genes : Mental, Physical, and skills
I also created an attribute I call ‘payoff’ which is the players overall rating - the players potential. 

### Exploratory Data analysis

Preparing the data set was fairly easy and I set myself up for the best part of the project. This is where my domain knowledge and curiosity allowed to me explore this data like it was under microscopic view. This attention to detail allowed me visualize some interesting trends.

### Geographic Distribution of players. 

I wanted to know how many players come from each of the 162 nations represented in the FIFA 19 dataset. I  was surprised to find England at the top spot, but then again the creators of the game should be ones that produce the most players. 
 




![Alt Text](Data%20Viz/cum_sum_nationality.png) 


After finding out the number of footballers by nation I wondered which nation had the highest aggregate overall. I took each players overall and added them all up to get that nations power index, I cant think of another name. I was surprised to see China PR, Japan, and Republic of Ireland in the top 20. I can think of three African nations that have better teams than these three, right off the top of my head. 






![Alt Text](Data%20Viz/nations%20power.png) 




And it was only natural for me to wonder the distribution of players by continent



![Alt Text](Data%20Viz/players_continent.png)




From there I wanted to see the homologous of a team. The way I think of this is how many native players does a club own i.e if ‘X’ player was born in L.A and plays for Atlanta United. This was pure curiosity. I didn’t use this for my model, but it does help me understand other factors to include when I work toward improving my model. I did find that three of the most heterogenous teams were Italian: Genoa, Udinese, Napoli. I have the graphs uploaded into the project if you are interested.  This part will be used for the next update of this project.


![Alt Text](Data%20Viz/Atl_Utd.png)


### Top positions from each country





![Alt Text](Data%20Viz/Bottom%20Footballers%20Value%20Distribution.png)















When we think of counties like Argentina, Brazil, and France, having the knowledge, we think of these being countries that produce some of the best players in the game now and in the past. Argentina has arguably the most iconic forwards in the game like Messi and Maradonna. Brazil has held the world cup trophy five times with names like Pele and Cafu. France has given us attackers like Thierry Henry that are backed by some strong defenders like Lilian Thuram. I looked into what positions are produced in each nation. There were some very interesting results. I wouldn’t of guessed that Center Backs (defensive players) were going to be the second highest output from Argentina. Argentina’s identity very offensive. I can also attest that for the amount of defenders Argentina is producing, the quality is subpar. Again, there are more visualizations for other nations. 



### Player rating with age

![Alt Text](Data%20Viz/Potential%20Meets%20Overall%20Rating.png)


FIFA 19 has rated all 42,000 professional footballers giving them an overall attribute and a potential attribute.  To find where potential meets overall, the data was grouped by age , the mean overall, and the mean potential. The chart above shows us four lines:
The red line shows the lefties potential rating
The blue line shows the righties potential rating
The cyan line shows us the players current overall rating for lefties
The orange line shows us the players current overall rating for righties
We can see that the potential and overall meet at age 29. We can conclude that a player is done developing at age 29. This analysis can be used to determine if you want to invest in a left/right footed youngster, it can tell you how much time you have to fully develop a player, or you can simply find a player by age so that you don’t have to teach them the basics of the game. 

### Mean Player Value vs Age


This graph visualizes the mean player value grouped by age, for all footballers, per their overall rating. The bar chart displays the data with players age on the x-axis and the y-axis displays the mean value, in Euros by the millions. 



![Alt Text](Data%20Viz/MeanVal%20by%20Age.png)


This graph is useful in visualizing the trends of valuation by age. The youngest players in our age group start at 16 all the way to 41. We see valuation climb from 16 to about 26-27, which are the ages where we can consider a player full developed(see graph #). Looking past age 27 we see valuation stat to decline for most players. Another interesting fact is that from age 20 to 21 the mean value increases by ~ €500K.  Inverse of that, the sharpest decline is seen at age ~ €800K.  I would also like to acknowledge age groups 27 and and 31. These groups disrupt the the graph because of players with high valuation like Messi and Neymar  Jr.


We can also analyze and display data of weekly wages in each age group. Using the same technique when I was looking into the valuation v. age (see above).





![Alt Text](Data%20Viz/MeanWage%20by%20Age.png)



The focus here is the weekly wages for each age group. At 16 you start with a €1000 weekly wage, which isn’t hard bad for a teen. Ages 16-19 are one big cluster of players earning about the same weekly wage. The trend grows till you hit that level of fully developed, at age 27 ( see graph above).  The largest mean gain is seen between ages 20 to 21, jumping ~ €2100.  Age group 30 is the anomaly here where the wage variance is the highest. The next age groups has players like Messi, Suarez, Rakitic, and Marcelo who are outliers in the weekly wage earnings. 


### Analysis by player position




![Alt Text](Data%20Viz/Value%20by%20Position.png)


Here we show valuation by position. We associated each player to their position versus the valuation for each player. The box plots are good to show the quartiles of the dataset while the whiskers extend to show the rest of the distribution, except for points that are determined to be “outliers” . These outliers are your superstars of the game like Eden Hazard, Phillip Coutinho, and Paulo Dybala. This graph helps both players and clubs understand valuation trends for each position. 






![Alt Text](Data%20Viz/count%20of%20players%20by%20position.png)



I also wanted to see which position has the most players and that’s what we see in the graph above. The supply of strikers and center backs and center midfielders are an abundance, which correlate to the lowest mean average valuation and wage. It’s simple economics of supply and demand. Nothing surprising there. Both 

### Analyzing the preferred foot

The righty v goofy argument exist in all sports from baseball to rugby. Soccer is no different. Do we want left footed players like Messi, Dybala, or Chiellini. How about a righty like Cristiano Ronaldo, Neymar Jr., or Eden Hazard. These are all highly skilled highly paid players. How does it look amongst top 100 footballers in the FIFA 19 dataset



![Alt Text](Data%20Viz/Top%20100%20Players%20Preferred%20Foot.png)

Violin plots are and effective and attractive way to show multiple distributions of data at once. The plot shows the preferred foot of each player grouped by age. Its starting to see that most of the 24 year olds, rated in the top 100 by value, heavily favor the goofy style. Inversely, the 33 year old group are righties, which include players like Cristiano Ronaldo and Thiago Silva.

Now looking into what the future holds

![Alt Text](Data%20Viz/Top%201000%20Players%20Preferred%20Foot.png)

The youngsters coming into the game are mainly right footers. The left footed player will become even rarer in the future generations. The beauty of a left footed defender is their unorthodox style of play, making it very hard to defend I would suspect their value would go up as well, economics 101. 

### Problem Statement
Can we predict the market value of player? What features can we use to help us use machine learning to predict that market value. In my analysis i found the features that have high correlation with the value of a player. 

![Alt Text](Data%20Viz/heatmap.png)


### Conclusion

For this project I cleaned up and deleted with the null values, merged certain tables, did a bit of feature engineering, and finally performed feature selection in order to visualize the data and perform some machine learning algorithms in attempt to predict a players market value. Using simple and complicated modeling techniques I was able to closely predict a players market value. What I found was that there was some features that I was missing. I though that the engineered features I created would help, but instead I came to discover that my model was good at predicting for players at the bottom of the list. It was opposite when looking at the top 100 players. In the top 100 is where I saw the highest variance in my residuals. I will have to find a way to include the 'Star Power' Gene in the future.


![Alt Text](Data%20Viz/pred%20value%20top.png)

![Alt Text](Data%20Viz/pred%20value%20bottom.png) 
