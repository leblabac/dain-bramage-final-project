![NFL-Salary-Cap](https://user-images.githubusercontent.com/87709841/153775860-75842691-11e6-4076-999e-c8e74142175d.png)

# Topic: 
"We hear fans scream about pampered athletes all the time. They complain that players are paid exorbitant amounts and treated like rock stars. The average person has a vision of a mega-rich lifestyle with easy money, fast cars and behavior unencumbered by the norms of polite society." Indeed, the National Football League (NFL) is the most popular professional sport in America with annual league revenues of just over 15.26 billion in 2019. The League distributed $9.5 billion to its 32 teams, so each team individually brought in $296 million last year. (Kelly 2020)

Beyond the images of pampered athletes, however, is the time-honored race to **WIN** - and (owners notwithstanding) many people have a team they're invested in the winning outcome of.  Team Dain Bramage began to wonder about the relationship between money allocation and winning.

# Dain Bramage Project Team
[Laura Blabac](https://github.com/leblabac/), [Kristina Engle](https://github.com/kristina1727/), [Pam Norman](https://github.com/pnorman411), [Dan Prenevost](https://github.com/dprenevost), [Kari Suchy](https://github.com/karisuchy)

# Question(s)  
- Does the more a team spends increase their chances of making the playoffs?
- Does salary cap distribution across individual team members affect team ability to make the playoffs?

# Hypotheses   
Team Spending and Team Wins  
- H<sub>0</sub>: Amount of money spent by a team has no effect on a teams chances of making the playoffs.
- H<sub>a</sub>: There is a relationship between the amount a team spends and their chances making the playoffs.

Salary Cap Distribution and Team Wins
- H<sub>0</sub>: Salary distribution has no effect on a teams chances of making the playoffs.
- H<sub>a</sub>: There is a relationship between salary distribution and the team's chances of making the playoffs.

# Methodology 
## Analytical Tools Used 
Python 3.7, Pandas, Jupyter Notebook, scikit-learn, Tableau Public, Bootstrap v5.0

## Data Analysis and Profiling  
To familiarize ourselves with the data, Team Dain Bramage performed analysis using Excel, reviewing the source data to understand its structure, content and interrelationships. The various terms associated with NFL football financials was reviewed to ensure full meaning of the data was comprehended.

## Extract, Transform, Load  
Beginning with a collection of data that spans 11 years (2011-2021), our data included NFL financials abstracted from www.spotrac.com and NFL standings from https://github.com/nflverse/nfldata/blob/master/data/standings.csv. Pandas was primarily utilized to combine, clean, and transform the datasets into a single data frame.  Once all the financial data was combined, the data was further explored, and unnecessary columns were eliminated as they were not needed to define our original hypothesis.

- [Merge_csv.ipynb](https://github.com/leblabac/dain-bramage-final-project/blob/0a11e27920e2e7253b1c1f6483fcc3639bbf08ff/Notebooks/merge_csv.ipynb)

- [NFL Financials.ipynb](https://github.com/leblabac/dain-bramage-final-project/blob/0a11e27920e2e7253b1c1f6483fcc3639bbf08ff/Notebooks/NFL%20Financials.ipynb)

After managing the financial data, the team standings were then read into the Jupyter notebook, where the categories and columns were transformed into a standard format, renamed, combining teams that changed names/locations and dropping unneeded years’ data in order to conform to the same 11-year period as the financial data.  

- [NFL_Standings_fixed.ipynb](https://github.com/leblabac/dain-bramage-final-project/blob/0a11e27920e2e7253b1c1f6483fcc3639bbf08ff/Notebooks/NFL_Standings_fixed.ipynb)

Once both data sets were cleaned and preprocessed, they were merged using “year” and “team” to arrive at the final working data set.

- [Dataset_merge.ipynb](https://github.com/leblabac/dain-bramage-final-project/blob/0a11e27920e2e7253b1c1f6483fcc3639bbf08ff/Notebooks/Dataset_merge.ipynb)

Finally, we loaded our data into a .csv called “NFL Merged_df.csv.”

## Machine Learning  
One hot encoding is a process by which categorical variables are converted into a form that can be provided to Machine Learning (“ML”) algorithms to do a better job in prediction.  

To discover a model that could predict whether money spent by a team increased the team’s chances of winning (as defined by making the playoffs), the data was one hot encoded. Three (3) targets (or outcomes) were distinguished:  
- Playoffs
- Won_Superbowl
- Win %  

We used one hot encoding with **get_dummies** to retain as much information as possible by converting the categorical column data to numerical format, to include them in the ML model. All categorical data was dropped save for the Player Position, and one hot encoding used in our next process.

![image](https://user-images.githubusercontent.com/91210001/156938031-3395c5d9-d0a8-455c-9466-be4f512cd6c0.png) 


Moving on to testing the use of the Random Forest Predictive model, “Playoffs” became the main focus for the model.  Use of this model demonstrated a 58.8% chance of predicting which team(s) would make it to the playoff games – odds only slightly better than flipping a coin.  

![image](https://user-images.githubusercontent.com/91210001/156938193-1575793f-924c-44ed-8202-1f18e5f3b894.png)


Concluding our ML for the project, we attempted to see if the Win% data could be ratified. The data was validated using Win% in a Random Forest Regressor using mean squared error (MSE).  
![image](https://user-images.githubusercontent.com/91210001/156938277-abbc8c9d-167d-4d8d-8a38-ae1e08221523.png)

The result showed a 3.9% error rate, which the team thought acceptable given the data that was collected.  

## Visualization
### Tableau
To visualize the data retrieved from our data sources about the spending of the NFL teams, as well as salary capitation (“salary cap”) distribution among the teams, the team decided to utilize Tableau to utilize the interactivity of the program. Tableau also allows for a degree of creativity that can be used outside the parameters of the PyPlot graphs, which we were also interested in exploring.  

To this end, five (5) visualizations were created:  

#### Win Percent By Year: 
This display shows the win percent for each team over the past 10 years (2011-2021).  Logos were obtained from www.NFL.com, which were subsequently loaded into the ‘My Tableau Repository Shapes’ folder. After this, the logos were added to the “shapes card” and assigned to the appropriate team, from which point they could be used within the graph. This work allowed the ability to use the logo at the point on the graph that represents the percentage of games won by the team in the given year. To enhance the display, tooltips were applied to highlight the portion of the team salary cap that was received by an individual player. The graph is fully interactive, allowing the user to select individual teams and in addition to look at playoff or Super Bowl wins.

#### Team Capitation Spent vs Win Percent  
This graph examines the salary cap used by the team in relationship to the percentage of games won by the team for a given year. Salary capitation (or “salary cap”) is the amount that a team is allowed for player salaries for the year, as set by the NFL. For Team Dain Bramage’s analysis, the active players, those players currently on injured reserve (“Injured Reserve Cap”), and those players on the Practice Squad were included in the “Salary Cap” columns. Of note for our analysis, although “dead cap” players’ salaries *also* count against a team’s capitation, since these players were traded or released and their release data was not readily available, the team concluded that when comparing against games for the season, they should be excluded.  

The intent of the graph was to determine visually if there was any correlation between money spent by a team and percentage games won. The variation shown indicates that there is likely no correlation. Again, tooltips were applied to highlight the salary distribution for the top ten players and was created to be fully interactive.

#### Win Percent by Cap Hit  
This display provides another look at the team’s win percentage over a ten-year period, but with the focus on examining the distribution of salary among the team’s players. The horizontal axis shows the percentage of games won, while the vertical axis shows the amount in dollars that an individual received for that year. To show the variables of salary percent received, win percent and year, the game year was added to the color marks card. A tooltip calls out the player, their position, team and the percent of the salary cap that player received, along with the actual salary. Also interactive, while the initial filter was set to an individual team, the ability to compare multiple teams was added.  

#### Salary by Position  
As known by many, position on the team often influences the amount of money distributed to a player. The Salary by Position graph shows the minimum, the average, and the maximum salary for each position.  This can be reviewed across all teams, or individual teams. To create the visual, a circle and line chart were overlapped using dual axis and then subsequently synchronizing the axes. Tableaus built in calculations allowed for the calculation of the minimum, the maximum and the average salaries, sorted by max salary, but additionally interactional.  

#### Player Salary Z-Score  
To observe the variation of salary distribution based on a traditional bell curve, a z-score visualization was created to identify the number of standard deviations an individual player’s salary was in relation to the team’s average for a particular year. To accomplish this, three calculated fields were created in Tableau:  
- Average Salary &: Window_Avg(sum([Salary%]))
- STDEVP Salary %: WINDOW_STDEVP(SUM([Salary%]))
- Z-Score Salary %: (sum([Salary%]) - [Avg Salary %]) / [STDEVP Salary%]  
Like the other graphs, this was designed to be interactive by year and team, and includes tooltips that show the player’s name, position, capitation distribution and the percent of deviation away from standard.

### Bootstrap 5  




## Summary and Recommendations






## Resources

### Data Sources 
- [NFL Financial Records 2011-2024](https://www.spotrac.com/)
- [NFL NFL Standings](https://github.com/nflverse/nfldata/blob/master/data/standings.csv)

## Additional References  
- Untitled illustration of NFL logo on money background. NFL Salary Caps. Retrieved on February 13, 2022 from https://fantasydata.com/nfl-salary-cap-update-2022
