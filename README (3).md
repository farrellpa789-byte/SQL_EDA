# SQL Exploratory Data Analysis (EDA): Tech Layoffs

## 📊 Project Overview
Following the data cleaning phase, this project focuses on **Exploratory Data Analysis (EDA)** using MySQL. The objective is to explore the structured `layoffs_staging2` dataset to uncover trends, identify key patterns, and answer business questions regarding the global tech layoffs. 

This analysis provides a deep dive into which companies, industries, and countries were hit the hardest, as well as a chronological timeline of the layoff events.

## 🛠️ Tools & Advanced SQL Techniques Used
* **SQL Dialect:** MySQL
* **Key SQL Skills Applied:**
  * **Aggregations:** `SUM()`, `MAX()`, `MIN()`, `AVG()`
  * **Grouping & Sorting:** `GROUP BY`, `ORDER BY`
  * **Time Series Analysis:** Date extraction (`YEAR()`, `SUBSTRING()`)
  * **Advanced CTEs (Common Table Expressions):** Single and multiple cascading CTEs.
  * **Window Functions:** 
    * `SUM() OVER()` for calculating rolling/running totals.
    * `DENSE_RANK() OVER()` for ranking partitions of data.

## 🔍 Key Questions Explored & Insights Gained

Through this EDA, several critical business questions were addressed:

### 1. Overall Layoff Extremes
* **Maximums:** Identified the maximum number of employees laid off in a single day and the highest percentage of a company's workforce laid off.
* **Complete Shutdowns:** Filtered for companies that laid off 100% of their workforce (`percentage_laid_off = 1`), ordered by their funding to see the biggest companies that completely went under.

### 2. High-Level Aggregations (The "Worst Hit")
* **By Company:** Calculated the total sum of layoffs per company to identify who let go of the most employees overall.
* **By Industry:** Grouped data to see which tech sectors (e.g., Consumer, Crypto, Real Estate) suffered the heaviest job losses.
* **By Country:** Analyzed geographic data to see global layoff distributions.
* **By Stage:** Evaluated layoffs based on the company's funding stage (e.g., Post-IPO, Series B) to understand if mature or early-stage startups were more vulnerable.

### 3. Chronological Trends & Time Series
* **Timeline Range:** Extracted the absolute start (`MIN`) and end (`MAX`) dates of the dataset to understand the timeframe of the analysis.
* **Yearly Totals:** Grouped the total layoffs by year to observe macro-level trends.
* **Rolling Total (Running Sum):** Created a CTE utilizing `SUBSTRING()` on the date to group layoffs by Month and Year, then applied a Window Function to calculate the **rolling total of layoffs** over time, showing the cumulative impact month over month.

### 4. Advanced Ranking
* **Top 5 Layoffs Per Year:** Utilized a complex query involving two chained CTEs (`Company_Year` and `Company_Year_Rank`) and the `DENSE_RANK()` window function to partition the data by year. This successfully isolated and ranked the top 5 companies with the most layoffs for *each specific year*.

## 💡 Conclusion
This EDA highlights the severity of the tech layoffs across different dimensions. By leveraging advanced SQL queries, particularly CTEs and Window Functions, we transformed rows of data into actionable insights, revealing the timeline of the crisis, the hardest-hit sectors, and the specific companies that drove the highest layoff numbers.