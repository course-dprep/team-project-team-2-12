[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11726002&assignment_repo_type=AssignmentRepo)

# IMDB- the influence of a director on the movies openinggross

This project estimates how much influence the director of a movie has on the money the movies makes in its opening weekend. We have created an analyzation of the connection between director and opening gross, taking in to account the; amount of theaters the movie is shown in, the genre of the movie and also the runtime of the movie (length of the movie in minutes.). this tool helps to create an insight into the amount of influence a director has on the success of a movie.

## Research motivation

Every year around 500 movies gets released into the cinema’s, more than 60 percent of these movies do not make back the money that is invested in them. For the investors behind those movies making money is the most important part of investing, therefore it is important for the movie industry to get more profitable. When this is the case a logical effect is that more money will be invested and movies will go up in quality. Directors of movies have a key role in choosing cast members, production design and the complete creative aspect of filmmaking. The impact of a director on the end product of a movie is big as you can see, there this project is dedicated to finding out the direct impact of the director on the success of the movie. This tool can be used for choosing the right director for the right genre and therefore maximizing the profits of the movie.

## Research question
How much does the director of the movie influence the opening gross of the movie, taking into account the impact of the amount of theatres the movies is shown in, the genre of the movie and the runtime of the movie? 

## Research method
To collect the data a web scraper was built to collect the data from Boxofficemojo. Several data sets were collector from developer IMDB such as; title.basics.tsv.gz, title.crew.tsv.gz, name.basics.tsv.gz. From Box Office Mojo a web scraper was build to collect the following data; title, opening gross and amount of theaters. For the opening gross of a movie only the data for the top 1000 movies were available, for that reason the data from Box Office Mojo has been merged with the data of IMDB. The result were 992 observations out of 1000. The data had the be merged three several times to link all the different data sets with each other. 

For our regression analysis, we will use director_count as the independent variable of interest in the regression of the opening gross of movies on Imdb. As covariables, we used runtime in minutes and amount of theaters that the film was played in, as we expected that these variables would affect the opening gross. Probably, the more theaters the movie is played in, the higher the opening gross would be. Thus, a positive relationship is expected. Additionally, some people do not like long movies / movies of 190 minutes. Therefore,  the runtime in minutes is also expected to affect the opening gross. Concluding, these are the covariables we used in our regression analysis. The director count is the number of movies a director has directed. When a director has directed a lot of movies, especially popular movies,  he/ she is expected to be known by name. Therefore, we are interested in researching whether this affects the opening gross.

## conclusion
Looking at the results, we clearly observe a difference in the two means between the opening gross of films directed by directors with higher recognition (directed_above_median = 1) against directors with a lower recognition (directed_above_median = 0), and this difference is statistically significant. However, upon reviewing the results of the linear regression, it becomes clear that this outcome is predominantly driven by other variables. By including the variables “theaters” and “runtime_dummy,” we observe that the p-value for the variable “directed_above_median” becomes insignificant. The remaining variables in this model maintain their significance. Therefore, based on this dataset, it cannot be concluded that the director of a film has a significant impact on the opening gross of a film.

## Variables 

| Number| Variable| Description| Type|
|:-|:-|:-|:-|
| 1 | movie| The title of the movie                                  | String  |
| 2 | openinggross| The opening gross of the first weekend the movie premiered | Numeric |
| 3 | Theaters| The amount of theaters that the movie premiered in    | Numeric |
| 4 | runtimeMinutes| The duration of the movie in minutes                   | Numeric |
| 5 | genres| The genre of the movie                                  | String  |
| 6 | director_identifier| The unique identifier to identify which director directed the movie | String  |
| 7 | primaryProfession| The professions that a director has (sometimes they also have other roles in the movies such as actor or writer) | String  |
| 8 | runtime_dummy| A dummy variable that measures if a movie has a high (runTimeminutes above median) or low (runTimeminutes below median) runtime in minutes | Logical |
| 9 | director_count| The number of movies that a director has directed that are in this dataset | Numeric |
| 10| directed_above_median| A dummy variable that measures if a director has a high (director_count above median) or low (director_count below median) number of movies directed | Logical |



## Repository structure
```
├── data
   ├── dataset1
├── gen
   ├── analysis
     ├── input
   ├── data-preparation
     ├── input_downloading_and_merging
     ├── input_filtering
   └── paper
     ├── input
     ├── ouput
└── src
   ├── analysis
   ├── data_preparation
     ├── 1_Python_source_code
     ├── 2_data_download_and_merg
     ├── 3_data_filter_and_variable_expansion
   └── paper
├── .gitignore
├── README.md
├── makefile
```
# Example of reproducible research workflow -- Need to check this

This is a basic example repository using Gnu make for a reproducible research workflow, as described in detail here: [tilburgsciencehub.com](http://tilburgsciencehub.com/). 

The main aim of this to have a basic structure, which can be easily adjusted to use in an actual project.  In this example project, the following is done: 
1. Download and prepare data
2. Run some analysis
3. Present results in a final pdf generated using LaTeX

# Dependencies
## Software
In this research project, a diverse range of software applications were employed to gather and manipulate data effectively. Below, you will find a comprehensive list of the requisite software packages utilized throughout the course of this project: 
- R (Version 4.3.1) & RStudio (Version 2023.06.1)
- Python (Version 3.11.4)
- Make (Version 3.81)

## Packages
In the context of data preparation and analysis in R, various packages are employed. Below, you will find a categorized list of packages based on the specific purposes for which they are utilized:

Data preparation: 
- library(base)
- library(datasets)
- library(graphics)
- library(grDevices)
- library(methods)
- library(stats)
- library(utils)
- library(tidyverse)
- library(dplyr)   


Data analysis:
- library(base)
- library(datasets)
- library(graphics)
- library(grDevices)
- library(methods)
- library(stats)
- library(utils)
- library(readr)

# Recreating the Project: A Comprehensive Guide -- Need to check this
Voor dit project is ```make``` gebruikt om het project te automatiseren. Bij het runnen van de makefile die binnen deze repository niet in een map gestopt is worden alle map specifieke makefiles aangestuurd. Hiermee wordt het project gerund en hoeft het dus niet handmatig gedaan worden. Hieronder de volgorde waarin het project runt:

*src/python_source_code/1_boxofficemojo_openingweekendscraper.py
src/data-preparation/2_download_and_merge_data.R
src/data-preparation/3_data_filter_and_merg.R
src/analysis/4_Analysis.Rmd
**gen/clean.R

*Deze code wordt niet gerund door make. Omdat deze code statisch is en niet weinig aangepast zal worden over tijd is er voor gekozen om deze code niet te laten runnen via make. De dataset die uit deze webscraper komt is te vinden in data/weekend_data.csv. Wilt u deze scraper zelf laten runnen kan dit door het bestand te laten runnen in Python.

De clean.R wordt niet handmatig gerund en kan gerund worden om tijdelijke gegenereerde files te verwijderen uit de mappenstructuur. Deze wordt niet gelijk gerund omdat deze files gebruikt zouden kunnen worden om vanaf een later stadium in het project te resultaten opnieuw te runnen. Dit zorgt ervoor dat niet altijd de grote datasets hoeven worden ingeladen.

## Notes -- Need to check this
- `make clean` removes all unncessary temporary files. 
- Tested under Linux Mint (should work in any linux distro, as well as on Windows and Mac) 
- IMPORTANT: In `makefile`, when using `\` to split code into multiple lines, no space should follow `\`. Otherwise Gnu make aborts with error 193. 
- Many possible improvements remain. Comments and contributions are welcome!
