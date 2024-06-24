This project uses data-set on Netflix Movies and TV shows from https://www.kaggle.com/datasets/rahulvyasm/netflix-movies-and-tv-shows. 

I first downloaded the netflix_titles.csv dataset and converted it to an xlsx format by opening a new excel file > Click on Data tab > click From Text/CSV > Popup window will open for you to select the netflix_titles.csv file > Select Import > Click Load > Save file

This dataset contains 8, 809 records and the following 12 variables: 

-   **show_id:** A unique identifier for each title.

-   **type:** The category of the title, which is either 'Movie' or 'TV Show'

-   **title:** The name of the movie or TV show

-   **director:** The director(s) of the movie or TV show (Contains null values for some entries, especially TV shows where this information might not be applicable)

-   **cast:** The list of main actors/actresses in the title (Some entries might not have this information.)

-   **country:** The country or countries where the movie or TV show was produced.

-   **date_added:** The date the title was added to Netflix.

-   **release_year:** The year the movie or TV show was originally released.

-   **rating:** The age rating of the title.

-   **duration:** The duration of the title, in minutes for movies and seasons for TV shows

-   **listed_in:** The genres the title falls under.

-   **description:** A brief summary of the title.

You will need to load the following packages in R:
library(readxl)
library(ggplot2)
library(dplyr) 
library(tidyr) 
library(skimr)  
library(here) 

Next, to clean the data prior to analysis you will need to...

Handle the missing values in the 'director' variable: 
>rawdata$director[is.na(rawdata$director)] <- "Unknown"

Convert the 'date_added' variable into an actual date format:
>rawdata$date_added <- as.Date(rawdata$date_added, format = "%m/%d/%Y")


Remove rows where 'type' is "William Wyler" or NA and create a 'cleaned_data' subset:
>cleaned_data <- rawdata %>%
>>  filter(type != "William Wyler" & type != "Unknown" & !is.na(type))

and then convert the 'type' variable into a factor:
>rawdata$type <- as.factor(rawdata$type)



Generally, any dataset should contain some meta-data explaining what each variable in the dataset is. (This is often called a **Codebook**.) For this simple example, the codebook is given as a second sheet in the Excel file.

This raw data-set should generally not be edited by hand. It should instead be loaded and processed/cleaned using code.

