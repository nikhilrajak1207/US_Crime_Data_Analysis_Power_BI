# US Crime Data Analysis (1980-2014) - Power BI Report
This Power BI report presents an analysis of US crime data from 1980 to 2014. It provides valuable insights into crime trends across various states and cities, including crime rates by gender, relationship, and weapon types.

# Key Features
KPIs:

Total Crime Incidents: 638.45k
Solved Crime Rate: 70.2%
Crime Incidents Involving Women: 22.45%
Average Victim Age: 35 years

# Slicers:

Year
State

# Visualizations:

% of Crime Incidents by State: Highlights the states with the highest crime rates, with California accounting for 15.63% of total incidents.
Top 10 Cities by Crime: Displays the cities with the highest crime rates, with Los Angeles topping the list at 23%.
Total Crime Incidents by Relationship: Shows that the "Unknown" relationship category accounts for the highest number of crimes (273k).
Crime Incidents by Perpetrator Gender: Reveals that 89% of crimes were committed by male perpetrators.
Crime Incidents by Weapon Type: Highlights that handguns were used in the highest number of crimes.
Data Cleaning and Transformation
Before importing the data into Power BI, Power Query Editor was used to clean and transform the raw crime data. The data was processed to handle missing values, remove duplicates, and ensure consistency across the dataset, making it ready for accurate analysis and reporting.

# DAX Functions Used
The following DAX functions were utilized to calculate various metrics:

1. Total Crime Incidents
To calculate the total number of crime incidents:

Total Crime Incidents = 
SUM(CrimeData[Crime Count])
2. Solved Crime Rate
To calculate the solved crime rate:

Solved Crime Rate = 
DIVIDE(
    SUM(CrimeData[Solved Crimes]),
    SUM(CrimeData[Crime Count]),
    0
) * 100
Explanation: This formula divides the sum of solved crimes by the total number of crimes to get the percentage of solved crimes.
3. Crime Incidents Involving Women
To calculate the percentage of crimes involving women:

Crime with Women = 
DIVIDE(
    SUM(CrimeData[Crime Count Women]),
    SUM(CrimeData[Crime Count]),
    0
) * 100
Explanation: This formula calculates the percentage of crimes involving women by dividing the number of crimes involving women by the total number of crimes.
4. Average Victim Age
To calculate the average age of victims:

Average Victim Age = 
AVERAGE(CrimeData[Victim Age])
5. Crime Incidents by State
To calculate the percentage of crime incidents by state:

Crime % by State = 
DIVIDE(
    SUM(CrimeData[Crime Count]),
    CALCULATE(SUM(CrimeData[Crime Count]), ALL(CrimeData[State])),
    0
) * 100
Explanation: This formula calculates the percentage of crime incidents by state relative to the total incidents across all states.
6. Top 10 Cities by Crime
To calculate the top 10 cities by crime:

Top 10 Cities by Crime = 
RANKX(
    ALL(CrimeData[City]),
    SUM(CrimeData[Crime Count]),
    ,
    DESC
)
7. Crime Incidents by Relationship
To calculate the total number of crimes by relationship:

Crime by Relationship = 
CALCULATE(
    SUM(CrimeData[Crime Count]),
    CrimeData[Relationship] = "Unknown"
)
8. Crime Incidents by Perpetrator Gender
To calculate the percentage of crimes committed by male perpetrators:

Crime by Men = 
DIVIDE(
    SUM(CrimeData[Crime Count Men]),
    SUM(CrimeData[Crime Count]),
    0
) * 100
9. Crime Incidents by Weapon Type
To calculate the crime incidents committed by handguns:

Crime by Handgun = 
CALCULATE(
    SUM(CrimeData[Crime Count]),
    CrimeData[Weapon Type] = "Handgun"
)
Data
The report uses crime data from 1980 to 2014, with key fields such as Crime Count, Crime Type, City, State, Perpetrator Gender, Weapon Type, Victim Age, and Relationship among others.

Getting Started
Clone this repository or download the Power BI (.pbix) file.
Open the file in Power BI Desktop.
Use the slicers for year and state to explore crime trends in the US.
Prerequisites
Power BI Desktop (latest version recommended)
US Crime Dataset (included in the report)
Usage
This report is designed for law enforcement agencies, analysts, or anyone looking to gain insights into crime patterns across the US. It can be used to identify trends, inform policy decisions, and improve community safety.
