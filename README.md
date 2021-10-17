# PyBer_Analysis
## Overview of the analysis:
The purpose of the pyber analysis is to create a summary DataFrame of the ride-sharing data by city type And create a multiple-line graph that shows the total weekly fares for each city type.For getting this,I will work with two csv file,city_data.csv and ride_data.csv.I will load and read that files and make two dataframe.Then i will merge both dataframe and make new one to do my pyber analysis.With the help of dataframes I will write code and get results.Using the Pandas groupby() function with the count() and sum() methods on PyBer DataFrame columns,I will get the total number of rides, total number of drivers, and the total fares for each city type. Then, I will calculate the average fare per ride and average fare per driver for each city type.At last add this data to a new DataFrame and create a summary DataFrame.Using function pivot() and resample(),i will make a new dataframe and then i will create a multiple-line graph with that dataframe that shows the total fares for each week by city type.


### Results:
* For getting the total rides for each city type,I used pandas groupby function on city type and count() method on ride_id column. And for getting the total drivers for each city type I again used groupby function on city type and sum() method on driver_count column.And for  the total amount of fares for each city type,I used groupby function on city type and sum method on fare column.After getting these three results,I calculated for average fare per ride and average fare per driver for each city type.For average fare per ride for each city type,I divided the sum of all the fares by the total rides.And for the average fare per driver for each city type, I divided the sum of all the fares by the total drivers.Finally, add this data to a new DataFrame,delete the index of this dataframe and at last i formatted the columns and get a new formatted pyber summary DataFrame.

* **My formatted Pyber summary DataFrame is look like this:**
![image](https://user-images.githubusercontent.com/90277142/137607708-f727b03c-e98e-4b3d-9f0c-363a9855303f.png)


* I created a new DataFrame from pyber_data_df dataframe with multiple indices using the groupby() function on the "type" and "date" columns, then apply the sum() method on the "fare" column to get the total fare amount for each date.After that i Reset the index on the DataFrame that i was created because This is needed to use the 'pivot()' function.Generalization of pivot that can handle duplicate values for one index only. After resetting the index, I created a pivot table with the 'date' as the index, the columns ='type', and values='fare' to get the total fares for each type of city by the date..This is my code for pivot table : 
**type_date_sumfare_pivot = type_date_sumfare_df.pivot(values='fare' , index='date', columns='type')** 

* **My Pivot table looks like this:**
![pivot](https://user-images.githubusercontent.com/90277142/137608429-a9489b53-d15d-441d-a7a0-e4206fa7a143.png)


* After creating pivot, I Created a new DataFrame from the pivot table DataFrame using loc on the given dates, '2019-01-01':'2019-04-29'.Next I Set the "date" index to datetime datatype.Because this is necessary to use the resample() method .Then I Created a new DataFrame using the "resample()" function by week 'W' and get the sum of the fares for each week.This is my code of resample() function that i used on my pivot dataframe : type_date_sumfare_Week = **type_date_sumfare_pivot.resample("W").sum()**

* **After creating the resampled DataFrame,My DataFrame looks like this:
![image](https://user-images.githubusercontent.com/90277142/137608740-075af994-e082-448c-bae9-c57c1e9c8d0d.png)


* Finally,I plotted the graph of resampled DataFrame using the object-oriented interface method and the df.plot() method, as well as the Matplotlib "fivethirtyeight" graph style code snippet was provided in the starter code.I Annotated the y-axis label and the title, then I used the appropriate code to save the figure as PyBer_fare_summary.png in your "analysis" folder.

* **My multiple-line chart looks like the following image, where each week is a peak or dip in the line graphs.**
![PyBer_fare_summary](https://user-images.githubusercontent.com/90277142/137608956-26631aa2-c05a-4e96-a667-bb91a6a1520b.png)

     
#### Summary:
Based on the results, provide three business recommendations to the CEO for addressing any disparities(a great difference) among the city types.There is a statement summarizing three business recommendations to the CEO for addressing any disparities among the city types. (4 pt)Finally, you’ll submit a written report that summarizes how the data differs by city type and how those differences can be used by decision-makers at PyBer.
