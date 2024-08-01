# Movie Data Analysis Dashboard

## Table of Content
 - [Project Overview](#project-overview)
 - [Data Sources](#data-sources)
 - [Results and Findings](#results-and-findings)
 - [Challenges](#challenges)

### Project Overview
This data analysis project aims to provide insights into the performance and trends of movies from 2012 to 2016. 
By analyzing various aspects of the movie data, we seek to identify patterns, make data-driven recommendations, and gain a deeper understanding of the industry's dynamics. 

### Data Sources
Movie Data: The primary dataset used for this analysis is the [3NHyUVbSmqf2vlnJalLU_Movies Data.xlsx](https://github.com/user-attachments/files/16449093/3NHyUVbSmqf2vlnJalLU_Movies.Data.xlsx) file, containing detailed but raw information about each movie's box office revenue, geres, actors, directors etc.

### Tools
 - Power Query - used for Data Cleaning 
 - Excel, Pivot Tables - used for Data Analysis, Creating reports and visualizations

### Data Cleaning and Preparation
In the initial data preparation phase we performed the following tasks:
1. Data loading and inspection
2. Handling errors, missing values
3. Data cleaning and formatting

The final excel file after all the steps of data cleaning and preparation performed via PowerQuery can be found at [Movie data and dashboard.xlsx](https://github.com/user-attachments/files/16449140/Movie.data.and.dashboard.xlsx) (sheet named "Movie Data").

 ### Exploratory Data Analysis
  - which genres were the most profitable during the period of YY2012-2016?
  - Which zctors were the most successful?
  - etc

### Results and Findings
The best movie was...

The best actor was...

etc
![Dashboard 1](https://github.com/user-attachments/assets/23a5b151-75f0-4787-b481-9443d6fd92d0)
![Dashboard 2](https://github.com/user-attachments/assets/ce88e07d-fa97-4a76-908c-9375e7a4e645)
### Challenges
#### M Language 
One of interesting features / challenges I was working with was a specific code for Grouping in M language which enable me to Combine genres together for further analysis.
We had 2 different columns for genres, but we needed them to be combined into one in order to have the same format (e.g. "action/comedy" not "comedy/action").
```
= Table.Group(#"Sorted Rows1", {"Movie Title"}, 
                                            {{"Combined Genre", each Text.Combine([Concat Genre], " / "), type text},
                                            {"AllData", each _, 
                                                        type table [Movie Title=nullable text, Release Date=nullable date, Wikipedia URL=nullable text, Concat Genre=nullable text, Director=nullable text, Actor First=nullable text, Actor Second=nullable text, Actor Third=nullable text, Actor Fourth=nullable text, Actor Fifth=nullable text, #"Budget ($)"=nullable number, #"Box Office Revenue ($)"=nullable number]}
                                            }
```
### Excel Dashboard
The final excel file can be downloaded here: [Movie data and dashboard.xlsx](https://github.com/user-attachments/files/16449166/Movie.data.and.dashboard.xlsx) (sheet named "Dachboard").
