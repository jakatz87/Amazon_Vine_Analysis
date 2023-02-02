# Amazon Vine Analysis

## Overview
I used the ETL process to analyze Amazon reviews for Tools.  

## Resources
- [Amazon Tools Review](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Tools_v1_00.tsv.gz)
- Google Colab
- PySpark
- AWS, RDS, S3
- SQL, pgAdmin

## Process
- The first part of the project was extracting the data from Amazon's S3 service: 
![orig](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/Tools_Reviews.png)

- I then used PySpark to transform the data into smaller DataFrames or Tables:  

![customers](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/customers_df.png)

![products](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/products_df.png)

![review](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/review_id_df.png)

![vines](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/vine_df.png)

- I then used Amazon's RDS service to load these new tables into a database that could be accessible with pgAdmin and SQL programming:

![pgAdmin](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/pgAdmin_proof.png)

## Results

Analyzing the Vine Reviews, I found:

```
print(f"The number of Vine reviews is: {vine_df.count()}\n\
The number of Non Vine reviews is: {non_vine_df.count()}")
```
- There were 268 Vine Reviews to 29,517 Non-Vine Reviews

```
print(f"The number of 5 Star Vine reviews is: {vine_df.select('star_rating').where(vine_df.star_rating==5).count()}\n\
The number of 5 Star Non Vine reviews is: {non_vine_df.select('star_rating').where(non_vine_df.star_rating==5).count()}")
```
- There were 149 Vine 5 Star Ratings to 13,675 Non-Vine 5 Star Ratings

```
print(f"The percentage of 5 Star Vine reviews is: \
{round(vine_df.select('star_rating').where(vine_df.star_rating==5).count()/(vine_df.count())*100,2)}%   \n\
The percentage of 5 Star Non Vine reviews is: \
{round((non_vine_df.select('star_rating').where(non_vine_df.star_rating==5).count()/non_vine_df.count())*100,2)}%")
```
- 55.6% of the Vine Ratings were 5 Stars
- 46.33% of the Non-Vine Ratings were 5 Stars

## Summary
 
