# Amazon_Vine_Analysis
MapReduce, Spark &amp; AWS

## Project Background
Analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.<br>
<br>
Pick one of 50 datasets that contains reviews of a specific product, from clothing apparel to wireless product. Then, using PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, using SQL to determine if there is any bias toward favorable reviews from Vine members in that dataset. Lastly, a summary of the analysis will submit to the SellBy stakeholders.<br>
<br>

## Overview 
Deliverable 1: Perform ETL on Amazon Product Reviews
Deliverable 2: Determine Bias of Vine Reviews
Deliverable 3: A Written Report on the Analysis (README.md)

## Results
- How many Vine reviews and non-Vine reviews were there?
  - Vine reviews = 94
  - non-Vine reviews = 40,471
- How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
  - 5 stars Vine reviews  = 48
  - 5 starts non-Vine reviews = 15,663
- What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
  - 5 stars Vine reviews percentage = 51%
  - 5 starts non-Vine reviews percentage = 39%
