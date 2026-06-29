Data Transformations Documentation
Project

Video Game Sales Dataset

Purpose

The purpose of this transformation process was to prepare the Video Game Sales dataset for analysis using Hive SQL. The data was cleaned, organized, and transformed to improve its quality and usability while preserving the original dataset.

Transformations Applied
1. Created a Working Table

A new table named sales_genre was created from the original sales table.

Hive Query

CREATE TABLE sales_genre AS
SELECT *
FROM sales;

Purpose

Preserve the original dataset.
Perform transformations on a separate working table.
2. Selected Relevant Columns

Only the columns needed for the analysis were selected.

Columns Selected

Genre
Global_Sales
Critic_Score

Hive Query

SELECT Genre,
       Global_Sales,
       Critic_Score
FROM sales_genre;

Purpose

Remove unnecessary attributes.
Simplify the dataset for analysis.
3. Rounded Global Sales Values

The Global_Sales values were rounded to whole numbers.

Hive Query

SELECT Genre,
       ROUND(Global_Sales) AS Global_Sales_Rounded,
       Critic_Score
FROM sales_genre;

Purpose

Improve readability.
Standardize numerical values for reporting.
4. Filtered Invalid Records

Only records with a Critic_Score greater than 0 were retained.

Hive Query

SELECT Genre,
       ROUND(Global_Sales) AS Global_Sales_Rounded,
       Critic_Score
FROM sales_genre
WHERE Critic_Score > 0;

Purpose

Remove missing or invalid critic scores.
Ensure accurate and meaningful analysis.
5. Sorted the Data

The filtered records were sorted by Critic_Score in descending order.

Hive Query

SELECT Genre,
       ROUND(Global_Sales) AS Global_Sales_Rounded,
       Critic_Score
FROM sales_genre
WHERE Critic_Score > 0
ORDER BY Critic_Score DESC;

Purpose

Rank games from the highest to the lowest critic score.
Make it easier to identify top-performing game genres.
Summary of Transformations
Transformation	Description
Create Working Table	Created sales_genre from the original sales table.
Select Columns	Kept only Genre, Global_Sales, and Critic_Score.
Round Values	Rounded Global_Sales to whole numbers.
Filter Records	Removed records with Critic_Score ≤ 0.
Sort Data	Ordered records by Critic_Score in descending order.
Result

After completing these transformations:

The original dataset remained unchanged.
The analysis dataset became cleaner and more organized.
Only relevant information was retained.
Invalid records were removed.
Sales values were standardized.
The dataset was ready for aggregation, visualization, and further business analysis.
