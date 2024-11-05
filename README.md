# Exploratory Data Analysis on Spotify 2023 Dataset
by: Christian Kyle S. Antonio | 2-ECE-C

Table of Contents:

- [About the Project](#about-the-project)
- [General Overview](#general-overview)
- [Top Performers](#top-performers)
- [Basic Descriptive Statistics](#basic-descriptive-statistics)
- [Temporal Trends](#temporal-trends)
- [Genre and Music Characteristics](#genre-and-music-characteristics)
- [Platform Popularity](#platform-popularity)
- [Advanced Analysis](#advanced-analysis)
- [Conclusion](#conclusion)

## About the Project
In this project, a data set containing various information on the top songs on Spotify for the year 2023 is given from a database website, Kaggle.com. This documentation will show the various findings after the dataset has been applied with basic statistical treatment and data visualization tools using Python.


*Raw data set preview:*

![{80FDEC63-C110-4F95-9497-B86D98282739}](https://github.com/user-attachments/assets/d2ea4766-fac9-4d42-bc58-fd2700737e2b)

### Libraries Used
* Pandas
* Matplotlib

## General Overview
To initialize the project, it important to first examine the data set that is provided. Using the attribute ".info()" that is included in the Pandas library, we are able to get some information regarding the characteristics of the data set.

From the image below, we can see that there are over 953 rows and 24 columns with every column primarily containing string (or object) and integer values. Each row corresponds to a specific track while the column corresponds to various information types for every row.

*.info() output of the given data set:*

![{4ADC5569-2A7A-4D58-BA13-C8066CFA97F6}](https://github.com/user-attachments/assets/f6be3559-c2ea-4ee7-99ea-ca857d1c8fd2)


Upon observing the information on the data set further, we can notice that there are two columns that have a non-null count less than that of the total number of tracks. This indicates that in these columns, there are tracks with missing values. To be precise, there are 85 missing key values and 50 missing in_shazam_charts values.

*columns with missing values:*

![{59672547-AEC8-490F-92A7-FE9B5CDE4020}](https://github.com/user-attachments/assets/18f63ba1-9a7c-415e-b4c7-1885275ba395)
![{C0700D8C-65F3-42E2-9B3C-35C7AD51323B}](https://github.com/user-attachments/assets/fd70971d-dfb3-4ac9-b3b8-6a326de1e969)


## Top Performers
The most logical first step in analyzing this dataset would therefore be to sort the track by the number of streams in descending order using the ".sort_values()" attribute in Pandas. However a problem arises as one of the tracks appears to have a non-numeric value and as such appears to be on top of the list. 

*initial output of .sort_values():*

![{1DB0669F-23B3-4FC7-9C2E-A006970517C5}](https://github.com/user-attachments/assets/e13c86df-949d-4dad-b11f-ee74c1b7d270)

Additionally, when observing the sorted list, the supposed top five tracks have less streams than one of the song in the bottom five tracks. Referring back to .info() output of the data set, we can see that this column is, in fact, in string data-type format as opposed to a numeric data-type like an integer or floating point thus it may be the cause of this problem.

*streams column of inital sorted data set:*

![{8575405C-B485-4EE4-89D7-FE3363C7A9F5}](https://github.com/user-attachments/assets/c41e3c07-df16-4d75-b2ed-964c003edc6a)

To fix these inconsistencies, a numeric value in string data-type for the problem track must first be assigned. In this case, it shall be assigned to 0 as it is effectively unknown in the context of this data set and doing so will place it at the bottom when the set is sorted by the number of streams:

![{78F5BE98-5C74-42CD-9F60-98AB1CC81C1D}](https://github.com/user-attachments/assets/a729b33c-7fe1-48e8-bc58-4c690782c1a0)

Then, the values for the streams column must be converted to a numeric data-type in order for it to be accurately sorted. Initially, using an integer data type will yield the following error:

![{056ADE63-63A0-4FDE-B558-F95A3B5453B9}](https://github.com/user-attachments/assets/09ebdccc-a99f-4306-96c4-cb16e0bbc48f)

This may potentially be because of how large the numeric values of the strings to be converted in the streams column therefore floating point data-type is more appropriate:

![{F4A88160-F4BE-4083-99D4-99702FE1E7BC}](https://github.com/user-attachments/assets/7739d5dd-84fb-444f-a020-363f4d0f287a)

After this, we can simply sort it again and use the .head() attribute to determine the top performing tracks by stream count which yields the following songs and their artists:

![{8EE9315E-718E-4987-A9BC-E5087EEE75B4}](https://github.com/user-attachments/assets/5cd982b4-b92d-48fa-b342-dc77ba9ef048)
![{914B3CE6-02C4-4025-A6F3-4EA57A699A3F}](https://github.com/user-attachments/assets/49c749db-416e-4fc3-bf1f-226508c890c5)

Using the .value_counts attributes included in Pandas, the number of songs written by an artist can be attained with the following syntax:

![{29901D62-669E-4816-B4CD-707838FBDC8F}](https://github.com/user-attachments/assets/f882dcc3-6bd6-4eb3-afef-e95b30844121)

.head(5) can then be used to get the top 5 artists with the most written songs in the dataset:

![{B5336841-46F8-4A86-B373-BA4887DFD2C3}](https://github.com/user-attachments/assets/c6b577b7-e68d-436d-946b-558cd59d6aa2)

### In Summary:

The Top Performing Songs by Stream Count Are:
- 1st: Blinding Lights by The Weeknd (3.7b)
- 2nd: Shape of You by Ed Sheeran (3.56b)
- 3rd: Someone You Loved by Lewis Capaldi (2.88b)
- 4th: Dance Monkey by Tones and I (2.86b)
- 5th: Sunflower - Spider-Man: Into the Spider-Verse by	Post Malone & Swae Lee (2.80b)

The Top Artists with the Most Written Songs:
- 1st: Taylor Swift (34)
- 2nd: The Weeknd (22)
- 3rd: Bad Bunny & SZA (19)
- 4th: Harry Styles (17)
- 5th: Kendrick Lamar (12)
  
## Basic Descriptive Statistics
Now that the streams count have numeric values, it can now be easily treated with basic descriptive statistics. To do this, the streams column will be called and the built-in attributes for mean, median, and mode in pandas can be used.

![{39520CB3-D925-4B3C-8CB9-97A170F0974C}](https://github.com/user-attachments/assets/894fb628-0f87-4ea5-80c6-626a17fbbc82)

The output is then printed and the results came out as: 

![{F9C7E726-BC0B-49B6-8FB2-1289F305DB5A}](https://github.com/user-attachments/assets/3902b37c-9923-419f-adac-2c2edd7cb51e)

Based on the results above, here are the Basic Descriptive Statistics of the Stream Count:
- **Mean**: 513.60 million
- **Median**: 290.23 million
- **Standard Deviation:** 566.80 million

The average streams of the top songs of 2023 were 513.6 million. To put this into perspective, if the average song length is three minutes, the combined total listening time of only the average streams is about 2,934 years. However, it should be noted that the standard deviation is significantly high which may indicate that there is a significant level of variety in the stream counts of the tracks in the data set. This is supported by the median being significantly lower than the mean, indicating that the stream counts per track are distributed more in higher values than in lower values.

The distribution of the tracks by release year and the number of artists on a track can then be extracted from the data set by plotting them on a histogram respectively using Matplotlib. From the graph below, we can see that there are far more songs that were released in the last 20 years all the combined total of the years before 2000. This may, in part, be due to Spotify mostly catering to demographics that are more versed in the internet and social-media in general thus their song preferences tend to be those that are popular in recent decades. It should be noted that there are outliers as early as the 1940s that are included in the dataset. These songs might be tracks that were popularized my social-media or classics that are associated with the holiday season.

![{B4F41631-0765-494C-B024-59BDC6C01BEC}](https://github.com/user-attachments/assets/5a097319-5b16-47d2-8c48-52f645c89353)

The graph below then shows that the dataset contains more tracks that were written by solo or duo artists.

![{3A74BA8D-926D-4597-B61F-F2893C11B38F}](https://github.com/user-attachments/assets/af2cc759-79cc-49cb-92ad-8b95669d957e)

## Temporal Trends
The data set can then be further analyzed by looking at the trendline of the number of tracks released over the years and the months. To do this, Matplotlib is used to get their respective graphs.

To determine the X and Y values of these graphs, the .value_counts() attribute in Pandas can be utilized as the main concern would be the instances of the years or months in each row. The number of these instances will therefore yield the number of tracks released per year or month. The X axis will therefore either be the years or months released while the Y axis will always be the number of tracks.

*X and Y values for Years vs. No. of Tracks Graph*

![{E44DA15B-C722-4D4B-B0BC-9CF4F48BE743}](https://github.com/user-attachments/assets/fe8a3821-46d9-4a95-bec8-ec815bcd5534)

*X and Y values for Months vs. No. of Tracks Graph*

![{06AD6571-A5CF-473E-9D48-2B63956EF178}](https://github.com/user-attachments/assets/c4d33965-57ad-4bdf-ae20-6f6de1cffe07)

After assigning the X and Y values, Matplotlib can be used to plot these values. From the results of the graph, and as confirmed by the previous distribution graph, it can be observed that the number of tracks released has spiked significantly in recent years with the trend likely to be continue going upwards in the next coming years. As for the song releases in each month of the year, it can be observed that there is a steady and gradual increase in the tracks released from the months leading up to October. A significant spike in the number of tracks released can then be observed that will persist until December.

![image](https://github.com/user-attachments/assets/55821558-fa10-4ea2-928a-8977f212a3e9)
![{A8A6A40D-3DF7-4ED9-9F3F-70301A9D46BE}](https://github.com/user-attachments/assets/c1a74848-219a-46b0-9770-df5388f00735)

![{C5C4A902-585A-43F3-8378-3E36F93F5500}](https://github.com/user-attachments/assets/c45eb41d-589b-4bb7-8f64-04a54c7f42cb)
![{BEB2DB40-7838-4659-B934-650464AA3283}](https://github.com/user-attachments/assets/67b349fe-32c0-4815-9210-beafe05dfc77)

## Genre and Music Characteristics
The different attributes that the data set contains can be examined by looking at the co-rrelation between their different combinations. Matplotlib will once again be used to generate a scatterplot for this purpose. The initial step is to assign variables to the values of the attributes so that it would be easy to manipulate the generated scatter-plot:

![{C0E21E19-0A1D-420C-A691-2C8AAE854F9F}](https://github.com/user-attachments/assets/c02765e5-f012-44c7-9e9b-054328b26c8d)

Using Matplotlib, a scatterplot is then generated and formatted as the following. Note that the regression-coefficient was also computed using the .corr() attribute in pandas in order to have a better sense of the graph. This is then repeated for every combination of attributes that are to be tested.

![{34800FC3-756F-43C2-887C-1F25C4A16D3D}](https://github.com/user-attachments/assets/4882d7e5-984d-4b7f-8169-aecca7eb8b05)

Based on the results of the graph, none of the combination of attributes appear to have a significant co-rrelation for a relationship to be established. However, the following should be noted:

### Streams as a Function of BPM
Majority of the most streamed songs on the data-set appear to cluster around between the BPMs of 80 to 140. This suggests that songs with a balance between slow and lively melodies tended to be streamed more.

![{86F7821C-2A64-4055-8B7C-CD967194DBC6}](https://github.com/user-attachments/assets/da74b9cc-a966-4907-8f39-d6928be750a0)

### Streams as a Function of Danceability
The correlation between the number of streams and danceability is the strongest out of all that were tested against the number of streams. The most streamed songs tended to cluster around the danceability percentage of 50 to 90%. This suggests that songs tended to be streamed more if people are able to dance to it.

![{BAB32AA0-DDD3-4D98-84FC-775C9BA578FD}](https://github.com/user-attachments/assets/956f491c-c0fd-4eda-a20b-0970513b262b)

### Streams as a Function of Energy
Songs tended to cluster around the energy percentages of 40% to 90%. This suggests that songs that are perceived to be livelier tended to perform better.

![{8C498A55-4232-4D8B-83CB-E9A1563A244D}](https://github.com/user-attachments/assets/22e657ff-d118-46da-9b82-359170968274)

### Danceability as a Function of Energy
While the regression co-efficient appears to be statistically insignificant, the correlation between danceability and energy was the highest recorded relationship out of all that were tested. Songs with high perceived danceability percentages tended to cluster around the high energy percentages. This suggests that the higher perceived danceability songs are the songs that also tended to be livelier. This may, in turn, suggest that songs that are danceable and lively tended to perform better based on the previous tests for streams vs. danceability or energy.

![{054DBBE3-D34F-46BD-9F9D-C6BC83FF8C06}](https://github.com/user-attachments/assets/2fc4448f-9af0-44ff-b800-3bce7c524e3e)

### Valence as a Function of Acousticness
Based on the results, it is quite difficult to determine the exact relationship between valence and acousticness. However, it should be noted that the songs with less acoustics tended to have a higher valence or positivity in its contents. This suggests that songs become more solemn or sad the more acoustics that are being used.

![{84306FE5-F4EF-44E7-8F39-C2FCC1EEFD94}](https://github.com/user-attachments/assets/47362e7b-fd4f-47a4-a61c-25ae2a3c5282)

## Platform Popularity

## Advanced Analysis

## Conclusion
