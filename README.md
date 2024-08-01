# Movie Data Analysis Dashboard

## Table of Content
 - [Project Overview](#project-overview)
 - [Data Sources](#data-sources)
 - [Results and Findings](#results-and-findings)
 - [Challenges](#challenges)

### Project Overview
This data analysis project aims to find trends and provide insights about movies released in the period of YY2012-2016. 
By analyzing movie performance data we seek to identify patterns, make data-driven recommendations and get a deep understanding of the industry's dynamics. 

### Data Sources
The primary dataset used for this analysis is the [3NHyUVbSmqf2vlnJalLU_Movies Data.xlsx](https://github.com/user-attachments/files/16449093/3NHyUVbSmqf2vlnJalLU_Movies.Data.xlsx) file, containing detailed but raw information about each movie's release date, budget, box office revenue, geres, actors, directors,  etc.

### Tools
In order to process the raw data I used the following tools: 
 - Power Query - for Data Cleaning 
 - Excel, Pivot Tables - for Data Analysis, creating reports and visualizations

### Data Cleaning and Preparation
In the initial data preparation phase we performed the following tasks:
1. Data loading and inspection
2. Handling errors, missing values
3. Data cleaning and formatting

The process included fixing data types, deleting duplicates and empty columns, replacing ID columns for Genres, Directors and Cast with the real names for more convenient analysis, merging data in those cells where there were more than one genre type, calculating return on investment (ROI) ratio.

The final excel file after all the steps of data cleaning and preparation performed via PowerQuery can be found at [Movie data and dashboard.xlsx](https://github.com/user-attachments/files/16449140/Movie.data.and.dashboard.xlsx) (sheet named "Movie Data").

 ### Exploratory Data Analysis
 After we got the initial data handled and prepared for further analysis we could actually start working with data to find the answers for the following questions:
  - which movies released within YY2012-2016 brought highest revenues?
  - what genres were the most popular during that period?
  - which movies (and genres) were the most and the least profitable ones?
  - which movies released within the period of YY2012-2016 had the highest and the lowest budgets? 
  - Which actors were the most successful?
  - What time of the year is better for new movie release?
  - Are there any correlations between  these results?

### Results and Findings
![Dashboard 1](https://github.com/user-attachments/assets/23a5b151-75f0-4787-b481-9443d6fd92d0)
![Dashboard 2](https://github.com/user-attachments/assets/ce88e07d-fa97-4a76-908c-9375e7a4e645)
According to TOP genres by box office the most popular genres during the period of YY 2012-2016 were different variations / combinations of action, comedy, adventure and drama. The action / adventure movies had the highest budgets which is really important for such kind of movies, and that turned out to 2 of 5 top budget movies generated ones of the highest revenues (Batman v Superman & The Hobbit). 
The lowest budget genre is horror. This genre is specific and obviously isn`t as popular as action / adventure / comedy or other genres but it is the most profitable one not because of high revenues but because of low budget needed to create such type of movie.
The best time to release a new movie during the period of YY2012-2016 was march and summer months which could mean that families visit cinema theatres more during school breaks. So analyst could reccomend to release movies with highest budgets (action / comedies and other family-type genres) during that period.

### Challenges
#### M Language 
One of interesting features / challenges I was working with was a specific code for Grouping in M language which enable me to Combine genres together for further analysis.
We had 2 different columns for genres, but we needed them to be combined into one in order to have the same format (e.g. "action/comedy" not "comedy/action").
This code wasn`t able in excel basic tools so I had to search for it and insert manually in one of PowerQuery steps. The code itself is:
```
= Table.Group(#"Sorted Rows1", {"Movie Title"}, 
                                            {{"Combined Genre", each Text.Combine([Concat Genre], " / "), type text},
                                            {"AllData", each _, 
                                                        type table [Movie Title=nullable text, Release Date=nullable date, Wikipedia URL=nullable text, Concat Genre=nullable text, Director=nullable text, Actor First=nullable text, Actor Second=nullable text, Actor Third=nullable text, Actor Fourth=nullable text, Actor Fifth=nullable text, #"Budget ($)"=nullable number, #"Box Office Revenue ($)"=nullable number]}
                                            }
```
### Excel Dashboard
The final excel file can be downloaded here: [Movie data and dashboard.xlsx](https://github.com/user-attachments/files/16449166/Movie.data.and.dashboard.xlsx) (sheet named "Dachboard"). It is possible to play with different timelines and slicers in order to filter the data needed for specific analysis (e.g. to see the movies filmed by exact director or released within the exact period of time). Almost all the data is connected which makes it easy to build correlations and analyse the trends.
