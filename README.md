# Exploratory Data Analysis on Spotify 2023 Dataset
by: Christian Kyle S. Antonio | 2-ECE-C

Table of Contents:

- [About the Project](#about-the-project)
- [General Overview](#general-overview)
- [Top Performers](#top-performers)
   - [Summary](#in-summary)
- [Basic Descriptive Statistics](#basic-descriptive-statistics)
  
## About the Project
In this project, a data set containing various information on the top songs on Spotify for the year 2023 is given from a database website, Kaggle.com. This documentation will show the various findings after the dataset has been applied with basic statistical treatment and data visualization tools using Python.


*Raw data set preview:*

![{80FDEC63-C110-4F95-9497-B86D98282739}](https://github.com/user-attachments/assets/d2ea4766-fac9-4d42-bc58-fd2700737e2b)

### Libraries Used
* Pandas
* Matplotlib

## General Overview
To initialize the project, it important to first examine the data set that is provided. Using the attribute ".info()" that is included in the Pandas library, we are able to get some information regarding the characteristics of the data set.

From the image below, we can see that there are over **953 rows** and **24 columns** with every column primarily containing string (or object) and integer values. Each row corresponds to a specific track while the column corresponds to various information types for every row.

*.info() output of the given data set:*

![{4ADC5569-2A7A-4D58-BA13-C8066CFA97F6}](https://github.com/user-attachments/assets/f6be3559-c2ea-4ee7-99ea-ca857d1c8fd2)


Upon observing the information on the data set further, we can notice that there are two columns that have a non-null count less than that of the total number of tracks. This indicates that in these columns, there are tracks with missing values. To be precise, there are **85 missing key values** and **50 missing in_shazam_charts values**.

![{59672547-AEC8-490F-92A7-FE9B5CDE4020}](https://github.com/user-attachments/assets/18f63ba1-9a7c-415e-b4c7-1885275ba395)
![{C0700D8C-65F3-42E2-9B3C-35C7AD51323B}](https://github.com/user-attachments/assets/fd70971d-dfb3-4ac9-b3b8-6a326de1e969)


## Top Performers
The most logical first step in analyzing this dataset would therefore be to sort the track by the number of streams in descending order using the ".sort_values()" attribute in Pandas. However a problem arises as one of the tracks appears to have a non-numeric value and as such appears to be on top of the list. 

![{1DB0669F-23B3-4FC7-9C2E-A006970517C5}](https://github.com/user-attachments/assets/e13c86df-949d-4dad-b11f-ee74c1b7d270)

Additionally, when observing the sorted list, the supposed top five tracks have less streams than one of the song in the bottom five tracks. Referring back to .info() output of the data set, we can see that this column is, in fact, in string data-type format as opposed to a numeric data-type like an integer or floating point thus it may be the cause of this problem.

![{8575405C-B485-4EE4-89D7-FE3363C7A9F5}](https://github.com/user-attachments/assets/c41e3c07-df16-4d75-b2ed-964c003edc6a)

To fix these inconsistencies, a numeric value in string data-type for the problem track must first be assigned. In this case, it shall be assigned to 0 as it is effectively unknown in the context of this data set and doing so will place it at the bottom when the set is sorted by the number of streams.

![{78F5BE98-5C74-42CD-9F60-98AB1CC81C1D}](https://github.com/user-attachments/assets/a729b33c-7fe1-48e8-bc58-4c690782c1a0)

Then, the values for the streams column must be converted to a numeric data-type in order for it to be accurately sorted. Initially, using an integer data type will yield the following error:

![{056ADE63-63A0-4FDE-B558-F95A3B5453B9}](https://github.com/user-attachments/assets/09ebdccc-a99f-4306-96c4-cb16e0bbc48f)

This may potentially be because of how large the numeric values of the strings to be converted in the streams column therefore floating point data-type is more appropriate.

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

![{31DD6ECA-EB2A-4B20-9839-64603F56FBBA}](https://github.com/user-attachments/assets/21749674-7db0-4487-969f-9072f330b796)

The output is then printed and the results came out as: 

![{31DDA72A-11F2-471F-AFDE-74ECA666C774}](https://github.com/user-attachments/assets/b61cf148-f3df-4a7b-bb09-14091f47ab96)

From the results above, it was determined that the approximate values of the basic descriptive statistics of the stream count were:
- **Mean**: 513.60 million
- **Median**: 290.23 million
- **Standard Deviation:** 566.80 million


