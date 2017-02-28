File failed to load: /extensions/MathZoom.js
Univariate Plots Section
Univariate Analysis
Bivariate Plots Section
Bivariate Analysis
Multivariate Plots Section
Multivariate Analysis
Final Plots and Summary
Reflection
Univariate Plots Section
Univariate Analysis
Bivariate Plots Section
Bivariate Analysis
Multivariate Plots Section
Multivariate Analysis
Final Plots and Summary
Reflection




wineQualityReds
Sahil Sachdea

feb 18, 2017


In this project, we will explore a data set on red wines quality. Our main objective is to explore the chemical properties influences the quality of red wines. This tidy data set contains 1,599 red wines with 11 variables on the chemical properties of the wine. The data set is available here and information about the data set is available here.

## 'data.frame':    1599 obs. of  13 variables:
##  $ X                   : int  1 2 3 4 5 6 7 8 9 10 ...
##  $ fixed.acidity       : num  7.4 7.8 7.8 11.2 7.4 7.4 7.9 7.3 7.8 7.5 ...
##  $ volatile.acidity    : num  0.7 0.88 0.76 0.28 0.7 0.66 0.6 0.65 0.58 0.5 ...
##  $ citric.acid         : num  0 0 0.04 0.56 0 0 0.06 0 0.02 0.36 ...
##  $ residual.sugar      : num  1.9 2.6 2.3 1.9 1.9 1.8 1.6 1.2 2 6.1 ...
##  $ chlorides           : num  0.076 0.098 0.092 0.075 0.076 0.075 0.069 0.065 0.073 0.071 ...
##  $ free.sulfur.dioxide : num  11 25 15 17 11 13 15 15 9 17 ...
##  $ total.sulfur.dioxide: num  34 67 54 60 34 40 59 21 18 102 ...
##  $ density             : num  0.998 0.997 0.997 0.998 0.998 ...
##  $ pH                  : num  3.51 3.2 3.26 3.16 3.51 3.51 3.3 3.39 3.36 3.35 ...
##  $ sulphates           : num  0.56 0.68 0.65 0.58 0.56 0.56 0.46 0.47 0.57 0.8 ...
##  $ alcohol             : num  9.4 9.8 9.8 9.8 9.4 9.4 9.4 10 9.5 10.5 ...
##  $ quality             : int  5 5 5 6 5 5 5 7 7 5 ...
##        X          fixed.acidity   volatile.acidity  citric.acid   
##  Min.   :   1.0   Min.   : 4.60   Min.   :0.1200   Min.   :0.000  
##  1st Qu.: 400.5   1st Qu.: 7.10   1st Qu.:0.3900   1st Qu.:0.090  
##  Median : 800.0   Median : 7.90   Median :0.5200   Median :0.260  
##  Mean   : 800.0   Mean   : 8.32   Mean   :0.5278   Mean   :0.271  
##  3rd Qu.:1199.5   3rd Qu.: 9.20   3rd Qu.:0.6400   3rd Qu.:0.420  
##  Max.   :1599.0   Max.   :15.90   Max.   :1.5800   Max.   :1.000  
##  residual.sugar     chlorides       free.sulfur.dioxide
##  Min.   : 0.900   Min.   :0.01200   Min.   : 1.00      
##  1st Qu.: 1.900   1st Qu.:0.07000   1st Qu.: 7.00      
##  Median : 2.200   Median :0.07900   Median :14.00      
##  Mean   : 2.539   Mean   :0.08747   Mean   :15.87      
##  3rd Qu.: 2.600   3rd Qu.:0.09000   3rd Qu.:21.00      
##  Max.   :15.500   Max.   :0.61100   Max.   :72.00      
##  total.sulfur.dioxide    density             pH          sulphates     
##  Min.   :  6.00       Min.   :0.9901   Min.   :2.740   Min.   :0.3300  
##  1st Qu.: 22.00       1st Qu.:0.9956   1st Qu.:3.210   1st Qu.:0.5500  
##  Median : 38.00       Median :0.9968   Median :3.310   Median :0.6200  
##  Mean   : 46.47       Mean   :0.9967   Mean   :3.311   Mean   :0.6581  
##  3rd Qu.: 62.00       3rd Qu.:0.9978   3rd Qu.:3.400   3rd Qu.:0.7300  
##  Max.   :289.00       Max.   :1.0037   Max.   :4.010   Max.   :2.0000  
##     alcohol         quality     
##  Min.   : 8.40   Min.   :3.000  
##  1st Qu.: 9.50   1st Qu.:5.000  
##  Median :10.20   Median :6.000  
##  Mean   :10.42   Mean   :5.636  
##  3rd Qu.:11.10   3rd Qu.:6.000  
##  Max.   :14.90   Max.   :8.000
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   3.000   5.000   6.000   5.636   6.000   8.000
After running the above commands, here are some simple observations:

