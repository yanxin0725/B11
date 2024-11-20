# A Deep Dive into NHL Game Analysis

In this post, we’ll explore shot distributions and effectiveness, statistical trends as well as shot maps that shape each matchup during the regular and playoff season from the 2016-17 season all the way up to the 2023-24. We will also provide explanations on how we acquired the data and extracted the relevant features into a suitable format that can be used to create meaningful plots to help with the analysis of the games.

## Data Acquisition
###  Downloading Play-by-Play and Landing Data from the NHL API
When diving into a data science project involving hockey statistics, one of the key steps is obtaining accurate and comprehensive data. This guide will walk you through how to download the play-by-play and landing data for NHL games across multiple seasons and game types (regular season and playoffs), using the DataAcquisition class. It covers fetching game data via API endpoints, saving the data locally, and ensuring a smooth, automated process.



