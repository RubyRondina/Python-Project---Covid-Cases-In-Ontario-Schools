{\rtf1\ansi\ansicpg1252\cocoartf2580
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;\f1\fnil\fcharset0 HelveticaNeue;\f2\fnil\fcharset0 Menlo-Regular;
}
{\colortbl;\red255\green255\blue255;\red0\green0\blue0;\red39\green106\blue180;\red27\green31\blue35;
\red255\green255\blue255;}
{\*\expandedcolortbl;;\cssrgb\c0\c0\c0\c87059;\cssrgb\c18824\c49804\c75686;\cssrgb\c14118\c16078\c18431;
\cssrgb\c100000\c100000\c100000;}
\margl1440\margr1440\vieww11520\viewh13600\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Python Project: Covid Cases In Ontario Public Schools\
\
![HeaderImage]()\
\
**Project Creation Date**:  *November 2021*\
\
This was a bootcamp project to carry out the entire data analysis process in Python.\
\
The task was to find a promising dataset and to determine a good question to ask of the data.\
\
The objectives were as follows:\
- Perform an exploratory analysis\
- Generate professional-quality figures\
- Produce a high-level overview of the data using aggregation and statistics\
- Answer a meaningful question about the dataset in question\
\
<br>\
\
***Dataset\
\
I sourced an [Ontario Public Schools Covid dataset](https://data.ontario.ca/dataset/summary-of-cases-in-schools) from the [Ontario Data website](https://data.ontario.ca/) and specifically studied the Covid data for the 2020-2021 school year.\
\
**NB: this was before the Omicron variant became the dominant strain in the province.**\
\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 It contained the date, school name, school ID, school board, municipality and the total confirmed number of cases for each day that schools were open.\
\
Although the dataset was clean and very easy to understand, it was missing additional information that I felt could potentially provide a deeper understanding of how this virus spreads.\
\
So I was able to find an [Ontario Schools Enrolment dataset](https://open.canada.ca/data/en/dataset/d89271cf-c5b7-4537-9d8b-5905766d93c6) to provide another dimension to this story and joined both tables together. \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 <br>\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 ***Question: \cf2 \expnd0\expndtw0\kerning0
Does High Enrolment correlate with Higher Number of Covid Cases in Ontario Schools?\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \kerning1\expnd0\expndtw0 \
**Hypothesis**:  Yes, h\cf2 \expnd0\expndtw0\kerning0
igh enrolment correlates with higher number of covid cases in Ontario Public Schools simply because the general story at the time was that the virus spreads fast and furious in large crowds of people.\
\cf0 \kerning1\expnd0\expndtw0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 <br>\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \
***Process and Challenges\
\
The covid dataset was very straightforward for the most part.  However, it did not actually provide the total number of cases for each school for the whole school year.  The data was structured by day, so it provided the case counts for each school per day, which means that for each person infected with the virus, they were counted as one case every day until they tested negative.  There is no metadata to confirm this but
\f1\fs28 \cf2 \expnd0\expndtw0\kerning0
 we can deduce that schools are counting the same infected person on multiple days because the case counts stay consistent for each school for about 10 days straight. We know from experience that covid infections take about 2 weeks to clear the human body.\
\
\pard\pardeftab720\sa280\partightenfactor0

\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 So the only way to get around this was to use the *MAX number of cases in one day* for each school as the key measure for analysis.  
\f1\fs28 \cf2 \expnd0\expndtw0\kerning0
This is the highest number of case counts in one day for each school in the 2020-2021 school year.  Meaning that if a school\'92s total case count was 1 on one day but 5 on another day, we will only take the 5 cases into account for that school because it is the max that they reported in one day for the school year.\
The other challenge was that enrolment data for the 2020-2021 school year was not publicly available so I had to use the enrolment data for the 2019-2020 school year.  It\'92s safe to assume that enrolment numbers stayed fairly consistent for the following year.\
<br>
\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 ***Answers and Analysis\
\pard\pardeftab720\qr\partightenfactor0

\f2\fs26 \cf3 \expnd0\expndtw0\kerning0
\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 **See full Jupyter Notebook [here]()**\
\
\pard\pardeftab720\sa320\partightenfactor0

\f1\fs32 \cf4 \cb5 \expnd0\expndtw0\kerning0
**Python libraries used**: *NumPy, Pandas, Seaborn, Matplotlib, Statsmodels*
\f0\fs24 \cf0 \cb1 \kerning1\expnd0\expndtw0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 I thought it was important to first separate and then compare elementary schools and high schools in Ontario in case this differentiation makes a difference in answering our hypothesis.  \
\
The visualization and descriptive statistics below provide clear breakdown:\
\
![BarChart]()\
![DescriptiveStats]()\
\
By creating an inner join of the Ontario Schools Covid dataset and the Ontario Schools Enrolment dataset and then creating a scatterplot, the answer to our question is very clear:\
\
![Scatterplot]()\
![Answer]()\
\
\pard\pardeftab720\sa280\partightenfactor0

\f1\fs28 \cf2 \expnd0\expndtw0\kerning0
These graphs show that most schools that had Covid cases had under 10 max cases in one day, regardless of their enrolment size.\
The elementary school with the highest enrolment in the province reported only the 2nd highest case count in one day in an elementary school (3rd highest overall if you also take high schools into account). And the school with the highest enrolment overall only had 3 cases as their max in one day.\
\pard\pardeftab720\sa140\partightenfactor0
\cf2 Meanwhile, extremely high case counts in one day (outliers) are in schools with low, average and high enrolment numbers (the full range).\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 \
<br>\
\
***Further Investigation
\f1\fs28 \cf2 \expnd0\expndtw0\kerning0
\
\pard\pardeftab720\qr\partightenfactor0

\f2\fs26 \cf3 \
\pard\pardeftab720\sa140\partightenfactor0

\f1\fs28 \cf2 These graphs show outliers very clearly. Let's see which schools these are
\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \
![Outliers]()\
\
\pard\pardeftab720\sa280\partightenfactor0

\f1\fs28 \cf2 \expnd0\expndtw0\kerning0
The outliers are a mix of elementary and secondary schools and are from different school boards (although the Toronto District School Board appears 6 times in the top 10. But that\'92s because the Toronto District School Board has the most number of schools in the province).\
I am still curious about the biggest outlier - Frank W Begley PS, which had 48 cases in one day. \
![Map](Outlier)\
Looking at this school in google maps, it is in Windsor, directly across the river from Detroit. You can swim it. This makes me wonder if frequent cross border travel to the US which had surging numbers early in the pandemic, leads to higher risk of infection.\
\pard\pardeftab720\sa140\partightenfactor0
\cf2 However, none of the neighbouring schools that you can see on the map even show up in the top 10 of our scatterplot.   West view, Holy Rosary School and FJ Brennan Catholic High School each had a max case count of 1.  So there is clearly something more in play here than just enrolment numbers and geographical location of the school.  \
\
That being said, this study was conducted and was based on data from before the more transmittable Omicron variant took hold.  It would be useful to do this study again with data from December 2021 when Omicron became the dominant variant and when schools were still open. 
\f0\fs24 \cf0 \kerning1\expnd0\expndtw0 \
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0
\cf0 \
}