There are 1599 observations in the dataset with 12 variables. Column ‘X’ was an identifier which wasn’t useful for analysis, so I removed it from the dataset. Quality variable is my focus of interest and it is an ordered, categorical variable. As per the information given regarding the dataset, red wines are rated on a 0-10 scale, and our sample had a range of 3-8 with a mean of 5.6 and median of 6 All other variables are continuous in nature. Since we are interested in the categorical variable Quality ,it makes sense to convert it into a factor.

Univariate Plots Section


We’ve found that the quality lies in the range of [3, 8] with mean is equal to 5.636.



The histogram reveals following observations:

Density and pH are normally distributed with a few outliers. Fixed and volatile acidity, sulfur dioxides, sulphates, and alcohol seem to be long-tailed.

Univariate Analysis
Quality of wine
As we can see the entire wine quality are in the range of 3 to 8 with the most common values are 5 and 6 and the least common values are 3, 4, 7, and 8. So, we create another variable rating with rate given below.

0 - 4 : poor
5 - 6 : good
7 - 10 : ideal
rw$rating <- ifelse(rw$quality < 5, 'poor', ifelse(rw$quality < 7,'good', 'ideal'))

rw$rating <- ordered(rw$rating, levels = c('poor', 'good', 'ideal'))
summary(rw$rating)
##  poor  good ideal 
##    63  1319   217
ggplot(data = rw, aes(x = as.factor(rating))) +
geom_bar() +
theme_minimal() +
scale_fill_brewer(type = 'seq', palette = 2)


Summary of the rating
##  poor  good ideal 
##    63  1319   217
Calculate total acidity
To calculate sum of all acids in the red wines, we create a new variable called total.acidity.

## [1]  8.10  8.68  8.60 12.04  8.10  8.06


Distribution and Outliers
fixed.acidity, volatile.acidity, sulfur.dioxide, sulphated and alcohol are appeared to be long tailed. density and pH are normally distributed with few outliers. residual.sugar and chlorides have extreme outliers. citric.acid contains large number of zero values.

Plot base 10 logarithmic scale of the long tailed distribution


Taking log_10, we can see that fixed.acidity, volatile.acidity, and sulphates are normally distributed, with some few outliers.

Find number of zeroes in citric.acid
## [1] 132
We found that 132 observations have zero values.

Find some patterns in residual.sugar and chlorides after removing some extreme outliers


After removing some extreme outliers, we see chlorides are now normally distributed Since residual.sugar comes in wide range as, it’ is’s rare to find wines with less than 1 gm/liter and wines with greater than 45 gm/liter are considered sweet, so the range of 1 - 4 as we found in the plot are ok with some outliers.

What is the structure of your dataset?
## 'data.frame':    1599 obs. of  15 variables:
##  $ X                   : int  1 2 3 4 5 6 7 8 9 10 ...
##  $ fixed.acidity       : num  7.4 7.8 7.8 11.2 7.4 7.4 7.9 7.3 7.8 7.5 ...
##  $ volatile.acidity    : num  0.7 0.88 0.76 0.28 0.7 0.66 0.6 0.65 0.58 0.5 ...
##  $ citric.acid         : num  0 0 0.04 0.56 0 0 0.06 0 0.02 0.36 ...
##  $ residual.sugar      : num  1.9 2.6 2.3 1.9 1.9 1.8 1.6 1.2 2 6.1 ...
##  $ chlorides           : num  0.076 0.098 0.092 0.075 0.076 0.075 0.069 0.065 0.073 0.071 ...
##  $ free.sulfur.dioxide : num  11 25 15 17 11 13 15 15 9 17 ...
##  $ total.sulfur.dioxide: num  34 67 54 60 34 40 59 21 18 102 ...
##  $ density             : num  0.998 0.997 0.997 0.998 0.998 ...
##  $ pH                  : num  3.51 3.2 3.26 3.16 3.51 3.51 3.3 3.39 3.36 3.35 ...
##  $ sulphates           : num  0.56 0.68 0.65 0.58 0.56 0.56 0.46 0.47 0.57 0.8 ...
##  $ alcohol             : num  9.4 9.8 9.8 9.8 9.4 9.4 9.4 10 9.5 10.5 ...
##  $ quality             : int  5 5 5 6 5 5 5 7 7 5 ...
##  $ rating              : Ord.factor w/ 3 levels "poor"<"good"<..: 2 2 2 2 2 2 2 3 3 2 ...
##  $ total.acidity       : num  8.1 8.68 8.6 12.04 8.1 ...
What is/are the main feature(s) of interest in your dataset?
As our main objective is to conclude quality. So, it’s the main feature.

What other features in the dataset do you think will help support your investigation into your feature(s) of interest?
density and pH are also normally distributed as our new variable rating. So, these two can help support our analysis.

Did you create any new variables from existing variables in the dataset?
I created an ordered factor rating, level each variables as ‘poor’, ‘good’ and ‘ideal’. And, total.acidity to calculate sum of all acids.

