# Most-Streamed-Spotify
- In this report, I will report a huge data set based on "Most Streamed Spotify Songs 2023". In this report, I will be answering the following questions:

1. Overview of Dataset

2. Basic Descriptive Statistics

3. Top Performers

4. Temporal Trends

5. Genre and Music Characteristics

6. Platform Popularity

7. Advanced Analysis

# Overview of Dataset
- At first, you may think that you must create a data set for this enormous size, but we can just download the data, which will be labeled as an Excel file. First, we need to import pandas, matplot, and seaborn. This is required for the data wrangling

![image](https://github.com/user-attachments/assets/b8431010-9aeb-4534-86d8-eefd5456e33f)

Image 1.1 - Importing Pandas, Matplot, and Seaborn


- Now, we need to open the dataset, so use the following code to open the data. Variable "df" is used to name the data. There is additional "encoding" and "encoding error" because it will run an error and not open as usual when using read_csv.

![image](https://github.com/user-attachments/assets/ef8f0ae1-941b-4979-8a14-89f896f41352)

Image 1.2 - Opening the dataset

1. How many rows and columns does the dataset contain?
- Looking at the dataset of variable df, there are precisely 953 rows and 24 columns.

![image](https://github.com/user-attachments/assets/dd520e30-494f-4d96-b2f8-b2f3af30468f)

Image 1.3 - The data with its numbers of rows and columns.

2. What are the data types of each column? Are there any missing values?
- To check for the data type of each column, I used this code: "df.info()" to see the data types for each column.

![image](https://github.com/user-attachments/assets/6a28113d-bd53-4a18-9f7a-c8b67a4889a0)

Image 1.4 - Data type for each column

- Upon inspection, the two common data types used are "objects" and "int64".
  
- To check if there are any NaN values in each data set, I used this code: "df.isna().sum()" to see the total NaN values in each column

![image](https://github.com/user-attachments/assets/de90fa4f-6e7b-43c0-b834-16530e682651)

Image 1.5 - NaN Values of each column

- Upon inspection, the column "in_shazam_charts" has 50 NaN values, and the column "key" has 95 NaN values, and the column "streams" has 1 NaN value.

# Basic Descriptive Statistics

1. What are the mean, median, and standard deviation of the streams column?
- At first, I could not find the mean, median, and standard deviation of the streams column because it has a data type of "objects." To find the mean, median, and mode of the streams column, I have to convert the data type of the streams column from "object" to "float". So, to convert the data type for the streams column, I use this code for conversion:"df["streams'] = pd.to_numeric(df["streams"], errors="coerce"). I added errors="coerce" to handle any value that cannot be converted with a number. It will be converted into a NaN because it will raise an error if it is not converted into "float".

![image](https://github.com/user-attachments/assets/a21516a9-6cc6-40b6-851e-d6c649f568cd)

Image 2.1 - "streams" column converted from "objects" to "float64"

- Now we can find the mean, median, and standard deviation of the "streams" column.
- To find the mean, I use this code: "df["streams"].mean()"
- To find the median, I use this code: "df["streams"].median()"
- To find the standard deviation, I use this code: "df["streams'].std()"

![image](https://github.com/user-attachments/assets/f328e53a-8be3-4f88-bd48-7bab5394f259)

Image 2.2 - Mean, Median, and Standard Deviation of the "streams" column

2. What is the distribution of released_year and artist_count? Are there any noticeable trends or outliers?
- To find the distribution of released_year and artist_count, I used a boxplot chart to find their distributions. First, I will show the code for how I plotted the data. I used Matplot and Seaborn to find their distributions.

![image](https://github.com/user-attachments/assets/a7bee403-8537-404a-9e0c-b2d078d29f29)

Image 2.3 - Code for the plotting distribution for column "released_year" and column "artist_count"

Code Explanation:
- "plt.figure" allows me to adjust the size of the figure, considering that there are a lot of x values and the years make the chart messy.
- "sns.boxplot" allows me to plot the chart by using boxplot. I identified the data to be chart is from variable "df". The x data will be used from column 'released_year,' and the y data will be used as 'artisti_count.' I also adjusted the linewidth to 1 in order to tidy the data. I also adjusted the filesize to 10 because upon looking at the chart, the outliers or trends were small in size and had to be adjusted by using the filesize code.
- "plt.xticks", aside from "plt.figure", allows me to adjust the font size of the years for the x values and also allows rotation for adjustment.
- "plt.yticks" only allows me to adjust the font size of the number for 'artist_count'
- "plt.xlabel" allows me to add a text on the x-axis as the "Released Year" and also allows me to adjust the font size.
- "plt.ylabel", similar to "plt.xlabel", allows me to add a text on the y-axis as the "Artist Count" and also allows me to adjust the font size.
- By running the code from Image 2.3, I receive this chart:

![image](https://github.com/user-attachments/assets/b665b862-4efe-4e9e-8565-78b0d6508d77)

Image 2.4 - Boxplot chart of Released Year and Artist Count

- So, are there any noticeable trends or outliers? Yes, there were some noticeable outliers and trends. There was only 1 outlier shown in 1999, but as the year progresses, the outliers for different years increase. The increase started in 2013 with 2 outliers and went up to 2023 with 3 outliers. However, the year 2022 has the most outliers, with 4.

#  Top Performers
Which track has the highest number of streams? Display the top 5 most streamed tracks.
- I did some indexing to find the top 5 tracks with the highest number of streams. The code for indexing is: "df.loc[df['streams'].nlargest(5).index, 'track_name']".

![image](https://github.com/user-attachments/assets/55300937-fef1-4969-9841-a93825f704d4)

Image 3.1 - Top 5 tracks based on the number of streams

- As shown above, the top 5 tracks based on the number of streams are:
- "Blinding Lights" - 55 streams
- "Shape of You" - 179 streams
- "Someone You Loved" - 86 streams
- "Dance Monkey" - 620 streams
- "Sunflower - Spider-Man: Into the Spider-Verse" - 41 streams

Who are the top 5 most frequent artists based on the number of tracks in the dataset?
- To find the top 5 most frequent artists based on the number of tracks, I did some indexing to locate the top 5 artists. The code for indexing is: df["artist(s)_name"].value_counts()"

![image](https://github.com/user-attachments/assets/6fe96b83-1956-4344-9834-e1c100465825)

Image 3.2 - Top 5 most frequent artists based on the number of tracks in the dataset

- As shown above, the top 5 most frequent artists based on the number of tracks in the dataset are:
- Taylor Swift - 34 tracks
- The Weeknd - 22 tracks
- Bad Bunny - 19 tracks
- SZA - 19 tracks
- Harry Styles - 17 tracks

# Temporal Trends
1. Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.
- For this question, I analyze each track released over time. Using these questions and a countplot, I plotted the number of tracks released by year. First, I plotted the number of tracks released by year. So the code for plotting the number of tracks released by the year is:

![image](https://github.com/user-attachments/assets/61f3e630-0dc8-4c32-acd1-7480f1f1e4d1)

Image 4.1 - Code for the number of Tracks released per year

- With this code, the following chart below shows the chart of the number of tracks released per year

![image](https://github.com/user-attachments/assets/551e7093-6ed5-4d24-9fc6-fb928d7b14d5)

Image 4.2 - Countplot of the number of tracks per year.

- By looking at the chart, 2022 has the highest number of released tracks.

2. Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?
- I plotted this question using countplot. So the code for plotting the released per month is:

![image](https://github.com/user-attachments/assets/6f8dc50f-f722-48d2-bac6-7e0304523237)

Image 4.3 - Code for plotting the number of tracks released per month.

- By inputting this code, I get the following chart and data result:

![image](https://github.com/user-attachments/assets/12e97456-19f4-4375-9406-9b2f285c3533)

Image 4.4 - Bar chart for the number of tracks released per month.

- Is there a noticeable pattern? There is no noticeable pattern since the number of tracks for each month is different. Lastly, the month that sees the most releases is the first month: January.

#  Genre and Music Characteristics
1. Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?
- To examine the correlation between the streams and musical attributes of bpm, danceability_%, and energy_%, I used a heatmap chart to correlate the relationship of the streams and musical attributes. The following is the code for the heatmap chart.

![image](https://github.com/user-attachments/assets/9b9d4d6c-6d48-4a08-8adb-863a0bf4abc5)

Image 5.1 - Code for heatmap correlation

- Inputting this code will give the following chart:

![image](https://github.com/user-attachments/assets/8d400352-5d00-44ef-855c-ac6c9f46ed71)

Image 5.2 - Heatmap correlation of streams and musical attributes

- So, which musical attribute influence streams the most? According to the heatmap chart, danceability_% and energy_% influence the streams the most.

2. Is there a correlation between danceability_% and energy_%? How about valence_% and acousticness_%?
- As previously answered, there is a correlation between danceability_% and energy_% with a value of 0.2.
- For the correlation of valence_% and acousticness_%, I created the same heatmap chart but with a different color and included valence_% and acousticness_%. The following code below shows the code for the 2nd heatmap chart:

![image](https://github.com/user-attachments/assets/5b0547c1-fa3a-476c-bdc3-ea9df07de45d)

Image 5.3 - Code for the second heatmap chart

- With this code, I will have the following chart:

![image](https://github.com/user-attachments/assets/1672d5a8-6d55-45d9-bd1a-3d4f34f2663a)

Image 5.4 - Heatmap chart with valence_% and acousticness_%
- So is there a correlation between valence_% and acousticness_%? According to the heatmap chart, there is a -0.082 correlation coefficient, meaning they are opposite.

# Platform Popularity
1. How do the numbers of tracks in spotify_playlists, deezer_playlist, and apple_playlists compare? Which platform seems to favor the most popular tracks?
- To compare this, we have to index their columns. By using this code: "df[['in_spotify_playlists', 'in_deezer_playlists','in_apple_playlists']]", we will get the following output:

![image](https://github.com/user-attachments/assets/7edfe413-8404-4dae-a0ff-e3e765009c88)

Image 6.1 - Indexing of the 3 platforms

- To compare, Spotify seems to have more tracks than Apple and Deezer. This means that Spotify seems to favor the most popular tracks.

 # Advanced Analysis

1. Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?
- To do this, I have to plot it using a bar chart. The following image is the code syntax for the bar chart with key vs streams:

![image](https://github.com/user-attachments/assets/3e5f2a1e-86ab-4a82-a1e8-8da16a8e4cc6)

Image 7.1 - Code and the chart for the similarities of keys based on the number of streams

- Next, I have to plot for the mode. The following image is the code syntax for the bar chart with mode vs streams:

![image](https://github.com/user-attachments/assets/9762e8d6-1ec9-464d-8b53-ff3b750c2aa1)

Image 7.2 - Code and the chart for the similarities of modes based on the number of streams

- So, are there patterns with the same key? Yes there are, key A# and D# appears that they are the only key to be the same.
- What about for mode? According to image 7.2, there seem to be no patterns for similarity.

2. Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.
- To do this, I have to compare which are the most frequently appearing artists for all playlists and charts. The following code below shows the comparison for all playlists and charts:

![image](https://github.com/user-attachments/assets/6120172c-2be6-4a13-a823-ff4da2392619)

Image 7.3 - Code for playlists and charts comparison for the most frequently appearing artists

- So what I learn from this comparison? It appears just because Tayloy Swift is the most streamed artists, doesn't mean that she is the most streamed in others. She is the most frequent for both Spotify and Charts. She also is the most top frequent for Apple Charts. The Weeknd, Madonna, and Playboi Carti are the most frequently appearing artists in the Deezer playlists. Chris Brown, Rvssian, and Rauw Alejandro are the most frequently appearing artists in Deezer Charts. Bizarrap and Peso Pluma are the most frequently appearing artists in Apple playlists.

# Extra Insights

- I think for a track to be popular or catchy is by looking at the heatmaps. It appears valence_% and danceability_% has somewhat correlation on what makes a good track. Another is the valence_% and energy_% also has correlation on what makes a good track. With this, the most common denominator on what makes a good track is the valence_%. Apart from musical attributes, the popularity of the artist(s) also what makes a track popular. Examples are Taylor Swift, and The Weeknd. Their one of the most frequent artists that appear in Spotify playlist and charts, with spotify being the most used music media.
