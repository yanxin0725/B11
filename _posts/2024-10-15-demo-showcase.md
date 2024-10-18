---
layout: post
title: B-11 Project Display
---
## Data Acquisition
###  Downloading Play-by-Play and Landing Data from the NHL API
When diving into a data science project involving hockey statistics, one of the key steps is obtaining accurate and comprehensive data. This guide will walk you through how to download the play-by-play and landing data for NHL games across multiple seasons and game types (regular season and playoffs), using the DataAcquisition class. It covers fetching game data via API endpoints, saving the data locally, and ensuring a smooth, automated process.

### Overview of the DataAcquisition Class
The DataAcquisition class is designed to make downloading play-by-play and landing data easy and automated. It connects to the NHL’s API to retrieve game information based on specified seasons and game types. The core functionalities include:
- Fetching game IDs for selected seasons and game types.
- Retrieving play-by-play data for each game.
- Retrieving landing data for each game
- Saving game data to your local system in JSON format.
- Handling additional landing information related to the games (optional).

#### Key Components
-  **\_\_int\_\_**: This method initializes the class with the selected seasons, game types, and file path for saving the data.
- **_get_game_request_url**: A helper function to build the URL for retrieving play-by-play data for a specific game.
- **get_associated_game_ids**: Fetches all relevant game IDs for the provided seasons and game types.
- **get_game_data**: Retrieves play-by-play data for a specific game by its game ID.
- **download_play_by_play_data_for_specific_season_gametype**: Downloads and saves the play-by-play data for all games of a specific season and game type.
- **download_all_play_by_play_data**: Automates downloading of play-by-play data for all specified seasons and game types.
- **get_landing_information**: Retrieves landing data for a specific game by its game ID.
- **download_all_landing_information**: Automates downloading of play-by-play data for all specified seasons and game types.

 **Step-by-Step Example**
 
Let’s assume you’re interested in downloading play-by-play data for multiple NHL seasons, including both regular season and playoff games. Here’s how to go about it:

**Step 1: Initialize the DataAcquisition Class**
 
