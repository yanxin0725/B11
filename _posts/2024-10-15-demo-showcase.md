---
layout: post
title: B-11 Project Display
---
## Data Acquisition
###  Downloading Play-by-Play Data from the NHL API
When diving into a data science project involving hockey statistics, one of the key steps is obtaining accurate and comprehensive data. This guide will walk you through how to download the play-by-play data for NHL games across multiple seasons and game types (regular season and playoffs), using the DataAcquisition class. It covers fetching game data via API endpoints, saving the data locally, and ensuring a smooth, automated process.

### Overview of the DataAcquisition Class
The DataAcquisition class is designed to make downloading play-by-play data easy and automated. It connects to the NHL’s API to retrieve game information based on specified seasons and game types. The core functionalities include:
- Fetching game IDs for selected seasons and game types.
- Retrieving play-by-play data for each game.
- Saving game data to your local system in JSON format.
- Handling additional landing information related to the games (optional).

#### Key Components
- **__init__**: This method initializes the class with the selected seasons, game types, and file path for saving the data.
- **_get_game_request_url**: A helper function to build the URL for retrieving play-by-play data for a specific game.
- **get_associated_game_ids**: Fetches all relevant game IDs for the provided seasons and game types.
- **get_game_data**: Retrieves play-by-play data for a specific game by its game ID.
- **download_play_by_play_data_for_specific_season_gametype**: Downloads and saves the play-by-play data for all games of a specific season and game type.
- **download_all_play_by_play_data**: Automates downloading of play-by-play data for all specified seasons and game types.

#####**Step-by-Step Example**
Let’s assume you’re interested in downloading play-by-play data for multiple NHL seasons, including both regular season and playoff games. Here’s how to go about it:
######**Step 1**: Initialize the DataAcquisition Class
We need to specify which seasons and game types we are interested in. In NHL game types, '2' represents regular season games, and '3' represents playoff games.
![image](https://github.com/user-attachments/assets/3b4b2e9d-065d-4112-b25e-b1b3ee8e248a)
This initialization sets up the necessary parameters to interact with the NHL API.

######**Step 2: Download All Play-by-Play Data**
To download the play-by-play data for all games in the selected seasons and game types, you can call the following method:
![image](https://github.com/user-attachments/assets/9f77a38c-ad42-4597-9353-da5de029dad8)

This will:
- Fetch the game IDs for all games within the specified seasons and game types.
- Retrieve play-by-play data for each game and save it to the specified files_path (e.g., data/).
- Use the tqdm library to show a progress bar as data is downloaded.

######**Step 3: Inspect the Downloaded Files**
After the download is complete, you’ll find the data saved as individual JSON files in the data/ folder. Each file is named based on the game ID, allowing you to easily access and analyze specific games later on.

**Customization: Downloading Data for a Specific Season and Game Type**
If you’re only interested in downloading data for a particular season (say, the 2020-2021 season) and only for regular season games, you can use the method download_play_by_play_data_for_specific_season_gametype:

![image](https://github.com/user-attachments/assets/05659901-6f00-40bd-b369-0c6b8ec784e6)
This allows you to narrow down the data you want to download without retrieving unnecessary data for other seasons or game types.

**Functionality Summary**
- **Ease of Use**: The DataAcquisition class abstracts away the complexities of interacting with the NHL API. You don’t need to worry about constructing API requests manually.
- **Flexibility**: You can specify any seasons and game types, ensuring you have control over what data is downloaded.
- **Automation**: Once set up, the class can automatically fetch and save all relevant game data in a structured format.


## Debugging Tool

## Tidy data

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

* Red areas show where the team takes more shots than the league average, often indicating high-pressure offensive zones.
* Blue areas show where the team takes fewer shots compared to the average, meaning they generate less offense in those spots.
* White areas represent spots where the team shoots at a rate that's about equal to the league average.

By using this map, you can easily see where a team tends to be more or less aggressive in creating scoring chances.


### 3. Avalanche's Comparison for the 2016-17 and 2020-21 Seasons

| ![Figure 1](/assets/COL_2016.png) | ![Figure 2](/assets/COL_2020.png) |
|:----------------------------:|:----------------------------:|
| Fig 1: The 2016-17 Season         | Fig 2: The 2020-21 Season         |

* In the 2016-17 season, the Avalanche's shot map shows a scattered offensive presence, with only a small red area in front of the net indicating more shots than the league average. Large blue areas, especially on the wings and mid-range, suggest the team struggled to generate consistent offense, which is consistent with their last-place finish in the standings.

* By the 2020-21 season, the shot map shows a major shift. The red areas are much more pronounced, especially around the net, reflecting a stronger and more consistent offensive attack. The reduction in blue areas means they were generating more shots from across the ice, particularly in high-danger areas. This corresponds to their top finish in the league, highlighting a clear improvement in offensive performance and efficiency.

* The maps clearly show how the Avalanche transformed from a team with weak shot generation to one of the league's best in creating scoring opportunities.


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
* In all three seasons, the Sabres’ shot maps show some offensive presence near the opponent's net, with red regions indicating more frequent shooting. However, there are noticeable gaps and blue regions, especially in areas farther from the net and along the boards. This suggests inconsistent shot generation and an inability to consistently apply offensive pressure across the ice. Their offense seems limited to a few high-danger areas, but the lack of intensity in these red zones compared to Tampa Bay shows a potential weakness in creating high-quality scoring chances.

**Tampa Bay Lightning:**
* Tampa Bay's shot maps from the same seasons show a much more aggressive and consistent offensive presence. Each season, they generate a lot of red zones, particularly in the high-danger areas directly in front of the net. This indicates that Tampa Bay consistently produces more shots from prime scoring areas. There are also fewer blue areas, meaning they maintain a balanced offensive approach from multiple positions on the ice. This likely contributes to their ability to dominate games, as they create more frequent and dangerous scoring opportunities.

**Key Observations:**
* Consistency and Pressure: The Lightning's maps show a much more balanced and aggressive offensive presence, which likely explains their success. Their ability to consistently generate shots from dangerous areas year over year likely contributes to their ability to win tight games and perform well in the playoffs.

* Limited Offense for Buffalo: The Sabres, on the other hand, show inconsistency and a lack of pressure in key areas of the ice. This likely explains why they have struggled in recent years — their offense is not as threatening or well-rounded as Tampa Bay’s.
Limitations of Shot Maps:

* While these maps provide a good visual representation of shot generation, they don’t tell the full story. Other factors such as shot quality, team defense, goaltending, and overall game strategy also play crucial roles in determining success. Tampa Bay's success isn't just because they shoot more; it's also about the quality of those shots and their overall team play. Similarly, Buffalo's struggles can't be solely attributed to shot volume but are likely also due to issues like defensive weakness and inconsistent goaltending.

* In conclusion, these shot maps paint a strong picture of why Tampa Bay has been so successful and why Buffalo has struggled, but they are just one piece of the overall puzzle.