Of the features you investigated, were there any unusual distributions? Did you perform any operations on the data to tidy, adjust, or change the form of the data? If so, why did you do this?
residual.sugar and chlorides contains many outliers but after doing some operations, chlorides get into normal distribution citric.acid have very large number of zero values but after reading documentation it’s fine as it found in small quantities.

Bivariate Plots Section
Boxplot of quality


From this graph we can see that higher the citric acid and alcohol in wine higher is the quality

Boxplot of rating


poor rating seems to have following trends:

lower fixed.acidity, higher volatile.acidity and lower citric.acid. lower sulfur.dioxide and sulphates. higher pH and high density.

good rating seems to have following trends:

low fixed.acidity and volatile.acidity. higher sulfur.dioxide. low pH and higher density.

ideal rating seems to have following trends:

higher fixed.acidity , lower volatile.acidity and higher citric.acid. low sulfur.dioxide and higher sulphates. lower pH and density.

Finding relations between differnt variables


Citric acid and fixed acidity showed a strong positive correlation whereas pH and fixed acidity showed a strong negative correlation.

Correlation between residual.sugar and chlorides :
## 
##  Pearson's product-moment correlation
## 
## data:  rw$residual.sugar and rw$chlorides
## t = 2.2257, df = 1597, p-value = 0.02617
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.006606405 0.104346223
## sample estimates:
##        cor 
## 0.05560954
After removing some extreme outliers, we see chlorides are now normally distributed Since residual.sugar comes in wide range as, it’ is’s rare to find wines with less than 1 gm/liter and wines with greater than 45 gm/liter are considered sweet, so the range of 1 - 4 as we found in the plot are ok with some outliers.

Bivariate Analysis
poor rating seems to have following trends:

lower fixed.acidity, higher volatile.acidity and lower citric.acid. lower sulfur.dioxide and sulphates. higher pH and high density.

good rating seems to have following trends:

low fixed.acidity and volatile.acidity. higher sulfur.dioxide. low pH and higher density.

ideal rating seems to have following trends:

higher fixed.acidity , lower volatile.acidity and higher citric.acid. low sulfur.dioxide and higher sulphates. lower pH and density.

Correlation of variables against quality
##        fixed.acidity     volatile.acidity          citric.acid 
##           0.12405165          -0.39055778           0.22637251 
##       residual.sugar            chlorides  free.sulfur.dioxide 
##           0.01373164          -0.12890656          -0.05065606 
## total.sulfur.dioxide              density                   pH 
##          -0.18510029          -0.17491923          -0.05773139 
##            sulphates              alcohol        total.acidity 
##           0.25139708           0.47616632           0.10375373
Following variables show strong correlations with quality
alcohol sulphates citric.acid fixed.acidity

Multivariate Plots Section
To See which factors are affecting the quality of wine


Plot 1 - From this plot we can conclude higher alcohol and lower pH yields better wines

Plot 2 - From this plot we can conclude higher alcohol and sulphates yields better wines

Plot 3 - From this plot we can conclude higher alcohol and Citric.acid yields better wines

Plot 4 - From this plot we can conclude higher Citric.acid and lower fixed.acidity yields better wines

Relation of sulphates and alcohol on rating


It shows higher the % of alcohol and higher the sulphates give better wines.

Multivariate Analysis
I plot graph between four variables citric.acid, fixed.acidity, sulphates and alcohol which shown high correlations with quality. I conclude that higher citric.acid and lower fixed.acidity yields better wines. Better wines also have higher alcohol and sulphates and lower pH.

Final Plots and Summary
Plot One: Effect of alcohol on wine quality


Description
As alcohol is highly correlated with the quality, it is better to see its pattern with varying rating. From the above plot, it clearly shows higher % of alcohol yields better wine.

Plot Two : Effect of acids on wine quality


Description Two
As more the acidic better is the wine. It would be better to see which acids have more impact on wine quality. Above plot shows, fixed.acidity and citric.acid have highly correlated with quality but volatile.acidity has negative impact on quality.

Plot Three : Ideal vs poor wine


Description Three
It would be great to see the real pattern between good and bad wines. Above plot differentiate between good and bad wines. It shows higher the % of alcohol and higher the sulphates give better wines.

Reflection
So, there are lots of features on which the wine quality is depend. We do a lot to find the relationship between every variables in the dataset, try to get some linear relation using geom_smooth(). And, after this EDA, I can conclude that the major factors for better wine quality is alcohol, acidity and sulphates. These features must also be in required content otherwise negative impact will effect the wine quality. Also, we can’t be totally sure about quality index also it has been taken by some experts. We’ve also concluded that there is linear relationship between pH and quality with negative slope.

One problem that i faced was the amount of residual.sugar. It contains many outliers, also after doing some operation we get its common range from 1 to 4. But we can’t find its amount for ideal wine quality. I think more future research need to be done to find its ideal quantity.
