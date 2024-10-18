---
layout: post
title: B-11 Project Display
---
## Simple Visualizations
### 1. Shot distribution for season 2019-2020
![Figure 1](/assets/shot_types_2019.png) 
The figure above shows the shot distribution and goal ratio for each shot type for the season 2019-2020. From the plot, we can see that the most dangerous type of shot appears to be the "tip-in" with a goal rate of around 16.7\%. However, the most common type of shot is the "wrist" shot by a large margin. The stacked bar plot is appropriate to help visualize and compare proportion of shot types across the league. The red line plot helps give an exact answer on how effective a shot is. Together, both plots help give insights on shot distribution and efficiency.
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



