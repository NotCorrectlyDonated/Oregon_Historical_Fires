# Oregon_Historical_Fires

The aim of this exploratory analysis is to comprehend the situation among human-made fires occurring in the state of Oregon and to get some insights into 2 topics:

Locations where fires are more common to be spread. \
Types of fields that may have an increment to have fires over the years

This exploratory analysis was fully made in ``python`` language in a ``JupyterNotebook``

## Dataset and Libraries used

The dataset was provided by kaggle and can be seen [here](https://www.kaggle.com/datasets/mattop/fire-occurrence-and-cause-data-2000-2022). In order to correctly address the data, the following libraries were imported.

``pandas``: As the main library to handle, organize and group data. \
``plotly``: Visualization library [^1] [^2]

[^1]: I will use ``pio`` plotly extension to render flat images into GitHub,  
[^2]: To build animate graphs and locate them, I will use plotly MapBox extension, to have an immersive analysis, a token will be needed.


## Data Used

For this analysis, I will be using the following columns as I felt they provided sufficient information for my research, the rest of the columns can be seen at this Kaggle [link](https://www.kaggle.com/datasets/mattop/fire-occurrence-and-cause-data-2000-2022).

`SERIAL`: As a fire identification (``int``) \
`DistrictName`: Regional indicator where the fire was located (``str``) \
`FireYear`: Year when the fire was set (``int``) \
`SizeClass`: Categorical column referring to the size of burned acres. (``str``) \
`EstTotalAcres`: Total acres burned estimation (``float``) \
`GeneralCause`: Matter of the fire (``str``)\
`Lat_DD','Long_DD'`: Exact location of the fire (``float``) \
`FO_LandOwnType`: Owner of the fire origin (``str``) \
`Ign_DateTime`: Date when the fire was set (``str``) \
`Control_DateTime`: Date when the fire was controlled (``str``) \

## Data Proccessing
### Handling Null values

After selecting the columns used for the research, we were left with 11 columns and 23490 entries for my analysis.

Checking whether the dataset contained null values, there where seen that 100 rows contained null values in any of the columns, since the number of null rows is less than 0,5% of the entries in the dataset, I got rid of them I presume it won't make an impact in our analysis. 


### Datetime conversion
 
Having a look at the types of data in the columns, we can find that the columns `Ign_DateTime` and `Control_DateTime` are not recognizable as dates in our dataset, for this reason, we will convert them into ``datetime`` class, and transform them to show the month and year where the fire was made.

After these 2 processes, the dataset is ready to extract information

## Getting Insights

As the main aim of the project is to look for human-made fires, we will have a look at the unique values of the column "GeneralCause", showing the following values: 'Lightning', 'Smoking', 'Recreation', 'Debris Burning',
       'Equipment Use', 'Miscellaneous', 'Arson', 'Under Invest',
       'Juveniles', 'Railroad'.
       
Since all of the values shown except "Lightning" are directly or indirectly caused by humans, we will get rid of the Lighting entries contained in this column.

### Evolution of the size of fires over years

For this process, a `groupby` function was done to count the number of fires depending on the `Size_class` and `FireYear` columns, to then show them in a line chart.

![img1](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/img1.PNG)

We can observe how low-size fires "A" have increased over the years since 2010, "B" class showed a steady frequency over the years.


In order to show data in a more clear way, a new dataframe was made to show fires ranked from C above.

![img2](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/img2.PNG)


We can observe an increase in the number of fires which are more dangerous (ranked "E" and above) since 2015.

### Total Acres per District

When grouping our dataset into the quantity of acres burned per district, the following bar chart is shown


![img3](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/img3.PNG)


As previously mentioned, we can see how from 2015, there was an increase in the number of dangerous fires, being reflected in the number of acres burned. In the year 2020, we find out the most quantity of acres burned, having more than 8 times more acres burned, further studies are needed if a possible correlation between these events with the Covid-19 pandemic is to be verified..

The most affected districts where North & South Cascade and Southwest Oregon.


### Land Owners & Fires

Since some of the fires may be caused intentionally for personal interest reasons, grouping between the number of fires and the type of the owners was made, having the following result.


![img4](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/img4.PNG)


There were not many variations among the different types of land but in 2021, where it is seen a huge outlier referring to Private and BLM properties. Further investigations need to be made to see the origin of these outliers and if it also could be as a response to the Covid-19 pandemic. 


### Fires Located using Mapbox

In order to correctly see the graphs, we will need an account in plotly mapbox, as a token is needed to process this kind of graph, more information is shown [here](https://plotly.com/chart-studio-help/make-a-mapbox-map/). \
Screenshots will be attached to have a preview of the work done.

The first graph shows all the fires located in the state of Oregon with size class badges:

![img4](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/all_fires.PNG)

Analyzing the locations where the fires had occurred, we can observe that most of them were in the West part of the state, (The Cascade Range and Grass Pass) in natural areas. 

![img4](https://github.com/NotCorrectlyDonated/Oregon_Historical_Fires/blob/main/data/danger_fires.PNG)

When analyzing high-size fires, which are the critical part of this study, we can state that most dangerous fires are covered in the inside of these woods, which gives us a hint that these regions may be lacking firewalls to prevent these fires to occur in these difficult accessible lands..

       
#### Fires per year.

Mapbox extension also allow us to see chronologically when the fires have occurred, showing the following graph





https://user-images.githubusercontent.com/110167165/224986529-bd9177c5-5215-4003-8940-319ec1a7cda1.mp4



