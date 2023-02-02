# Amazon Vine Analysis

## Overview
I used the ETL process to analyze Amazon reviews for Tools.  

## Resources
- [Amazon Tools Review](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Tools_v1_00.tsv.gz)
- Google Colab
- PySpark
- AWS, RDS, S3
- SQL, pgAdmin

## Results
- The first part of the project was extracting the data from Amazon's S3 service: ```from pyspark import SparkFiles
url = "https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Tools_v1_00.tsv.gz"
spark.sparkContext.addFile(url)
df = spark.read.option("encoding", "UTF-8").csv(SparkFiles.get("amazon_reviews_us_Tools_v1_00.tsv.gz"), sep="\t", header=True, inferSchema=True)```
![orig](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/Tools_Reviews.png)

- I then used PySpark to transform the data into smaller DataFrames or Tables:  

![customers](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/customers_df.png)

![products](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/products_df.png)

![review](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/review_id_df.png)

![vines](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/vine_df.png)

- I then used Amazon's RDS service to load these new tables into a database that could be accessible with pgAdmin and SQL programming:

![pgAdmin](https://github.com/jakatz87/Amazon_Vine_Analysis/blob/main/Resources/Images/pgAdmin_proof.png)

## Summary
 
