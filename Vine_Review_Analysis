-- Deliverable 1: Perform ETL on Amazon Product Reviews
-- Create Active User Table
CREATE TABLE customers_table (
    customer_id INT PRIMARY KEY NOT NULL,
    customer_count INT
);

CREATE TABLE review_id_table (
    review_id TEXT PRIMARY KEY NOT NULL,
    customer_id INT,
    product_id TEXT,
    product_parent INT,
    review_date DATE 
);

CREATE TABLE products_table (
    product_id VARCHAR PRIMARY KEY NOT NULL,
    product_title TEXT
);

-- View table
SELECT * FROM customers_table 
SELECT * FROM review_id_table
SELECT * FROM products_table



-- Deliverable 2: Determine Bias of Vine Reviews
CREATE TABLE vine_table (
    review_id VARCHAR PRIMARY KEY NOT NULL,
    star_rating INT,
    helpful_votes INT,
    total_votes INT,
    vine VARCHAR(1),
    verified_purchase VARCHAR(1)
);

SELECT * FROM vine_table


-- Data is filtered to create a DataFrame or table where there are 20 or more total votes
CREATE TABLE totalvotes20 AS
	SELECT *
	FROM vine_table
	WHERE total_votes>=20;

SELECT * FROM totalvotes20;

-- Data is filtered to create a DataFrame or table where the percentage of helpful_votes is equal to or greater than 50% 
CREATE TABLE helpfulreviews AS
	SELECT *
	FROM totalVotes20
	WHERE CAST(helpful_votes AS FLOAT)/CAST(total_votes AS FLOAT) >=0.5;

SELECT * FROM helpfulreviews;

-- Data is filtered to create a DataFrame or table where there is a Vine review
CREATE TABLE helpfulreviewsvine AS
	SELECT *
	FROM helpfulreviews
	WHERE vine='Y';

SELECT * FROM helpfulreviewsvine;

-- Data is filtered to create a DataFrame or table where there isn’t a Vine review
CREATE TABLE helpfulreviewsnotvine AS
	SELECT *
	FROM helpfulreviews
	WHERE vine='N';

SELECT * FROM helpfulreviewsnotvine;

-- The total number of reviews, the number of 5-star reviews, and the percentage 5-star reviews are calculated for all Vine and non-Vine reviews
SELECT count(review_id) FROM helpfulReviews;
SELECT count(review_id) FROM helpfulReviewsVine;
SELECT count(review_id) FROM helpfulReviewsNotVine;

SELECT count(review_id) AS "5-Star Reviews" FROM helpfulReviewsVine
WHERE star_rating=5;

SELECT count(review_id) AS "5-Star Reviews" FROM helpfulReviewsNotVine
WHERE star_rating=5;

SELECT vine,COUNT(review_id) AS "5 Star Reviews",
CASE 
	WHEN vine='Y' THEN (SELECT count(review_id) FROM helpfulReviews WHERE vine='Y')
	WHEN vine='N' THEN (SELECT count(review_id) FROM helpfulReviews WHERE vine='N')
END AS "Total Reviews",
CAST(CAST(COUNT(review_id) AS FLOAT)/CAST(CASE 
	WHEN vine='Y' THEN (SELECT count(review_id) FROM helpfulReviews WHERE vine='Y')
	WHEN vine='N' THEN (SELECT count(review_id) FROM helpfulReviews WHERE vine='N')
END AS FLOAT) AS DEC(2,2)) AS "Percentage"
FROM helpfulReviews
WHERE star_rating=5
GROUP BY vine
ORDER BY vine DESC;
