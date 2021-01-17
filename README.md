# Amazon_Vine_Analysis
  
##  SUMMARY

The purpose of this project is to analyze Amazon review data through their Vine program.  The Vine program allows manufacturers and publishers to receive reviews of their products.  These manufacturers and publishers provide products to Vine members and then pay a small fee to Amazon to receive these reviews from Vine members.  The Vine members are required to provide a review.  

### Background

The dataset used for this project is the Amazon database of Musical Instrument reviews.  The data fields provided include:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/datasetschema.PNG)

The goal of this analysis is to determine if there is any bias towards favorable reviews amongst the Vine members as compared to the non-Vine member reviews.

##  ANALYSIS

I have used PySpark to read in the Amazon data.  I have created a dataFrame from which we can analyze the data separated between Vine and non-Vine member reviews.  

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_df.PNG)

To make the analysis more credible, I have removed the instances where the total votes are less than 20 since these will not be very helpful and might result in div0 problems later.  Next I reduce the data to only the rows where the percent of "helpful votes" to total votes is greater than or equal to 50%.  Again, we are looking for meaningful data so are reducing the dataset to reflect only the reviews that are considered helpful.  

After reducing for the above, the subject analysis data first 20 records looks like this:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_gt50pct.PNG)

After removing these above values, I have calculated tables by "Star Rating" of the review divided between those that were part of the Vine program and those that were not.  

###  VINE PROGRAM RESULTS


1.  The following table shows the total number of reviews that are part of the Vine program.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_y_gt50pct.PNG)

With only 263 Vine reviews, this is a fairly small sample for analysis purposes.  

2.  The following table breaks the total Vine reviews down by Star Rating and calculates the percent each star rating represents of the total Vine reviews.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_y_pct.PNG)

3.  Approximately 65% of Vine reviews give 5 star ratings to the products.  In addition, 24% give 4 star reviews.  So positive reviews total 89% of the reviews.  This is a large percentage.  


### NON-VINE RESULTS

1.  The following table shows the total non-Vine reviews in the dataset after reducing based on the same criteria as the Vine reviews.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_n_gt50pct.PNG)

With over 58,000 helpful reviews outside the Vine program, the non-Vine review data set is significantly more credible than the Vine dataset.  

2.  The following table shows the percent of reviews by star rating for non-Vine program reviews:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_n_pct.PNG)

3.  These reviews show that about 70% of non-Vine participant reviews have been given 5 stars.  This is slightly higher than the Vine review percents but still in the same ballpark.  In addition, 18% of the reviews rank the products as 4 stars.  So the positive results total 88% which is almost exactly the same as the Vine review dataset.  

### COMPARISON OF VINE VS NON-VINE RESULTS

The following pie charts help to visualize the percent of reviews by star rating for the two different populations we are examining.  

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/VinePie.png)

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/NonVinePie.png)

## SUMMARY OF RESULTS

Although there is a small difference in the 5 star reviews - 65% Vine vs 70% non-Vine, overall the positive reviews including the 4 and 5 star ratings is remarkably similar for the Vine vs non-Vine datasets.  In fact, the non-Vine review set had more 5 star reviews than the paid Vine review set.  Given the small size of the Vine dataset, this difference could be random variation rather than a true bias.  Just based on a visual review of these numbers, there does NOT appear to be any bias towards higher reviews in the paid Vine dataset.  To statistically confirm this results, we could use R to do hypothesis testing of these results by setting the null hypothesis that the average star review for each dataset is the same and the alternative hypothesis being that they are not the same.  However, this is beyond this basic analysis.  




