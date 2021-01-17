# Amazon_Vine_Analysis
  
##  SUMMARY

The purpose of this project is to analyze Amazon review data through their Vine program.  The Vine program allows manufacturers and publishers to receive reviews of their products and then pay a small fee to Amazon to provide these reviews to the Vine members.  The Vine members are required to provide a review.  

### Background

The dataset used for this project is the Amazon database of Musical Instrument reviews.  The data fields provided include:

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/datasetschema.PNG)

The goal of this analysis is to determine if there is any bias towards favorable reviews amongst the Vine members as compared to the total reviews.

#### ANALYSIS

I have used PySpark to read in the Amazon data.  I have created a dataFrame to collect the Vine data for analysis.  

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_df.PNG)

To make the analysis more credible, I have removed the instances where the total votes are less than 20 since these will not be very helpful and might result in div0 problems later.  Next I reduce the data to only the rows where the percent of "helpful votes" to total votes is greater than or equal to 50%.  Again, we are looking for meaningful data so are reducing the dataset to reflect the reviews that are considered helpful.  

After removing these above values, I have calculated tables by "Star Rating" of the review divided between those that were part of the Vine program and those that were not.  

The following table shows the total reviews that are part of the Vine program.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_y_gt50pct.PNG)

This table breaks the total Vine reviews down by Star Rating and calculates the percent each star rating represents of the total Vine reviews.


![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/vine_y_pct.PNG)

So 64.6% of Vine reviews give 5 star ratings to the products.

Now we will compare this to the non-Vine review.  This table shows the total non-Vine reviews in the dataset after reducing based on the above criteria.

![](https://github.com/xactuary/Amazon_Vine_Analysis/blob/main/ttl_n_gt50pct.PNG)




![]()
