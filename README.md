# Oregon_Historical_Fires

The aim of this exploratory analysis is to comprehend the situation among human-made fires ocurring in the state of Oregon and to get some insights around 2 topics:

Locations where fires are more common to be spread
Types of fields that may have an increment to have fires over the years

This exploratory analysis was fully made in python language

## Dataset and Libraries used

The dataset was provided by kaggle and can be seen [here](https://www.kaggle.com/datasets/mattop/fire-occurrence-and-cause-data-2000-2022). In order to correctly address the data, the following libraries were imported.

``pandas``: As the main library to handle, organise and group data. \
``plotly``: Visualization library [^1] [^2]

[^1]: We will use ``pio`` plotly extension to render flat images into GitHub,  
[^2]: To build animate graphs and locate them, we will use plotly MapBox extension, to have an inmersive analysis, a token will be needed.


## Data Used

For this analysis, I will be using the following columns as I felt it provided the sufficient information for my analysis, the rest of the columns can be seen at this kaggle [link](https://www.kaggle.com/datasets/mattop/fire-occurrence-and-cause-data-2000-2022).

`SERIAL`: As a fire indentificator (``int``) \
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

After selecting the columns used for the research, we were leflt with 11 columns and 23490 entries for our analysis.

Checking whether the dataset contained null values, there where seen that 100 rows contained null values in any of the columns, since the amount of null rows are less than 0,5% of the entries in the dataset, I got rid of them I pressume it won't make an impact in our analysis. 


### Datetime conversion
 
Having a look at the types of data in the columns, we can find that the columns `Ign_DateTime` and `Control_DateTime` are not recognizable as dates in our dataset, for this reason, we will convert them into ``datetime`` class, and transform them just to show the month and year where the fire was made.

After these 2 processes the dataset is ready to extract information

## Getting Insights

As the main aim of the project is to look fore human-made fires, we will have a look at the unique values of the column "GeneralCause", showing the following values: 'Lightning', 'Smoking', 'Recreation', 'Debris Burning',
       'Equipment Use', 'Miscellaneous', 'Arson', 'Under Invest',
       'Juveniles', 'Railroad'.
       
Since all of the values showes except "Lightning" are directly or indirectly caused by humans, we will get rid of the Lighting entries contained in this column.

### Evolution of the size of fires over years

For this process we will simply do a (groupby) function that counts the number of fires depending on the (Size_class) and (FireYear) to then transform it into a new dataset and show it in a line chart.

(IMAGEN 1)

We can observe how low-size fires "A" have an increise over the years since 2010, whether "B" class showed an steady frecuency over the years.


In order to show data in a more clear way, a new dataframe was made just to show fires ranked from C above.

(IMAGEN 2)


We can observe an increase in the number of fires which are more dangerous (ranked "E" and above) since 2015.

### Total Acres per District

When grouping our dataset into the quantity of acres burned per district, the following bar graph shows


(IMAGEN 3)


As previously mention, we can see how from 2015, there was an increase in the number of dangerous fires, being reflected in the number of acres burned. In the year 2020 we find out the most quantity of acres burned, having more than 8 times more acres burned, further studies have to be made if there was a correlation with the Covid-19 pandemic.

The most affected districs where North & South Cascade and Southwest Oregon.


### Land Owners & Fires

Since some of the fires may be caused intentionally for personal interest reasons, grouping between the number of fires and the type of the owners was made, having the following result.


(IMAGEN 4)


There were not many variations among the different types of land but in 2021, where it is seen a huge outliers referring to Private and BLM properties. Further investigations need to be made to see the origin of these outliers and if it also could be as a response to the Covid-19 pandemic. 


### Fires Located using Mapbox

In order to correctly see the graphs, we will need an account in plotly mapbox, as a token is needed to proccess this kind of graphs, more information is shown (HERE).
Screenshots will be attached to have a preview of the work done.

The first graph shows all the fires located in the state of Oregon with size class badge:

(ALL LOCATIONS PHYSICAL IMG)

Analyzing the locations where the fires had occurred, we can observe that most of them where in the West part of the state, (Cascade Range and Grass Pass) in natural areas. 

(danger fires)

When analyzing high size fires, which are the critical part of this study, we can state that most dangerous fires are covered in the inside of this woods, which gives us a hint that these regions may be lacking firewalls to prevent these fires to occur in this difficult accesible lands.

       
#### Fires per year.

Mapbox extension also allow us to see chronologically when the fires have occured, showing the following graph





https://user-images.githubusercontent.com/110167165/224986529-bd9177c5-5215-4003-8940-319ec1a7cda1.mp4



