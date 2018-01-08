# Udacity Data Science NanoDegree - Descriptive Statistics Notes

**Construct** - difficult to measure

**Operational Definition** - how you define and choose to measure a construct - A way of turning constructs into variables we can measure and describing a variable in terms of the way we measure it

**Variables** - columns of data

**Extraneous factors** - **lurking variables** - provide possible alternative explanations for observed relationships between variables. Are factors that could influence the relationships we measure between two or more variables.  Should be controlled in an experiment before we can make confident causal statements. Make it difficult to make causal statements from data from observational studies

#### 1.15

**Hypothesis** - making a guess about how one thing influences another that you can test with an experiment

#### 1.17

**Population parameters** (suchas **mu**, or **μ**) are values that describe the entire population.

**Sample statistics** (such as **X-bar**,or **x̄**) are values that describe our sample; we use statistics to estimate the population parameters.

Mu represents the average of a population and x-bar represents the average of a sample

Estimates are our best guesses for the population parameters. So, for example, we would use X-bar to estimate mu.

**Sampling error** - The difference between the sample and population averages

#### 1.20

**Randomness** - when we have a random sample each subject has an equalchance of being selected and the selection of one individual has no effect onthe chances of any other individual being selected
Random samples are less likely to be biased and they're more likely to be representative of the population from which they are drawn

#### 1.21

Variable on the x-axis is the **predictor variable**, on the y-axis is the **dependent variable** or **outcome**
In an experiment the researcher manipulates the **independent variable**, measures changes in the dependent variable, and seeks to control **lurking variables**

#### 1.22

Correlation does not prove/imply causation

#### 1.28

**Response bias** is respondents not understanding the questions
**Non-response bias** is respondents refusing to answer

#### 1.30

**Blinding** - not letting this participants know which treatment they are getting
**Placebo** - inactive pill

**Informed consent** - let's participants know that they may be in the control group or the active treatment group

#### 1.31

**Double blind experiment** - neither the participants nor the researchers know whichgroup the participants are in

**Single-blind experiment** - only the participants don't know which group they're in

#### 1.33

**Random assignment** - everyone has exactly the same chance of being assigned to either group

#### 1.34

**Within subject design** - using the same person twice keeping most other things constant

#### 2.2

**Frequency table** - tally and then turn each tally into a number

#### 2.3

When data is organized we can quickly describe data, see patterns, and make decisions

#### 2.4

**Relative Frequency** - proportion of the whole - always between or equal to zero and one - all together should add to one

#### 2.8

Another way to show relative frequency is with percentages

#### 2.11

Group data in bins of equal size

#### 2.14

**Histogram** - bar graph in which each bar represents a bin - y-axis represents frequency

#### 2.23

**Histograms** vs **bar graphs** - **numerical** vs **categorical**

#### 2.26

A **normal distribution** has one peak called the **mode** (most frequent value) with gradually decreasing frequency on both sides so that it's a relatively symmetrical bell curve

#### 2.27

A **positively skewed** distribution has the mode (peak) closer to the left and **negatively skewed** has the mode (peak) closer to the right

#### 3.3

"one number to describe them all"

**Measures of Center** - or **measures of central tendency**

**Mode** - Value at which frequency is the highest - can be a range(bin) - can be no mode (**uniform distribution** 3.7) or multiple modes (**bimodal** or **multi-modal distribution** 3.8) if the distribution has 2 or moredistinct clear trends, they do not have to be equal in value, Can be a category if the data is categorical 3.9

**Median** - Middle value - 50% fall on either side (think of a highwaymedian) values must be sorted first 3.19 - If even number of values find theaverage of the two middle values.  Doesn't get thrown off by outliers asmuch as the mean

**Mean (Average)** - total of all values divided by the number of values

#### 3.14

**formula for finding the mean**

x-bar equals Sum of x divided by n

**x̄ = ∑x / n**

#### 3.29

**formula for finding the median**

For even numbers - [x sub (n / 2) plus x sub((n / 2) + 1)] / 2

For odd numbers - x sub(n + 1) / 2

The position of the median is the {(n + 1) ÷ 2}th value, where n is the number of values in a set of data.

