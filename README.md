# 🗄️ Project 2: Relational Database Architecture & SQL
### *30-Day Data Science Challenge*

## 📌 Project Overview
Today’s objective was to transition from flat-file processing (CSV) to a **Relational Database Management System (RDBMS)**. I migrated the financial health dataset into a SQLite environment to perform complex analytical queries that are more efficient in SQL than in Python memory.

## 🏗️ Database Schema
The data was ingested into a table named `finances`.
- **Primary Key:** `user_id`
- **Indexing Strategy:** Recommended for `income_type` and `credit_score` to optimize query performance for large-scale financial reporting.



## 📝 SQL Query Log

### 1. Competitive Ranking (Window Functions)
**Goal:** Identify high-performing savers within their specific employment peer groups.
```sql
SELECT user_id, income_type, savings_rate, 
       RANK() OVER (PARTITION BY income_type ORDER BY savings_rate DESC) as rank_within_group
FROM finances
WHERE credit_score > 700
LIMIT 15;
