# IGR204: Babynames mini-project

## Visualization 1 (Tableau)
### Pre-processing
 
Departments have been removed from the dataset to lighten and speed up the table's processing.
Names that appear only once in the dataset have been added to *Rare_Names*.
To clarify browsing, the gender information has been added to the name, to avoid confusion in the case of mixed-gender names.

### Visualization
In the lower left corner, a **bar plot** presents at the same time the **sum of births and the total birth percentage agregated over all years for which the Dashboard is filtered**. This plot helps order names by importance over a giver time period (the names are presented in decreasing order).
Two cursors ("Name popularity" and "Popularity variability") help explore names in this bar plot.
When opening the Dashboard, only 5 names are displayed, but the filter on the right permits to select all names and thus fully use these cursors to explore.

As usual, the **temporal evolution** of each name is presented through a **line plot**. We can observe the evolution either in terms of annual birth count or in percentage of this count.
The two cursors mentionned above unfortunately do not operate on the **line plot**. Thus, it is advised to start using the cursors on the bar plot and then filter the line plot from the bar plot.
In any case, it is possible to filter the line plot through a second filter (Checkbox) in the top right corner.
Beware, if too many names are displayed on this plot, it becomes unreadable. Furthermore, the quantity of data might induce latency. Therefore, it is recommanded to always filter the data for this plot.

Finally, in the lower right corner, a line plot is presenting the total annual births and the annual birth of the selected names. The total count of births over the period and the gender details are displayed to the right of this line plot.

### Conclusion
This visualization enables the user to grasp the importance of names through time thanks to the popularity and variablity metrics. It also helps asses theses names overall *weight* in the dataset thanks to the different bar and line plots. Hence, it answers the assignement criteria.

## Visualization 1 (Altair)
### Pre-processing
Data cleaning was performed on the following fields:
- "Department" feature has been removed
- rows containing "PRENOMS_RARES" for the "preusuel" feature have been deleted
- rows containing "XXXX" for the "annais" feature have been deleted

Additional features was necessary for the data visualization :
- a column with the number of baby names in year N-1 for a given first name has been added
- a column with the rate of change of the number of baby names between years N-1 and N has been added

To avoid confusion in the case of mixed-gender names, the gender information has been added to the name.

### Visualization
Line plot on the top and bar plot in the lower right corner are similar to ones designed on Tableau software. 
A bar chart with both positive and negative values has been created to display the rate of change of the number of baby names as a function of the year. 
On the top right corner, an interactive legend has been added to display graphs only for a specific name.
Besides, a selection of a temporal range on the charts updates values of the bar plot in the lower right corner.

### Conclusion

This visualization enables the user to show the evolution and the popularity of baby names over time. In particular, the chart with the rate of change allows to highlight a sudden evolution of the number of baby names over the time. Hence, it answers the assignment criteria.

## Visualization 2

### Pre-processing
We remove the *Rare_Names*, as well as the unknown ones. We define some functions to group the data by department and to either return the TOP1 name birth count (in percentage of the total for this department for a given year) or the requested name as passed in the corresponding parameter.

### Visualization

As we are working with Altair, we allow to directly specify a time period using the `MIN_YEAR` and `MAX_YEAR` variables in the notebook cell. We can also define specific man (`MALE_NAMES`) and woman names (`FEMALE_NAME`) if we want to display them instead of the TOP1 of each department.

The visualization consists of 2 geographic maps of France, one for women names, one for man names. By default, they display the TOP1 name of each department, with additional information in a tooltip when the mouse hovers on a department. We can select the year we want to display by using a drop-down selection menu. The coloration of the map depends on the popularity of the name in the given department (in percentage of the total birth in the department).

### Conclusion
This visualization allows to see the regional differences in terms of names popularities for both male and female names. It is interactive as we can select specific year as well as specific names.



## Visualization 3

### Pre-processing
 
First we removed departments, rare firstnames and missing years from the dataset. After we are trying to isolate the first names every year which belongs to a boy and a girl at the same year. The output is like "JOSEPH1900" which mean that in the year 1900 we had some girls called Joseph and boys too.
We render a dataframe sorted by year with every first names and the sum of baby names used both sex.

### Visualization
As we can see on the plot, the popularity of baby names used for both boys and girls rised at the end of 1950's. Then we have a sudden drop for like 10 or 20 years.
After that, since 1980, it's increasing a little bit every year. 

### Conclusion
The initial question was "Does popularity of names given to both sexes evolve consistently", we can provide an answer with the help of the chart. In the past 100 years, we can say that the first 50 years there was a big trend of using the same first name for both boys and girls, and the last 50 years, there was a big drop at the begining but it's growing years after years.
