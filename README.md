# An Investigation into the EU Power Sector and its Clean Energy
Status

## Abstract

This report is an investigation into the European Union Power Section and its Clean Energy Status. The data used for this report is from EuroStat, and it investigated the 2019 statistics annual electricity data from 2016 to 2018 on the volumes of electricity that have been produced and supplied at the level of the European Union. (EuroStat) The data includes information on the annual total energy production of EU nations, as well as amount of annual energy production according to type, such as nuclear energy or solar energy. Our overarching research question is, how are we doing in terms of current progress with regards to renewable energy? Are we on the right track? Several statistical methods such as bootstrap confidence intervals, maximum likelihood estimation, hypothesis tests, simple linear regression, goodness of fit tests, and bayesian credible intervals were used to investigate research questions such as, what is average proportion of annual non-clean energy production in the EU in 2017, what is the estimated proportion of EU countries in 2018 that
have met their renewable energy production targets, and etc. The overarching finding was that clean renewable energy production integration is going very well and has progressed in the European Union. With specific findings such as, with 95% probability, the true proportion of EU countries that have met their target in 2018 is between 0.21 and 0.44 based on prior information. While the report does face some weaknesses and difficulty due to the lack of data points in the simple linear regression analysis, this has been suggested for future studies. Overall we were able to conclude that, results were very promising, and there is great hope that the European Union will continue to meet their target proportion of clean energy production in the coming years.

## Introduction

It is fair to assume that the most recent generation is the most aware of the issues of climate change, and
the most knowledgeable about the importance of sustainable living. The need to halt climate change and
promote sustainable living is the largest goal and problem our society faces today. In this report, we will
be investigating the power sector of the European Union and its status in its increase in renewable energy
production.

The data used for this report is from EuroStat, and it investigated the 2019 statistics annual electricity data
from 2016 to 2018 on the volumes of electricity that have been produced and supplied at the level of the
European Union. (EuroStat) The data includes information on the annual total energy production of EU
nations, as well as amount of annual energy production according to type, such as nuclear energy or solar
energy.

Increasing the amount of renewable energy production is a very effective way to reduce carbon emissions and
make way for sustainable living. This goal of increasing the use of renewable energy has been reflect multinationally
in the form of renewable energy production proportion targets. Governments across the globe have
been participating in meeting these targets set at these international forums in an effort to work together to halt climate change. An example would be the groups such as the G20, the EU and the Paris Agreement adopted at COP21. In tackling any large-scale issue, it is imperative that progress is assessed accurately
and without bias. Our report today tackles this problem and aims to accurately assess our progress in the
increase in renewable energy production using many statistical methods of analysis. The analysis in this
investigation will be important in setting new renewable energy production targets, judge how well we are
collaborating on the issue of climate change and whether our current efforts are indeed enough.
It is clear to see that such investigation holds global relevance, as the issue is inherently global. It is important
to note that international collaboration is a crucial, as well as most difficult when countries have their own
motives and goals in mind. This investigation will provide evidence on whether changes need to be made in
our fight towards sustainability or whether we are on the right track.

Before we get into the report, here is some important terminology that should be defined beforehand.
Clean renewable energy refers to energy produced by wind, solar, hydro and geothermal energy production
types. Non-clean renewable energy refers to energy produced by nuclear and conventional thermal energy
production types. A population is an entire group that we would like to draw conclusions about. (Bhandari)
A sample is a specific group that we have collected data from. (Bhandari) A confidence interval gives an
estimated range of values that is likely to include an unknown population parameter, the estimated range
being calculated from a given set of sample data. (Easton)

In this investigation we address several research questions and form several hypotheses. Our overarching
research question is, how are we doing in terms of current progress with regards to renewable energy? Are we
on the right track? Does the data align with what government officials claim to be true? Our main hypothesis
to the overarching research questions is that we have not progressed fast or far enough in renewable energy
production. And the claims made by government officials about our progress is questionable as it does not
necessarily align with our data.

