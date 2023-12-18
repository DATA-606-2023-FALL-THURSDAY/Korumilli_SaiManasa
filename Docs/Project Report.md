# Title and Author

- **Project Title**: Crime Report Analysis and Status Prediction - Los Angeles City
- **Prepared for UMBC Data Science Master Degree Capstone by**: Dr. Chaojie (Jay) Wang
- **Author**: Sai Manasa Korumilli
- **Semester** : Fall 2023
- **Link to the author's GitHub profile**: [GitHub Profile](https://github.com/SaiManasaK1508)
- **Link to the author's LinkedIn profile**: [LinkedIn Profile](https://www.linkedin.com/in/saimanasa-korumilli/)
- **Link to PowerPoint presentation file**: [Powerpoint Presentation](https://1drv.ms/p/s!AsYJIXOWnLxRhh5cZuR6VIl1qp42?e=fwq41M&nav=eyJzSWQiOjI5MiwiY0lkIjozODk4NDQ3OTI5fQ)
- **Link to Youtube Video**: [youtube video](https://youtu.be/TH2mwLp2piQ)
# Background

Los Angeles, often referred to as LA, is a vibrant and diverse city located in Southern California, USA, Los Angeles boasts a thriving cultural scene, a bustling economy, and stunning natural beauty, with picturesque beaches and mountains. However, LA faces challenges like traffic congestion, high living costs, income inequality, and crime rates. Crime rates have varied over the years, with some areas experiencing higher levels of criminal activity, particularly property crimes and gang-related incidents. This dataset presents a comprehensive record of criminal incidents within the City of Los Angeles between 2010 and 2019. 

As Crime is a pervasive concern impacting communities, cities, and nations globally, gaining insights into crime patterns and trends is of utmost importance for law enforcement agencies, policymakers, and communities to craft effective strategies for crime prevention and response. Analyzing historical crime data allows for a deeper understanding of how criminal activities have evolved over the specified decade. The years from 2010 to 2019 are especially noteworthy for studying crime trends, given the societal and technological shifts that occurred during this period.

# Project objective

1. To Analyse the trends in overall crimes during the decade. <br>

2. To develop a machine learning model that predicts the status of future crimes taking relevant factors into consideration.
   
# Research Questions


1. Which specific crime categories showed the most significant changes in prevalence over the study period?

2. Are there geographical hotspots for crime, and do these locations remain consistent over time?

3. How do demographic factors, such as age, gender effect the crime?


# Data

- Each row represents a crime record in Los Angeles City for 10 years from 2010 -2019
- Source: Data is provided by the Los Angeles Police Department 
- Data Link: [Dataset](https://data.lacity.org/Public-Safety/Crime-Data-from-2010-to-2019/63jg-8b9z)
- Data Size: 515 MB
- Data Shape: Number of rows: 2135598, Number of columns: 28
  

  #  Data Description 

-  **DR_NO** - int64 - Division of Records Number: Official file number made up of a 2-digit year, area ID, and 5-digit
- **Date Rptd** - object - MM/DD/YYYY
- **DATE OCC** - object - MM/DD/YYYY
- **TIME OCC** - int64 - In 24-hour military time
- **AREA** - int64 - The LAPD has 21 Community Police Stations referred to as Geographic Areas within the department. These Geographic Areas are sequentially numbered from 1-21            
- **AREA NAME** - object - The 21 Geographic Areas or Patrol Divisions are also given a name designation that references a landmark or the surrounding community that it is responsible for. For example, 77th Street Division is located at the intersection of South Broadway and 77th Street, serving neighborhoods in South Los Angeles
- **Rpt Dist No** - int64 -  A four-digit code that represents a sub-area within a Geographic Area. All crime records reference the "RD" that it occurred in for statistical comparisons. Find LAPD Reporting Districts on the LA City GeoHub at http://geohub.lacity.org/datasets/c4f83909b81d4786aa8ba8a7 
- **Part 1-2** - int64  
- **Crm Cd** - int64 -  Indicates the crime committed. (Same as Crime Code 1) 
- **Crm Cd Desc** - object - Defines the Crime Code provided
- **Mocodes - object** -  Activities associated with the suspect in the commission of the crime. See the attached PDF for a list of MO Codes in numerical order. https://data.lacity.org/api/views/y8tr-7khq/files/3a967fbd-f210-4857-bc52-60230efe256c?download=true&filename=MO%20CODES%20(numerical%20order).pdf
- **Vict Age** - int64 - Two-character numeric  
- **Vict Sex** - object - F - Female M - Male X - Unknown 
- **Vict Descent** - object - A - Other Asian B - Black C - Chinese D - Cambodian F - Filipino G - Guamanian H - Hispanic/Latin/Mexican I - American Indian/Alaskan Native J - Japanese K - Korean L - Laotian O - Other P - Pacific Islander S - Samoan U - Hawaiian V - Vietnamese W - White X - Unknown Z - Asian Indian
- **Premis Cd** - float64 - The type of structure, vehicle, or location where the crime took place
- **Premis Desc** - object - Defines the Premise Code provided
- **Weapon Used Cd** - float64 - The type of weapon used in the crime.
- **Weapon Desc** - object -  Defines the Weapon Used Code provided
- **Status** - object - Status of the case. (IC is the default)
- **Status Desc** - object - Defines the Status Code provided
- **Crm Cd 1** - float64 - Indicates the crime committed. Crime Code 1 is the primary and most serious one. Crime Codes 2, 3, and 4 are respectively less serious offenses. Lower crime class numbers are more serious
- **Crm Cd 2** - float64 - May contain a code for an additional crime, less serious than Crime Code 1
- **Crm Cd 3** - float64 - May contain a code for an additional crime, less serious than Crime Code 1
- **Crm Cd 4**- float64 - May contain a code for an additional crime, less serious than Crime Code 1
- **LOCATION** - object - The street address of the crime incident rounded to the nearest hundred block to maintain anonymity
- **Cross Street** - object - Cross Street of rounded Address
- **LAT** - float64 -  Latitude
- **LON** - float64 - Longitude
  
# Target Variable and Predictors
Through this analysis, I am trying to predict the status of future crimes that will occur in LA <br>

**Target variable for the ML Model** - Status Desc (Mapped) <br>
**Features** - Weapon Used Cd, Weapon Desc, Vict Descent, Vict Sex, AREA NAME, Vict Age

# Exploratory Data Analysis

### Data Cleaning and Pre-processing

**Removing the Duplicates** - Checking the duplicates in the data set, there are no duplicates present in the data.

**Removing the similar columns** - Columns such as 'Mocodes', 'Crm Cd 1', 'Crm Cd 2', 'Crm Cd 3', 'Crm Cd 4', ' Part 1-2' represents similar information of 'Crm cd'. The columns 'Rpt Dist No' and 'Cross street' are not of much necessary information, therefore these were removed.

**Replacing the null values** - As the other columns contain important information that is helpful for the ML model, instead of dropping the rows of the null values, I have replaced them with 'Unknown' values.

### Analysing and Visualization of Data

**Crimes according to the crime categories**
 <img width="1000" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/crime%20category.png">

Top crime categories are Battery - Simple assault, Stolen Vehicles, Burglary from vehicles and Theft

**Most affected areas**

<img width="1000" alt="image" src= "https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/area.png">

The top most effected area is 77th street in LA followed by Southwest and Southeast.

**Crimes according to the gender**


<img width="1000" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/gender.png">

We can draw the conclusion as the crimes happening with male are comparatively higher than the female

**Mapping of locations using latitutes and longitudes**

<img width="1000" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/crimes-area.png">


<img width="1000" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/location-no.of%20crimes.png">

We can see the number of crimes in each locations

**Premis wise crimes**

<img width="600" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/premis.png">

Streets are where most crimes are happening, even the parking lot is not safe according to the visualization

# Machine Learning Models

<img width="600" height="500" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/mapped%20status.png">

<img width="1000" height="400" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/balanced%20data.png">


<img width="700" height="500" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/ml%20model%20comparision.png">


<img width="700" height="500" alt="image" src="https://github.com/DATA-606-2023-FALL-THURSDAY/Korumilli_SaiManasa/blob/main/Images/roc%20comparision.png">



