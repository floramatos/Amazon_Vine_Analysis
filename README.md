# Examining the Association between Star Rating and Paid Reviews in Amazon Toy Reviews


## Overview
The purpose of this project was to examine whether there was a difference between the number of 5-star ratings for toy reviews between members and non-members of the Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

## Results

### ETL process
PySpark was used to perform the ETL (Extract, Transform and Load) process:
- The dataset was first extracted from Amazon S3 

*** Add print screen here
(https: //s3.amazonaws.com/amazon-reviews-pds/tsv/amazon reviews us Toys v1 00.tsv.gz).

- Then, the dataset was transformed into four different tables: review_id_table, products_table, customers_table and vine_table.

- These tables were loaded into pgAdmin through an AWS RDS instance connection.

### Star rating and Vine Membership Relationship
Jupyter Notebook and Python(Pandas) were used to examine if there were more 5-star reviews from Vine members in the dataset.   To conduct the present exploratory analysis, the vine_table was first exported from pgAdmin into a csv file. 

The whole vine_table dataframe had a total of 4,864,249 reviews. To pick reviews that are more likely to be helpful, the dataset was filtered to include reviews with:
- total_votes count equal to or greater than 20, and 
- number of helpful_votes divided by total_votes equal to or greater than 50%.

The resulting filtered dataframe had a total of 70,474 reviews, a minority from vine members, 1,266 of the reviews, and a majority from non-vine members, 62,028 of the reviews.

As seen in the Table below, 432 (34%) of the Vine reviews were 5 stars, while 29,982 (48%) of the non-Vine reviews were 5 stars.

*** Add print screen here

The higher percentage of 5-star rating for non-Vine reviews, compared to the percentage for Vine reviews, does not indicate the existence of a bias toward favorable reviews from Vine members.

## Summary
In sum, the exploratory analysis conducted here does not point to any positivity bias for reviews in the Vine program, as 5-star ratings were more frequent for non-Vine reviews compared to  Vine reviews.

To further investigate this question, the hypothesis of whether there is a relationship between vine membership and star review can be assessed by statistical testing using a Chi-square.

H₀: whether vine membership and star review are independent.
H₁: whether vine membership and star review are dependent.



