# SQL Data Cleaning — Tech Layoffs Dataset

> End-to-end data cleaning using MySQL on a real-world tech layoffs dataset

## 📌 Project Overview

Raw data is never clean. This project demonstrates a full data cleaning workflow in SQL — turning a messy dataset into analysis-ready data.

## 🧹 Cleaning Steps Performed

1. **Remove Duplicates** — Used ROW_NUMBER() + CTE to identify and delete duplicate rows
2. **Standardize Data** — Fixed inconsistent text (Crypto/CryptoCurrency), trimmed whitespace, removed trailing punctuation
3. **Handle NULL Values** — Converted blank strings to NULL, used self-JOIN to fill missing industry values from matching companies
4. **Convert Data Types** — Converted date column from text (mm/dd/yyyy) to proper DATE format using STR_TO_DATE()
5. **Remove Unnecessary Columns** — Dropped the row_num helper column after deduplication

## 🛠️ Tools Used

- **MySQL Workbench**
- **SQL concepts:** CTEs, ROW_NUMBER(), PARTITION BY, self-JOIN, UPDATE, ALTER TABLE, STR_TO_DATE()

## 📂 Files

- `Data_Cleaning.sql` — Full cleaning script with comments

## 💡 Key SQL Techniques

```sql
-- Identify duplicates using ROW_NUMBER
WITH duplicate_cte AS (
  SELECT *, ROW_NUMBER() OVER(
    PARTITION BY company, industry, total_laid_off, 
    percentage_laid_off, date) AS row_num
  FROM layoffs_staging
)
SELECT * FROM duplicate_cte WHERE row_num > 1;
```

## 📧 Contact

Suraj Vishwakarma 
— [LinkedIn](https://www.linkedin.com/in/suraj-vishwakarma-8761b3354/) 
— sv4235404@gmail.com
