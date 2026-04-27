# sql-data-warehouse-eLibrary
building a modern data warehouse with mysQL

Welcome to the "Data Warehouse and Analytical Project" repository!
This project demonstrates on how to build a proper and clean data warehouse and analytical solution that gives a meaningful insights!


Project Requirements

Objective: Develop a modern data warehouse using SQL server to consolidate sales data, enabling analytic reporting and informed.

Specifications
- dapat ma import ang data the sources 
- dapat ma cleanse natu ang raw data, no gaps, no invalid and errors
- integrations, combine sources



- store books and inventory
- manage transactions
- proper circulations



Design Data Architecture
Data Warehouse | Medallion Architecture

Design Data Layer




Bronze Layer
row and unprocessed data directly from the data sources
Traceability and debugging
Tables
Load Method
None
None

Silver Layer
Clean & standardize
Prepare data for Analysis
Tables
Full Load
Data Cleaning
Data Standardization
Data Normalization
Derived Columns (FK)
Data Enrichment
None

Gold Layer
Business-ready data
Present data to be consumed for reporting & Analytic
Views
None
Data Integration
Data Aggregations
Business Logic and Rules
Start Schema
Aggregated Objects
Flat Tables





Separations of Concerns




Naming Conventions (llower_snake) / English /

Bronze Layer
All source comes first then the table names, the table names must remain unchanged and match with its source, and ignore the case in mysql like “table”
<source>_<entity>
<source> = crm or erp
<entity> = table names
Example: crm_books

Silver Layer
Like the bronze layer, we keep consistent as well, the tables must still match the last layer before for traceability and debugging.
<source>_<entity>
Example: cm_books from silver layer | cm_books from bronze layer. must match

Gold Layer
All names are meaningful, something a user can easily identify for business consumers,
Names must be <category>_<entity>
<category> = dim or dimensions
<entity> = table name
examples:
dim_member_info → member ID, name, contact, membership type 

dim_book_info → book ID, title, author, genre, ISBN


Since dimension is the context or descriptive information around those events, it basically tells "who, what, where, when" in a table that gives meaning to your facts.


COLUMN NAMING CONVENTIONS


Surrogate Key
all primary keys must use the suffix _keys at the end
Example:
customer_key

Technical Columns
All technical columns must start with the prefix dwh_ like dwh_column_name
Example: dwh_load_date


Stored Procedure
All stored procedure must be named patterns like <load>_<layer>
Example : load_bronze, load_silver, load_gold
load_bronze -> loads the data in the bronze layer