Moreover, here are the specific research questions we will be investigating in this report.
1. On average, is the proportion of annual clean energy production increasing over the year 2018 among
the EU nations?
2. On average, what is the proportion of annual conventional thermal energy production across the EU
nations in the years 2016 to 2018?
3. On average, what is the proportion of annual non-clean energy production across the EU nations in
2017?
4. There is a claim by EuroStat that in 2018, the share of renewable energy in the EU is up to 18%.
(EuroStat) Can we trust this claim?
5. It is evident that some countries in the EU are doing better in meeting the renewable energy targets
than others. Suppose we were to grade the EU countries based on their renewable energy production
proportion, what would the distribution of these grades look like?
6. What is the estimated proportion of EU countries in 2018 that have met their renewable energy
production targets?

The next section in this report will describe the data used in this report.

## Data
The data used in this report is from a R package called tidytuesdayR. From tidytuesdayR we will be using
the European Energy Dataset, taken from Eurostat. The dataset includes information on the annual total
energy production in gigawatt hours for 37 nations in the European Union for the years 2016, 2017 and 2018.
It also includes information on the annual energy production in gigawatt hours separated into several energy production types for these same 37 nations for the years 2016, 2017 and 2018. The energy production types
are as follows, conventional thermal (fossil fuels), nuclear, hydro, wind, solar, geothermal, or other.
According to Eurostat, this dataset consists of information voluntarily supplied by the member states of the
European Union. (EuroStat) The data collection process for this report was fairly simple. The tidytuesdayR
package was installed and loaded as a library in R studio, then the European Energy Dataset was loaded in
from the R package.

There was quite an extensive cleaning process involved. Firstly, some minor errors on the country names
were fixed and NA values in the numerical columns were replaced with zeros. The main issue with the
original dataset was that the amount of energy produced was expressed in gigawatts hour. This meant that
when finding the average over countries, it would be impossible to control for the size of the country. So, we
used the proportion of energy production type. We introduced new columns; for example, the proportion
of conventional energy production, and were calculated by dividing the amount of energy produced by a
certain energy type by the total amount of energy produced in gigawatt hour for every country by year. We
also created a new column for clean energy to calculate the annual proportion of clean energy production,
which aggregated the energy production types, wind, solar, geothermal and hydro. The same was also done
for non-clean energy production types which included nuclear and conventional thermal.

We then end up with the dataset below. Here is a glimpse for a better idea.

<img src="images/img_1.png">

Here are some of the important variables. The year at the end of the variable names indicate the annual
year the energy production proportion is from. To avoid repetition, the variables will be described without
their year. Nonetheless, it is quite straight forward.

1. country_name : Categorical variable. Character type. Lists of the 37 nations in the European Union.
2. clean_prop : Numerical variable. Numeric type. Is the proportion of clean energy production (hydro,
wind, solar and geothermal) in a country for a certain year.
3. conventional_prop : Numerical variable. Numeric type. Is the proportion of conventional thermal
energy production in a country for a certain year.
4. non_clean_prop : Numerical variable. Numeric type. Is the proportion of non-clean energy production
(nuclear, conventional thermal) in a country for a certain year.

Here is the numerical summary of the proportion of clean energy production for 2017.

<img src="images/img_2.png">

We can see that in 2017, the average proportion of clean energy production across the EU nations was 0.13360.
What is more surprising is the spread of the data. The minimum proportion of clean energy production
is 0.01286, which is very very low. The maximum proportion of clean energy production is 0.47264, which
is very very high. This numerical summary shows that the progress of implementing renewable energy
production is very variable across countries. We observe that there are some countries that rely solely on
non-clean means of energy production, and certain countries that use renewable clean energy production
methods for about half of their annual energy production.

Let’s observe the distribution of the proportion of clean energy production for 2017.

<img src="images/img_3.png">

The plot above is a histogram of the proportion of clean energy production in 2017. On the x-axis we have
the proportion of clean energy production, and on the y-axis the frequency. The blue line in the graph
indicates the upper quantile, which is 75 percentile quantiles plus (1.5 multiplied by the interquartile range).
Intuitively, it represents the threshold for the upper bound outlier. The lower bound outlier threshold is not
in the plot as no points in the data were lower bound outliers. As we can see in the plot above, there were
three outlier data points in our dataset. Observing the plot and ignoring the outliers, the distribution seems
to be the close to a normal distribution and is not definitively skewed in either direction. This means that
a good parameter of interest will be the mean, rather than the median. This is because when there is no
skewness, the mean is an accurate representation of the middle of the data.
Later in investigation, we will perform a bootstrap on the proportion of conventional thermal energy production
for the years of 2016, 2017 and 2018. The bootstrap will allow us to find the true mean of the
proportion of conventional energy production for these years. We opted for the bootstrap method because
we only have 37 data points in our dataset. This is because there are only 37 countries in the European
Union. By performing a bootstrap, we will be able to increase the number of data points and reach a true
normal distribution of means. This will help us produce a reliable confidence interval for the true proportion
mean.

