# Predictive analytics for smarter city services
<a href="http://www.cityofchicago.org"><img src="http://dssg.io/img/partners/city.jpg" width="200"></a>
<a href="http://www.chapinhall.org"><img src="http://dssg.io/img/partners/chapin.jpg" width="400"></a>

**Exploratory analysis** and **predictive models** of how Chicago's neighborhoods interact with the City's 311 service requests.

This is project is a part of the 2013 [Data Science for Social Good](http://www.dssg.io) fellowship, in partnership with [City of Chicago](http://www.cityofchicago.org) and the [Chapin Hall at the University of Chicago](http://www.chapinhall.org).

## The Problem: understanding Chicago through 311, predicting 311 through Chicago
Through the City of Chicago's 311 system, every Chicagoan can ask for city services, from graffiti removal to pothole filling to abandoned car removal. The 311 data these service requests produce reflect - albeit imperfectly - the needs of the city and its inhabitants.

We want to investigate how patterns of service requests are related to the social and economic makeup of Chicago's neighborhoods. Specifically, we want to answer two related questions: 

- What do service requests tell us about the different neighborhoods in Chicago? 
- Can we use a neighborhood's characteristics to predict future service requests volumes across the city?

**[Read more about 311 in Chicago in our wiki.](https://github.com/dssg/411-on-311/wiki/problem)**

## The Solution: exploratory analysis, k-means clustering, poisson regression
To answer those big questions, we performed a three-step analysis:

1. [Exploratory analysis](http://en.wikipedia.org/wiki/Exploratory_data_analysis) of service request data through visualization of time series and scatterplots
2. Applied [k-means clustering](http://en.wikipedia.org/wiki/K-means_clustering), an unsupervised machine learning technique, to identify Chicago census tracts with similar service request patterns. This part of the analysis revealed clear clusters of census tracts that request 311 service in similar ways. These service-request clusters also tend to be geographically next to each other, and overlap with Chicago's race boundaries - a clear sign that Chicago's neighborhoods request services in distinct ways.
3. Built statistical models to predict 311 requests levels across census tracts. We trained a [Poisson Generalized Linear Models (GLM)](http://en.wikipedia.org/wiki/Poisson_regression) on relevant demographic, economic, and temporal predictors. We fitted Poisson GLM for graffiti removals pothole fillings, but the code is easily customized to work with other service request types. These predictive models could eventually be used to make the City's public services more proactive and responsive to street problems.

**Read more about [exploratory analysis](https://github.com/dssg/411-on-311/wiki/exploratory-analysis), [clustering](https://github.com/dssg/411-on-311/wiki/clustering-analysis), and [statistical models](https://github.com/dssg/411-on-311/wiki/statistical-models) in our wiki.**

## The Data: 311 service requests and census data
We used the main data sources:
 
1. Open 311 data from the City of Chicago [open data portal](http://data.cityofchicago.org). The City publishes to most popular service requests as open data, but only for the last few years.
2. A database of 311 requests obtained from Chapin Hall. This dataset is an extract of the City's 311 system - it contains every service request type (there are hundreds) and goes back to when the 311 system was launched in 1999.
3. 2010 Census and ACS (American Community Survey) data.

**[Read more about the data we used in our wiki.](https://github.com/dssg/411-on-311/wiki/data)**


## Project layout

### Data preparation
The folder `munging` contains some Python and R code that retrieves and preprocesses the data, aggregating it according to some specified spatial and temporal resolution (e.g. by Community Area, monthly.)

### Exploratory analysis
The code that implements our exploratory analysis lives in the `analysis/viz` folder. It's a set of functions that operates on 311 service request data from the City of Chicago [open data portal](http://data.cityofchicago.org). Most of this analysis is performed at the level of [community areas](en.wikipedia.org/wiki/Community_areas_in_Chicago).

### Clustering
The folder `analysis/clustering` contains code that applies the [k-means clustering algorithm](http://en.wikipedia.org/wiki/K-means_clustering) on a highly-dimensional space of 311 requests, aggregated by census tract. It uses the [scikit-learn](http://scikit-learn.org) machine learning Python library.

[![sci-kit-learn](http://scikit-learn.org/stable/_static/scikit-learn-logo-small.png)](http://scikit-learn.org)

### Predictive model
The code that implements our predictive models for graffiti removal and pothole filling requests is contained in the folder `analysis/prediction`. This part of the project is implemented in R.

## Installation guide
The project consists of Python scripts and modules, and R scripts.

- To execute [Python](http://www.python.org/) scripts, install Python 2.7.x on your computer, and call the invoke directly or within a Python interpreter (we recommend [iPython](http://ipython.org/).)
- To use Python modules (such as `analysis/viz/viz_311_data.py`), import the module within a Python file or a Python interpreter and call the functions.
- To execute R scripts, install [R](http://www.r-project.org/) and invoke the script directly or within the R interpreter. For editing and exploring the workspace, we recommend the [RStudio IDE](http://www.rstudio.com/ide/).

Some external libraries are needed:
- `Python` [scikit-learn](http://scikit-learn.org)
- `Python` [SciPy](http://www.scipy.org/)
- `Python` [matplotlib](http://matplotlib.org/)


## Team
[![311 team](http://dssg.io/img/people/teams/311.png)](http://dssg.io/people)

## Contributing to the Project
- Check out the [issue tracker](https://github.com/dssg/dssg-Indices-project/issues?page=1&state=open).
- For any question or information, contact [Alessandro Panella](mailto:apanel2@uic.edu).
 
## License

Copyright (C) 2013 [Data Science for Social Good Fellowship at the University of Chicago](http://dssg.io)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
