# IGR204: Babynames mini-project

## Visualization 1 (Tableau & Altair)

As we wanted to develop our skills with different tools, we decided to use both Tableau and Altair for this first vizualisation. Now that the the job is completed, it appears that Tableau is much better than Altair at processing large amounts of data, making it much more appropriate for data exploration.  
On the other hand, the bigger flexibility of Altair allows for a nicer dashboard and easier interface between visualization and Pandas pre-processing.

### Tableau version
#### Pre-processing
 
- Departments have been removed from the dataset to speed up data processing.
- Names that appear only once in the dataset have been added to *Rare_Names*.
- All names that appear at least twice in the dataset (ie for two different years) have been dupplicated in order to have one entry (with zero births if the entry is created) every year. This makes the dataset much bigger but was necessary for some Tableau aggregations to work properly.
- The gender information has been added to the name, to avoid confusion in the case of mixed-gender names.

#### Description
First of all, a slider ("Year"), located in the center-right of the dashboard, enables to filter out a specific time range between 1900 and 2020. It applies to all subplots within this dashboard.

In the lower left corner, a **bar plot** displays for each name the **sum of births and the percentage of births** over the filtered time period. Names on this plot are ordered by importance (ie descending sum or births). Two **sliders** ("Name popularity" and "Popularity variability") help exploring the names displayed in this bar plot. These sliders and bar plot combined allow users to answer the following questions :
- Are there names that have consistently remained popular or unpopular?  (using "Name popularity" slider)
- Are there some that have were suddenly or briefl y popular orunpopular ? (using "Popularity variability" slider)

When opening the Dashboard, only 5 names are displayed (names from our group), but a checkox filter based on names, located on the right, allows to select all names and thus fully explore the dataset.

The **temporal evolution** of each name is presented through a **line plot**. We can observe the evolution either in terms of **annual births** or in **percentage of yearly births**.  
The two sliders mentionned above ("Name popularity" and "Popularity variability") unfortunately do not operate on the line plot (the reason for this is that these sliders are based on LOD expressions that are not as easy to manipulate as classic filters).  Consequently, the way to proceed is to start using the sliders with the bar plot and then filter the line plot using a brush on the bar plot.  
A checkbox filter on names, located in the top right corner of the dashboard, enables the user to select the names to be displayed on the line plot. By default, only the names of our group members are selected. Beware, if too many names are displayed on this plot, it becomes unreadable and the amount of data might induce latency. Therefore, it is recommended to always filter out the data for this plot (either with a brush on the bar plot or with the checkbox filter).  
This line plot and filtering tools combined allow users to answer the following questions :
- How do baby names evolve over time?
- Are there trends in time?

In the lower right corner, a line plot is displaying the evolution of the total annual births (all names included) as well as the evolution of the sum of annual births of the selected names only.  
Finally, the total sum of births over the period, aggregated by gender, is displayed just above the previously mentionned line plot.

#### Conclusion
The popularity and variablity sliders are the key features that enable relevant data exploration, thus meeting the homework criteria. Neverthless, user experience could still be improved by linking all subplots and sliders more directly, but we haven't found a way to do so.

### Altair version
#### Pre-processing
Data cleaning was performed on the following fields:
- "Department" feature has been removed
- rows containing "PRENOMS_RARES" for the "preusuel" feature have been deleted
- rows containing "XXXX" for the "annais" feature have been deleted

Additional features was necessary for the data visualization :
- a column with the number of baby names in year N-1 for a given first name has been added
- a column with the rate of change of the number of baby names between years N-1 and N has been added

To avoid confusion in the case of mixed-gender names, the gender information has been added to the name.

#### Description
We recommend selecting less than 10 names for a better readability of the graphs.

The visualization consists of 3 charts : 
- Graph 1 : for each of the selected names, the line plot on the top represents the total number of babies that were given that name each year
- Graph 2 : the bar chart on the bottom left corner shows the year over year change rate on the number of births for a given name. 
- Graph 3 : the bar chart on the bottom right corner displays the cumulative sum of the selected names on a given time frame.

The display can be filtered by selecting a time window (e.g. 1950 - 1970) and/or by selecting a specific name on the interactive legend on the top right corner. 

When a time window is selected on graph 1 or 2, the cumulative sum of the selected names on graph 3 will be automatically updated. 

If the user selects a name on the interactive legend, the year over year change rate for that name will be displayed on graph 2. In addition, the selected name will be highlighted on the line plot  on graph 1 and the bar plot on graph 3.


#### Conclusion

The visualization shows the evolution and the popularity of names over time.

For instance, we display graphs for the following names : Bastien, Clément, Guillaume, Julien and Lucas. 
According to the graph, we can observe :
- Guillaume and Julien were popular names between 1970 and 1995 in comparison with others. These names are unpopular nowadays
- Lucas became a popular name in 90's and remain quite popular nowadays
- Guillaume was suddenly unpopular name in 1997


## Visualization 2 (Altair)

#### Pre-processing
We remove the *Rare_Names*, as well as the unknown ones. We define some functions to group the data by department and to either return the TOP1 name birth count (in percentage of the total for this department for a given year) or the requested name as passed in the corresponding parameter.

#### Description

As we are working with Altair, we allow to directly specify a time period using the `MIN_YEAR` and `MAX_YEAR` variables in the notebook cell. We can also define specific man (`MALE_NAMES`) and woman names (`FEMALE_NAME`) if we want to display them instead of the TOP1 of each department.

The visualization consists of 2 geographic maps of France, one for women names, one for man names. By default, they display the TOP1 name of each department, with additional information in a tooltip when the mouse hovers on a department. We can select the year we want to display by using a drop-down selection menu. The coloration of the map depends on the popularity of the name in the given department (in percentage of the total birth in the department).

#### Conclusion
This visualization allows to see the regional differences in terms of names popularities for both male and female names. It is interactive as we can select specific year as well as specific names.



## Visualization 3 (Altair)

#### Pre-processing
 
First we removed departments, rare firstnames and missing years from the dataset. After we are trying to isolate the first names every year which belongs to a boy and a girl at the same year. The output is like "JOSEPH1900" which mean that in the year 1900 we had some girls called Joseph and boys too.
We render a dataframe sorted by year with every first names and the sum of baby names used both sex.

#### Description
As we can see on the plot, the popularity of baby names used for both boys and girls rised at the end of 1950's. Then we have a sudden drop for like 10 or 20 years.
After that, since 1980, it's increasing a little bit every year. 

#### Conclusion
The initial question was "Does popularity of names given to both sexes evolve consistently", we can provide an answer with the help of the chart. In the past 100 years, we can say that the first 50 years there was a big trend of using the same first name for both boys and girls, and the last 50 years, there was a big drop at the begining but it's growing years after years.
