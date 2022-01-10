# Python Project: Covid Cases In Ontario Public Schools

<p align="center"><img width="600" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/covidclassroom_1.jpg"></p>


**Project Creation Date**:  *November 2021*

This was a bootcamp project to carry out the entire data analysis process in Python.

The task was to find a promising dataset and to determine a good question to ask of the data.

The objectives were as follows:
- Perform an exploratory analysis
- Generate professional-quality figures
- Produce a high-level overview of the data using aggregation and statistics
- Answer a meaningful question about the dataset in question

<br>

## Dataset

I sourced an [Ontario Public Schools Covid dataset](https://data.ontario.ca/dataset/summary-of-cases-in-schools) from the [Ontario Data website](https://data.ontario.ca/) and specifically studied the Covid data for the 2020-2021 school year.

It contained the date, school name, school ID, school board, municipality and the total confirmed number of cases for each day that schools were open.

**NB: this was before the Omicron variant became the dominant strain in the province.**

Although the dataset was clean and very easy to understand, it was missing additional information that I felt could potentially provide a deeper understanding of how this virus spreads.

I was able to find an [Ontario Schools Enrolment dataset](https://open.canada.ca/data/en/dataset/d89271cf-c5b7-4537-9d8b-5905766d93c6) to provide another dimension to this story and joined both tables together. 

<br>

## Question: Does High Enrolment correlate with Higher Number of Covid Cases in Ontario Schools?
**Hypothesis**:  Yes, high enrolment correlates with higher number of covid cases in Ontario Public Schools simply because the general story at the time was that the virus spreads fast and furious in large crowds of people.

<br>

## Process and Challenges

The covid dataset was very straightforward for the most part.  However, it did not actually provide the total number of cases for each school for the whole school year.  The data was structured by day, so it provided the case counts for each school per day, which means that for each person infected with the virus, they were counted as one case every day until they tested negative.  There is no metadata to confirm this but we can deduce that schools are counting the same infected person on multiple days because the case counts stay consistent for each school for about 10 days straight. We know from experience that covid infections take about 2 weeks to clear the human body.

So the only way to get around this was to use the *MAX number of cases in one day* for each school as the key measure for analysis.  

This is the highest number of case counts in one day for each school in the 2020-2021 school year.  Meaning that if a school's total case count was 1 on one day but 5 on another day, we will only take the 5 cases into account for that school because it is the max that they reported in one day for the school year.

The other challenge was that enrolment data for the 2020-2021 school year was not publicly available so I had to use the enrolment data for the 2019-2020 school year.  It's safe to assume that enrolment numbers stayed fairly consistent for the following year.

<br>

## Answers and Analysis 

**See full Jupyter Notebook [here](https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/Python%20Project%20-%20Covid%20in%20Ontario%20Schools.ipynb)**

**Python libraries used**: *NumPy, Pandas, Seaborn, Matplotlib, Statsmodels*

I thought it was important to first separate and then compare elementary schools and high schools in Ontario in case this differentiation makes a difference in answering our hypothesis.  

The visualization and descriptive statistics below provide a clear breakdown:

<h3 align="center">Number of Elementary Schools and High Schools in Ontario</h3>

<p align="center"><img width="500" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/BarChartOnPrimarySecondarySchools.png"></p>

<h3 align="center">Comparing Mean and Max Enrolment for Elementary and High Schools</h3>  

<p align="center"><img width="1000" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/DescriptiveStatsPrimarySecondarySchools.png"></p>

There are 4 times more elementary schools than high schools in Ontario but average high school enrolment is double the elementary average enrolment. Max enrolment is also double for high schools than elementary.

Then by creating an inner join of the Ontario Schools Covid dataset and the Ontario Schools Enrolment dataset and then creating a scatterplot, the answer to our question is very clear:

<p align="center"><img width="1000" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/Answer-Scatterplot.png"></p>
<p align="center"><img width="650" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/Answer2.png"></p>

There is no correlation between high enrolment and high covid case counts, not even if you break it down by elementary and secondary schools as visualized by the relational plot above.

These graphs show that most schools that had Covid cases had under 10 max cases in one day, regardless of their enrolment size.
The elementary school with the highest enrolment in the province reported only the 2nd highest case count in one day in an elementary school (3rd highest overall if you also take high schools into account). And the school with the highest enrolment overall only had 3 cases as their max in one day.

Meanwhile, extremely high case counts in one day (outliers) are in schools with low, average and high enrolment numbers (the full range).

<br>

## Further Investigation

These graphs show outliers very clearly. Let's see which schools these are

<p align="center"><img width="1000" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/Outliers.png"></p>

The outliers are a mix of elementary and secondary schools and are from different school boards (although the Toronto District School Board appears 6 times in the top 10. But that's because the Toronto District School Board has the most number of schools in the province).

I am still curious about the biggest outlier - Frank W Begley PS, which had 48 cases in one day. 

<p align="center"><img width="700" height="" src="https://github.com/RubyRondina/Python-Project---Covid-Cases-In-Ontario-Schools/blob/main/NotebookAndViz/MapOutlier.png"></p>

Looking at this school on google maps, it is in Windsor, directly across the river from Detroit. You can swim it. This makes me wonder if frequent cross border travel to the US which had surging numbers early in the pandemic, leads to higher risk of infection.

However, none of the neighbouring schools that you can see on the map even show up in the top 10 of our scatterplot.   West view, Holy Rosary School and FJ Brennan Catholic High School each had a max case count of 1.  So there is clearly something more in play here than just enrolment numbers and geographical location of the school.  


### Recommendation and Notes

This dataset is from a time before most of the Ontario population was vaccinated against Covid. Vaccines aside, we should take a multi-faceted approach to battling the spread of this disease.

Our analysis shows that just because a student or staff member is in a school with high enrolment doesn’t necessarily mean they have a higher chance of getting Covid-19. Other factors come into play like masking, hand washing, ventilation systems, types of households students and staff belong to and other social behaviour etc.

I do not recommend shrinking class sizes or school sizes as the one and only solution to protecting students and school staff against covid. We should use a multi-faceted approach.

Last but not least, our method of using the Max Covid case counts in one day per school might not be the best measure of comparison. The study may have been different if we looked at total cases per school for the whole school year, not just each school's highest case count in one day. It just speaks to the limitation of our dataset since cases were reported by day and it is unclear if each count was of a new infected person or the same person with the same infection day after day. It might be worth finding data for total cases per school and comparing it with this study.

That being said, this study was conducted and was based on data from before the more transmittable Omicron variant took hold.  Omicron is a game changer.  It would be useful to do this study again with data from December 2021 when Omicron became the dominant variant and when schools were still open.
