# Amazon_Vine_Analysis
  
##  SUMMARY

The purpose of this project is to analyze Amazon review data through their Vine program.  The Vine program allows manufacturers and publishers to receive reviews of their products.  These manufacturers and publishers provide products to Vine members and then pay a small fee to Amazon to receive these reviews from Vine members.  The Vine members are required to provide a review.  

### Background

The dataset used for this project is the Amazon database of Musical Instrument reviews.  The data fields provided include:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/datasetschema.PNG)

The goal of this analysis is to determine if there is any bias towards favorable reviews amongst the Vine members as compared to the non-Vine member reviews.

#### ANALYSIS

I have used PySpark to read in the Amazon data.  I have created a dataFrame from which we can analyze the data separated between Vine and non-Vine member reviews.  

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_df.PNG)

To make the analysis more credible, I have removed the instances where the total votes are less than 20 since these will not be very helpful and might result in div0 problems later.  Next I reduce the data to only the rows where the percent of "helpful votes" to total votes is greater than or equal to 50%.  Again, we are looking for meaningful data so are reducing the dataset to reflect only the reviews that are considered helpful.  

After reducing for the above, the subject analysis data first 20 records looks like this:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_gt50pct.PNG)

After removing these above values, I have calculated tables by "Star Rating" of the review divided between those that were part of the Vine program and those that were not.  

###  VINE PROGRAM RESULTS


The following table shows the total number of reviews that are part of the Vine program.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_y_gt50pct.PNG)

With only 263 Vine reviews, this is a fairly small sample for analysis purposes.  

The following table breaks the total Vine reviews down by Star Rating and calculates the percent each star rating represents of the total Vine reviews.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_y_pct.PNG)

So about 65% of Vine reviews give 5 star ratings to the products.  

To compare to the non-Vine data, we look at the total size of the dataset. 

This total shows significantly more reviews than in the Vine program.  

The following table shows the percent of reviews by star rating for non-Vine program reviews:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_n_pct.PNG)

These reviews show that about 70% of non-Vine participant reviews have been given 5 stars.  This is slightly higher than the Vine review percents but still in the same ballpark.  





Now we will compare this to the non-Vine review.  This table shows the total non-Vine reviews in the dataset after reducing based on the above criteria.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_n_gt50pct.PNG)




Pie chart for Vine versus non-Vine Reviews

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/VinePie.png)

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/NonVinePie.png)
