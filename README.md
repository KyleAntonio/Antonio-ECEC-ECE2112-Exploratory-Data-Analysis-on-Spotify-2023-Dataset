# Exploratory Data Analysis on Spotify 2023 Dataset
by: Christian Kyle S. Antonio | 2-ECE-C

Table of Contents:

- [About the Project](#about-the-project)
- [General Overview](#general-overview)
- [Top Performers & Basic Descriptive Statistics](#top-performers-&-basic-descriptive-statistics)
  
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

![{A73384C0-0D59-4996-8315-1456465D658F}](https://github.com/user-attachments/assets/903a170d-e1a2-4bd1-a964-3b9dc4a82e4e)

Upon observing the information on the data set further, we can notice that there are two columns that have a non-null count less than that of the total number of tracks. This indicates that in these columns, there are tracks with missing values. To be precise, there are **85 missing key values** and **50 missing in_shazam_charts values**.

![{59672547-AEC8-490F-92A7-FE9B5CDE4020}](https://github.com/user-attachments/assets/18f63ba1-9a7c-415e-b4c7-1885275ba395)
![{C0700D8C-65F3-42E2-9B3C-35C7AD51323B}](https://github.com/user-attachments/assets/fd70971d-dfb3-4ac9-b3b8-6a326de1e969)


## Top Performers & Basic Descriptive Statistics
The most logical first step in analyzing this dataset would therefore be to sort the track by the number of streams in descending order using the ".sort_values()" attribute in Pandas. However a problem arises as one of the tracks appears to have a non-numeric value and as such appears to be on top of the list. 

![{1DB0669F-23B3-4FC7-9C2E-A006970517C5}](https://github.com/user-attachments/assets/e13c86df-949d-4dad-b11f-ee74c1b7d270)

Referring back to the data type info in the previous section, we can see that the streams column is assigned string values as opposed to integer values which one would might assume for this situation. For the purpose of analyzing the data in later sections, it is vital that this is to be converted to numeric values and for the erroneous data to be replaced with a corresponding numeric value, which in this case, 0 as it is difficult to determine the real value without compromising the entire datset.