The next section will describe the methodologies used in the investigation.

## Methods

To answer the research question, on average, what is the proportion of annual conventional thermal energy
production across the EU nations in 2018, we will be using a statistical method called bootstrap confidence
intervals.

The aim of this method is to “make an inference about an estimate (such as sample mean) for a population
parameter (such as population mean) using sample data. It is a resampling method by independently
sampling with replacement from an existing sample data with the same sample size n and performing
inference among these resampled data” (Yen) We will also be using a certain type of bootstrapping method
called empirical bootstrapping, this is because our European Energy Data is empirical data. In our case we
will be randomly selecting 500 samples of the proportion of conventional thermal energy production with
replacement. This will be done for the year 2018. And the mean of each of these 500 samples will make up
the bootstrap sampling distribution. From this we will be able to obtain a confidence interval of 95%. Thus,
we will be able to estimate with 95% confidence that the mean of the proportion of conventional thermal
energy production in 2018 is a value in the range of the outputted confidence interval. This will help us
estimate the true mean of the proportion of conventional thermal energy production, and we will be able to
investigate how much EU countries are reliant on conventional thermal energy production, a non-renewable
energy source.

Our parameter of interest is the mean of the proportion of conventional thermal energy production in 2018.
And we will be bootstrapping over the proportion of conventional thermal energy production numerical
variable. We will be conducting one bootstrap for 2018. The bootstrap will have an iteration of 500 and a
sample size of 37, collected with replacement.

We deemed the bootstrap confidence interval due to its assumptions and practical rationale. The bootstrap
method is a very good choice for our variable and this dataset. This is because our dataset only consists
of 37 data points, due to the fact that the European Union has 37 member states. Our sample dataset
is not normally distributed, but by doing bootstrap sampling our estimate for the confidence interval will
stabilize thanks to the law of large numbers. This means as the number of sample means increases, the
bootstrap distribution will reach a normal distribution, allowing for a better true estimate of the interval of
the proportion of conventional thermal energy production.

There are a couple assumptions that have been made for the bootstrap method. Firstly, the sample data
must be independent and identically distributed. We assume that this is fulfilled as this is an empirical
dataset. There is a possibility of confounding variables between observations, but this is the best we can do for now. Secondly, the sample size should not be too small. This has also been fulfilled as 37 countries is a good enough size for a sample. We have also decided to use a 95% confidence interval, partly because it is very commonly used in statistics and because we are confident in our sample.

To answer the research question, on average, what is the proportion of annual non-clean energy production across the EU nations in 2017, we will be using a statistical method called maximum likelihood estimation.

Intuitively speaking, the aim of maximum likelihood estimation is to estimate a parameter of interest of an observed data distribution. Such as is the case here, we have an observed dataset on the proportion of energy production among the European Union Member states.  

The maximum likelihood estimator is obtained by maximizing the likelihood of the sample. The value that maximizes the likelihood is called the maximum likelihood estimator. Thus, we can obtain the solution through differentiation and find a value of the likelihood function that maximizes it. 

The parameter of interest for this method is the average proportion of non-clean energy production among EU nations in 2017. Our variable of interest is the proportion of non-clean energy production across the EU nations in 2017. When plotting the initial sample, the distribution seems to follow a normal distribution; the plot will appear in the results section. Therefore, we will assume that our empirical data follows a normal distribution and is a sequence that is independent and identically distributed. We also assume that the mean is $\mu$ and fixed variance, $\sigma^2$. We will use the maximum likelihood estimator (MLE) approach to estimate the mean, $\mu$. The MLE of $\mu$ is $\bar{X} = \hat{\mu}$. All derivations regarding the MLE can be found in Section 1 of the Appendix.

From the derivation in our appendix we can determine that maximum likelihood estimators of the mean are, $\hat{\mu} = \frac{1}{n} \sum_{i=1}^n(x_j)$.  

Thus, we can conclude that the maximum likelihood estimator $\hat{\mu}$ is equal to the sample mean.