We need to specify which seasons and game types we are interested in. In NHL game types, '2' represents regular season games, and '3' represents playoff games.
![image](https://github.com/user-attachments/assets/3b4b2e9d-065d-4112-b25e-b1b3ee8e248a)

This initialization sets up the necessary parameters to interact with the NHL API.

**Step 2: Download All Play-by-Play Data**

To download the play-by-play data for all games in the selected seasons and game types, you can call the following method:
![image](https://github.com/user-attachments/assets/9f77a38c-ad42-4597-9353-da5de029dad8)

This will:
- Fetch the game IDs for all games within the specified seasons and game types.
- Retrieve play-by-play data for each game and save it to the specified files_path (e.g., data/).
- Use the tqdm library to show a progress bar as data is downloaded.

**Step 3: Inspect the Downloaded Files**

After the download is complete, you’ll find the data saved as individual JSON files in the data/ folder. Each file is named based on the game ID, allowing you to easily access and analyze specific games later on.

**Customization: Downloading Data for a Specific Season and Game Type**

If you’re only interested in downloading data for a particular season (say, the 2020-2021 season) and only for regular season games, you can use the method download_play_by_play_data_for_specific_season_gametype:

![image](https://github.com/user-attachments/assets/05659901-6f00-40bd-b369-0c6b8ec784e6)
This allows you to narrow down the data you want to download without retrieving unnecessary data for other seasons or game types.

**Downloading landing Data**

The process to download the landing data is almost identical to downloading the play-by-play data. You can call the download_all_landing_information() method from the previously instantiated DataAcquisition object:
![image](/assets/landing_data_acquisition.PNG) 
where seasons and game_types are the same as previously defined.

**Functionality Summary**

- **Ease of Use**: The DataAcquisition class abstracts away the complexities of interacting with the NHL API. You don’t need to worry about constructing API requests manually.
- **Flexibility**: You can specify any seasons and game types, ensuring you have control over what data is downloaded.
- **Automation**: Once set up, the class can automatically fetch and save all relevant game data in a structured format.


## Debugging Tool

![](/assets/ipywidget1.png)
![](/assets/ipywidget2.png)


### Tool's code
![](/assets/code1.png)
![](/assets/code2.png)
![](/assets/code3.png)

### Description of how the tool works
Choose the type of game first. Then, use the first slider to navigate through all the available games. After selecting a game, use the second slider to explore the different events within that game. The output will display detailed information about the game and its corresponding events.


## Tidy data

### Snippet of final dataframe
![image](/assets/final_dataframe_1.png)
![image](/assets/final_dataframe_2.png)

Above are screenshots of our final dataframe resulting from the tidy data step.

### Additional features to be considered

**Labeling a shot as a rebound shot**
It would be interesting to know if a shot taken was actually a rebound shot. To do this, we would have to get the timestamps for each shot event. Then, any two shots that were taken within 2-3 seconds of each other could be considered to be rebound shots. Another method would be to take a look at 'blocked-shot' events that were made by a goalie. Any shot ensuing this event would also be considered to be rebound shots.

**Checking if a shot is off the rush**
Shots off the rush can be identified using 'takeaway' and 'giveaway' events that are present in the play-by-play data. A 'takeaway' is a form of turnover in which the player takes the puck from the opposition, while a 'giveaway' is a form of turnover where the player makes an unforced error that results in giving the puck up to the opposition. Any shot that is taken right after these events in a short amount of time can be considered to be shots that are off the rush.

**Identifying Faceoff plays**

## Simple Visualizations
### 1. Shot distribution for season 2019-2020
![Figure 1](/assets/shot_types_2019.png) 
The figure above shows the shot distribution and goal ratio for each shot type for the season 2019-2020. From the plot, we can see that the most dangerous type of shot appears to be the "tip-in" with a goal rate of around 16.7\%. However, the most common type of shot is the "wrist" shot by a large margin. The stacked bar plot is appropriate to help visualize and compare proportion of shot types across the league. The red line plot helps give an exact answer on how effective a shot is. Together, both plots help give insights on shot distribution and efficiency.

### 2. Relationship between shot distance and goal
![Figure 1](/assets/distance_goal_2018.png) 
![Figure 1](/assets/distance_goal_2019.png) 
![Figure 1](/assets/distance_goal_2020.png) 
From the above plots, we can see that the closer the puck is to the net, the higher the chance of scoring. One interesting observation is that when the puck is at the opposite end of the goal (at around 180 to 200 feet), there seems to be an odd increase in the goal rate. These goals are likely scored through open nets. Combining this with the low amount of shots recorded, the slight upwards trend observed from the 70 to 200 feet is not so surprising. Note that the graphs are almost identical over the past three seasons. The goal rate starts at around 30\% and decreases to a very low point until about the 70 feet range. Then there there is a slight upwards trend from 70 feet onwards. We decided that the line plot is the most useful plot to describe the goal rate and number of shots. It allows us to easily see trends given a distance from the net.

### 3. Relationship between shot distance, shot type and goal for 2021-2022
![Figure 1](/assets/distance_shot_goal_2021.png) 
The figure above shows the goal rate given the shot type and the distance from the net for the 2021-2022 season. We can see that at very close range, deflections have very high scoring chances and wrap-arounds have the lowest scoring chances. All shots see a rapid decrease when getting further away from the net, which no clear shot being the most dangerous one. However, we can note that the deflected shot has two spikes occurring at around 45 feet and 60 feet. The shots scoring beyond 75 feet are likely due to open nets, which are easy to score even from afar. The spikes in the data in the zone are possibly due to the rarity of shots beyond 75 feet made on open nets.

## Advanced Visualizations: Shot Maps
### 1. Interactive Offence Zone Plot

Seasons:
<select id="plot-selector" onchange="showPlot(this.value)">
  <option value="20162017">2016-2017</option>
  <option value="20172018">2017-2018</option>
  <option value="20182019">2018-2019</option>
  <option value="20192020">2019-2020</option>
  <option value="20202021">2020-2021</option>
</select>

<div id="plot-container">
  <div id="plot-20162017">{% include offensive_plots_20162017.html %}</div>
  <div id="plot-20172018" style="display: none;">{% include offensive_plots_20172018.html %}</div>
  <div id="plot-20182019" style="display: none;">{% include offensive_plots_20182019.html %}</div>
  <div id="plot-20192020" style="display: none;">{% include offensive_plots_20192020.html %}</div>
  <div id="plot-20202021" style="display: none;">{% include offensive_plots_20202021.html %}</div>
</div>

<script>
  function showPlot(plotId) {
    var plots = ["20162017", "20172018", "20182019", "20192020", "20202021"];
    
    plots.forEach(function(id) {
      document.getElementById("plot-" + id).style.display = (id === plotId) ? "block" : "none";
    });
  }
</script>

### 2. Interpretation for the Plot

This shot map shows how a team's shooting habits compare to the league average during 5-on-5 play. The colors highlight the differences in shooting frequency from different areas of the ice:

* Red areas show where the team takes higher shot probability than the league average, often indicating high-pressure offensive zones.
* Blue areas show where the team takes lower shot probability compared to the average, meaning they generate less offense in those spots.
* White areas represent spots where the team shoots at a rate that's about equal to the league average.

By using this map, you can easily see where a team tends to be more or less aggressive in creating scoring chances.


### 3. Avalanche's Comparison for the 2016-17 and 2020-21 Seasons

| ![Figure 1](/assets/COL_2016.png) | ![Figure 2](/assets/COL_2020.png) |
|:----------------------------:|:----------------------------:|
| Fig 1: The 2016-17 Season         | Fig 2: The 2020-21 Season         |

**2016-17 Season:**
* Shot density: In the 2016-17 heatmap, there is a distinct lack of dense shot attempts in the high-danger areas (the slot and areas right in front of the net). This indicates that the Avalanche struggled to generate high-quality scoring opportunities.

* Outside shots: There's a noticeable tendency for shots to come from the outside and at the point, which are less likely to result in goals.

**2020-21 Season:**
* Shot density: The 2020-21 heatmap, in contrast, shows a significant concentration of shot attempts directly in front of the net, especially in the high-danger areas. This suggests that the team improved its offensive play by generating more dangerous opportunities.

* Overall performance: The Avalanche were one of the top teams in the NHL during the 2020-21 season, winning the President’s Trophy for having the best regular-season record. This high concentration of shots in the most effective scoring zones reflects their high-powered offense during this period.

**Conclusions:**
* Shot quality and positioning: The difference in shot maps shows a clear improvement in shot quality and offensive positioning. The 2020-21 team was much more effective at getting to the high-danger areas (closer to the net), whereas the 2016-17 team struggled to generate those chances, taking more perimeter shots.

### 4. Contrasting: A Shot Map Analysis of the Sabres and Lightning from 2018-21 Seasons

| ![Figure 3](/assets/Sabres_2018.png) | ![Figure 4](/assets/Lightning_2018.png) |
|:----------------------------:|:----------------------------:|
| Fig 3: Sabres 2018         | Fig 4: Lightning 2018         |

| ![Figure 5](/assets/Sabres_2019.png) | ![Figure 6](/assets/Lightning_2019.png) |
|:----------------------------:|:----------------------------:|
| Fig 5: Sabres 2019         | Fig 6: Lightning 2019         |

| ![Figure 7](/assets/Sabres_2020.png) | ![Figure 8](/assets/Lightning_2020.png) |
|:----------------------------:|:----------------------------:|
| Fig 7: Sabres 2020         | Fig 8: Lightning 2020         |


**Buffalo Sabres:** 
* 2018-19: The Sabres' shot map shows a general lack of concentration in high-danger areas (directly in front of the net). They seem to take many shots from the perimeter, with some activity near the slot but not consistently.

* 2019-20: This season continues to show perimeter shooting, with slightly more activity in front of the net compared to 2018-19, but still not as dense as it needs to be for a successful offense.

* 2020-21: Similar to previous seasons, the Sabres struggle to generate high-danger chances, with more shots coming from outside the prime scoring areas. The overall offensive production seems scattered and lacks a consistent threat close to the net.

**Tampa Bay Lightning:**
* 2018-19: The Lightning's shot map is strikingly different from Buffalo's, with a heavy concentration of shots directly in front of the net. This shows a team that consistently gets into the high-danger areas and capitalizes on more dangerous scoring opportunities.

* 2019-20: This trend continues with another strong focus on high-danger areas, and their offense remains potent, which is likely a significant factor in their successful Stanley Cup win this season.

* 2020-21: Again, the Lightning's shot map shows a high concentration of shots in the slot and around the net, demonstrating a consistently dangerous offense that led them to a second consecutive Stanley Cup victory.

**Key Observations:**
* Sabres' Struggles: Buffalo's struggles can be largely attributed to their inability to generate consistent high-danger chances. Their shot maps show a lot of perimeter shooting, which is less likely to lead to goals. This lack of quality scoring opportunities is likely one of the key reasons they have not been competitive in recent years.

* Lightning's Success: Tampa Bay's success can be clearly seen in their shot maps. They consistently generate shots in the high-danger areas, which correlates with higher goal-scoring potential. Their focus on quality chances near the net has been a key component of their back-to-back championships.

**Limitation:**
* The shot maps provide a clear indication of why Tampa Bay has been so successful and why Buffalo has struggled offensively. However, while shot location is an important factor, it doesn’t account for other critical aspects like defensive play, goaltending, special teams, or the overall quality of the roster. These maps give us insight into offensive tendencies but do not capture the complete picture of why teams succeed or fail over a season.

* In conclusion, these shot maps paint a strong picture of why Lightning has been so successful and why Sabres has struggled, but they are just one piece of the overall puzzle.