If there is an even number of observations in the data set, there is no distinct middle value. So, the median is calculated by averaging the two middle values. i.e. if the formula above results in 7.5 then you would average the 7th and 8th values to find the median.

#### 3.30

Chart of pros and cons to 3 measures of center
Has simple equation - mean
Will always change if any data valuechanges - mean
Not affected by change in bin size - mean and median
Not affected severely by outliers - median and mode
Easy to find on a histogram - mode

#### 4.4

**Range** - difference between the maximum and the minimumvalues

#### 4.7

Traditionally statisticians cut off the upper and lower 25% of values.

#### 4.10

**Interquartile range (IQR)** - Q3 minus Q1

#### 4.12

**Outlier** - less than Q1 minus 1.5 times the IQR or greater than Q3 plus 1.5 times the IQR

#### 4.27

**Variance** - average squared deviation

#### 4.29, 4.30 and 4.31

**Standard deviation** - the square root of the variance, or the square root of the average squared deviation

**σ (sigma)** - represents the SD of a population

**s** - represents the SD of a sample

For variance, apply a squared symbol(s² or σ²).

#### 4.35

**What's so great about the Standard Deviation?**

In a normal distribution:

- 68% of the data falls within 1 SD of the mean and 
- 95% falls within 2 SD of the mean.
- 99.7% falls within 3 standard deviations.

#### 4.38

Samples tend to underestimate variability

**Besel's Correction** - divide by n-1 when calculating the variance
makes the variance and SD slightlylarger - estimates the SD of the population.  Calculated this way it's called the ***sample*** **standard deviation**

#### 5.9

A **normal distribution** is a theoretical model that uses relative frequencies and creates a smooth curve that can be described with an equation that allows us to calculate the proportion between any two values on the x-axis.

#### 5.10

All values on a normal distribution add to an area of one or 100%

#### 5.11

Values can be represented in terms of how many standard deviations they are away from the mean

#### 5.16

Formula for calculating the number of standard deviations a value is from the mean
x minus mu divided by sigma
**Z = (X – μ)/σ**

#### 5.17 through 5.21

standardizing any value on the x axis gives you the **z-score**.  The z- score is how many standard deviations a value is away form the mean.  Negative z-scores are less than the mean.  You can standardize any normal distribution

**Standardized Normal Distribution** and **Z-Scores**. That is, the z-score for any particular value of the variable X is X minus the mean (μ) for X, divided by the standard deviation (σ) of X. If you do this for all of the scores, you'll get the standardized normal distribution.

**Z = (X – μ)/σ**

So if you choose a value of X equal to the mean, then you will subtract the mean from itself, which yields 0. Thus, the mean in the standardized normal distribution is z = 0. If you choose a score that is one standard deviation above the mean and subtract the mean from it, then what you’ll have left is the standard deviation. When you then divide the standard deviation from that (thus, from itself), you’ll have z = 1.

http://scienceblogs.com/mixingmemory/2007/07/01/the-basics-of-statistics-ii-st/

**The mean in a standardized normal distribution is 0.**

**The standard deviation of a standardized normal distribution is 1.**

#### 6.1

A standardized normal distribution is called a “**Probability Density Function**” or **PDF**

#### 6.2

The area under the curve represents the probability of randomly selecting a value less than the value on the x-axis and also the proportion of the sample/population with values less than x.

#### 6.3

Tails never actually touch the x axis.  X-axis is a horizontal asymptote.  Can use a formula to describe a normal distribution PDF

#### 6.6

In a normal distribution 68% of values fall within 1 standard deviation of the mean and 95% fall within 2 SD’s.

#### 7.1

The mean of a sampling distribution is the same as the population mean

#### 7.12

**SE** = the standard deviation of all sample means or (**Standard Error**)

The "**standard deviation of the sampling distribution**" is also known as the standard error.

**σ (sigma)** - represents the SD of a population

**σ / SE** = square root of (n) your sample size!

#### 7.14

**Central Limit Theorem**

**σ/sqrt(n) = SE**

SE = Standard Error

The central limit theorem (CLT) is a statistical theory that states that given a sufficiently large sample size from a population with a finite level of variance, the mean of all samples from the same population will be approximately equal to the mean of the population.

#### 7.21

**If you quadruple your sample size you half your Standard Error.**