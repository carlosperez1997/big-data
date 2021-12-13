# Data warehouse

**A Data Warehousing (DW) is process for collecting and managing data from varied sources to provide meaningful business insights.** The data warehouse is **the core of the BI system** which is built for data analysis and reporting.

## How Datawarehouse works?
**A Data Warehouse works as a central repository where information arrives from one or more data sources. Data flows into a data warehouse from the transactional system and other relational databases.**

Data may be: Structured, Semi-structured  and Unstructured data.

**The data is processed, transformed, and ingested so that users can access the processed data in the Data Warehouse through Business Intelligence tools, SQL clients, and spreadsheets.**

By merging all of this information in one place, an organization can analyze its customers more holistically.

Data warehousing makes data mining possible. Data mining is looking for patterns in the data that may lead to higher sales and profits.

## Types of Data Warehouse
Three main types of Data Warehouses (DWH) are:

1. Enterprise Data Warehouse (EDW):

    Enterprise Data Warehouse (EDW) is a centralized warehouse. It provides decision support service across the enterprise. It offers a unified approach for organizing and representing data.

2. Operational Data Store:

    Operational Data Store, which is also called ODS, are nothing but data store required when neither Data warehouse nor OLTP systems support organizations reporting needs. In ODS, Data warehouse is refreshed in real time. Hence, it is widely preferred for routine activities like storing records of the Employees.

3. Data Mart:

    A data mart is a subset of the data warehouse. **It specially designed for a particular line of business, such as sales, finance, sales or finance.** In an independent data mart, data can collect directly from sources.

## Advantages of Data Warehouse (DWH):

- Data warehouse allows business users to quickly access critical data from some sources all in one place.
- Data warehouse provides consistent information on various cross-functional activities. It is also supporting ad-hoc reporting and query.
- Data Warehouse helps to integrate many sources of data.
- Data warehouse helps to reduce total turnaround time for analysis and reporting.
- Data warehouse allows users to access critical data from the number of sources in a single place. Therefore, it saves user’s time of retrieving data from multiple sources.
- Data warehouse stores a large amount of historical data. This helps users to analyze different time periods and trends to make future predictions.

## Disadvantages of Data Warehouse:

- **Not an ideal option for unstructured data.**
- **Data Warehouse can be outdated relatively quickly**
- **Difficult to make changes in data types and ranges, data source schema, indexes, and queries.**
- The data warehouse may seem easy, but actually, it is too complex for the average users.
- Despite best efforts at project management, data warehousing project scope will always increase.
- Organisations need to spend lots of their resources for training and Implementation purpose.

# ETL

ETL is a **process that extracts the data from different source systems, then transforms the data** (like applying calculations, concatenations, etc.) **and finally loads the data into the Data Warehouse system**. Full form of ETL is Extract, Transform and Load.

ETL is a recurring activity (daily, weekly, monthly) of a Data warehouse system and needs to be agile, automated, and well documented.

## Why do you need ETL?
There are many reasons for adopting ETL in the organization:

- It helps companies to analyze their business data for taking critical business decisions.
- **Transactional databases cannot answer complex business questions that can be answered by ETL example.**
- ETL provides a method of moving the data from various sources into a data warehouse.
- As data sources change, the Data Warehouse will automatically update.
- Well-designed and documented ETL system is almost essential to the success of a Data Warehouse project.
- **Allow verification of data transformation, aggregation and calculations rules.**
- ETL process allows sample data comparison between the source and the target system.
- ETL process can perform complex transformations and requires the extra area to store the data.
- ETL helps to Migrate data into a Data Warehouse. Convert to the various formats and types to adhere to one consistent system.
- ETL is a predefined process for accessing and manipulating source data into the target database.
- ETL in data warehouse offers deep historical context for the business.
- It helps to improve productivity because it codifies and reuses without a need for technical skills.

## ETL process

ETL is a 3-step process. 

![](https://www.guru99.com/images/1/022218_0848_ETLExtractT1.png)

###  Extraction

In this step of ETL architecture, **data is extracted from the source system into the staging area. Transformations if any are done in staging area** so that performance of source system in not degraded. Also, if corrupted data is copied directly from the source into Data warehouse database, rollback will be a challenge. **Staging area gives an opportunity to validate extracted data before it moves into the Data warehouse.**

Three Data Extraction methods:

- Full Extraction
- Partial Extraction- without update notification.
- Partial Extraction- with update notification
Irrespective of the method used, extraction should not affect performance and response time of the source systems. These source systems are live production databases. Any slow down or locking could effect company’s bottom line.

Some validations are done during Extraction:

- Reconcile records with the source data
- Make sure that no spam/unwanted data loaded
- Data type check
- Remove all types of duplicate/fragmented data
- Check whether all the keys are in place or not

### Transformation

**Data extracted from source server is raw and not usable in its original form. Therefore it needs to be cleansed, mapped and transformed.** In fact, this is the key step where ETL process adds value and changes data such that insightful BI reports can be generated.

It is one of the important ETL concepts where you apply a set of functions on extracted data. Data that does not require any transformation is called as direct move or pass through data.

**In transformation step, you can perform customized operations on data.** For instance, *if the user wants sum-of-sales revenue which is not in the database*. *Or if the first name and the last name in a table is in different columns. It is possible to concatenate them before loading.*

Following are Data Integrity Problems:

- Different spelling of the same person like Jon, John, etc.
- There are multiple ways to denote company name like Google, Google Inc.
- Use of different names like Cleaveland, Cleveland.
- There may be a case that different account numbers are generated by various applications for the same customer.
- In some data required files remains blank
- Invalid product collected at POS as manual entry can lead to mistakes.

Validations are done during this stage

- Filtering – Select only certain columns to load
- Using rules and lookup tables for Data standardization
- Character Set Conversion and encoding handling
- Conversion of Units of Measurements like Date Time Conversion, currency conversions, numerical conversions, etc.
- Data threshold validation check. For example, age cannot be more than two digits.
- **Data flow validation from the staging area to the intermediate tables.**
- Required fields should not be left blank.
- Cleaning ( for example, mapping NULL to 0 or Gender Male to “M” and Female to “F” etc.)
- Split a column into multiples and merging multiple columns into a single column.
- Transposing rows and columns,
- Use lookups to merge data
- Using any complex data validation (e.g., if the first two columns in a row are empty then it automatically reject the row from processing)

### Loading

Loading data into the target datawarehouse database is the last step of the ETL process. **In a typical Data warehouse, huge volume of data needs to be loaded in a relatively short period (nights).** Hence, load process should be optimized for performance.

In case of load failure, recover mechanisms should be configured to restart from the point of failure without data integrity loss. Data Warehouse admins need to monitor, resume, cancel loads as per prevailing server performance.

Types of Loading:

- Initial Load — populating all the Data Warehouse tables
- Incremental Load — applying ongoing changes as when needed periodically.
- Full Refresh —erasing the contents of one or more tables and reloading with fresh data.

Load verification
- Ensure that the key field data is neither missing nor null 
- Test modeling views based on the target tables.
- Check that combined values and calculated measures.
- Data checks in dimension table as well as history table.
- Check the BI reports on the loaded fact and dimension table.

## Best practices ETL process
Following are the best practices for ETL Process steps:

- Never try to cleanse all the data:
    
    Every organization would like to have all the data clean, but most of them are not ready to pay to wait or not ready to wait. To clean it all would simply take too long, so it is better not to try to cleanse all the data.

- Never cleanse Anything:

    Always plan to clean something because the biggest reason for building the Data Warehouse is to offer cleaner and more reliable data.

- Determine the cost of cleansing the data:

    Before cleansing all the dirty data, it is important for you to determine the cleansing cost for every dirty data element.

- To speed up query processing, have auxiliary views and indexes:

- To reduce storage costs, store summarized data into disk tapes. Also, the trade-off between the volume of data to be stored and its detailed usage is required. Trade-off at the level of granularity of data to decrease the storage costs.

# OLAP vs OLTP

OLTP, **Online Transaction Processing, is the most traditional processing system.** It is able to manage **transaction-oriented applications and can be characterized by a large number of short, atomic database operations, such as inserts, updates, and deletes, that are quite common in your day-to-day application.** Common examples include online banking and e-commerce applications. **Day to day operations of an application.**

OLAP, **Online Analytical Processing, manages historical or archival data.** It is characterized by a relatively low volume of transactions. OLAP systems are typically **used for analytical purposes — to extract insights and knowledge from bulk data, merged from multiple sources.** Unlike OLTP, the goal for OLAP systems is to have a limited amount of transactions, each consisting of mostly bulk reads and writes. **Data warehouses are the typical infrastructure to maintain these systems.** **Online query and analysis of business entities.**

Hopefully, by now, you are able to distinguish between both data processing systems easily. Both OLTP and OLAP systems have been around for quite some time, but recently, with the boom of data mining and machine learning techniques, the demand for OLAP systems has increased. Choosing a suitable technological infrastructure to host either system is also a crucial step to ensure your system or application is delivering the best performance for your needs.

| OLTP     | OLAP |
| ----------- | ----------- |
| Low volume of data     | High volume of data     |
| High volume of transactions   | Low volume of transactions       |
| Typically normalized data   | Denormalized data       |
| Require high availability    | Don’t usually require high availability       |
| One thing at a time    |  Aggregations and questioning of many things at a time      |
| Optimized for inserts and updates    |  Optimized for heavy reads |
| Uses just the current state    | Needs history to track business progression over time  |
| Optimal for application use, logical to the developer   | Optimal for business structure, understandable by business people  |
| Data might be inconsistent and presented in different logical way to the user. We may have multiple fields with the same names that have different data in them   | Data must be consistent for reports. There is one and only one field for a data point that means one thing (calculated in one accepted way)  |
|  The schema structure might change fundamentally for different application needs.  |  The schema must be consistent and flexible for different business needs. New business questions should not alter the schema in a way that invalidate old questions work  |




# Data warehouse schema design

## Normalization 3NF

We don't want to duplicate data. So we use keys, so we avoid storing one-to-many or many-to-many relationships in a table. 

![](https://www.guru99.com/images/1/022218_0848_ETLExtractT1.png)

## Fact tables and dimension tables

### Dimension

By what we measure things?
The who, what, when, where etc. of things
Examples: dates, products, countries...

How many purchases of a product have users from US made last year? We need dimensions to filter. 

![](images/dimension.png)

### Fact 

A fact is an observation or event. Something to be measured.  

Examples: Customer payment, user logins, product orders...

From a user login we can have a customer fk, that tells us the name of the user, its country or birthday; but we can also get to know things about the product, or the date the transaction was made.

In fact tables, we mix some dimensions with some facts. Facts have a meaning when with connect them to dimensions, so we know that the price corresponds to X product that was bought by Y customer. 

![](images/fact.png)

Facts change rapidly, but dimensions do not change often. The customer dimension might not change, their name would be the same, their birth date, it can change their email. 

## Kimball: Star schema

Fact table is in the middle and dimension tables feed the fact table. Fact table is connected to dimension tables via keys.

![](images/star_schema.png)

![](images/schema1.png)

### Grain 
The grain determines what each fact row contains and in what detail. The grain is defined by the dimensions in the fact table, and their details. 

Dimension presence example: For analytics, the platform dimension (less detailed grain: mobile, desktop or more detailed grain: iOS, Android, Blackberry, Mac...). 

The detail of the grain is defined by the business owners.

### Surrogate key

**The dimensions PK should be in control of the OLAP system.**

Don't use a PK from an operational system:

- Dimensions might change over time, to track changes the same on represented in the operational system might have multiple rows.

- Dimensions may come from multiple sources, sinchronizing the PK system is an unnecessary headache. 

- Decouple the OLTP system from the OLAP system.

### Slowly changing dimensions

Dimensions may change over time. There are multitple strategies to handle this:

- Type 1: Override the data. Don't track dimension history.
- Type 2: Add a new record for the new data, mark the old one inactive with inactivation date. RECOMMENDED!
- Type 3: Column of previous values in the table. 

**Bibliography:**

- [Data warehousing](https://www.guru99.com/data-warehousing.html)

- [ETL](https://www.guru99.com/etl-extract-load-process.html)

- [Row vs Columnar databases](https://dzone.com/articles/the-data-processing-holy-grail-row-vs-columnar-dat) 

- [Data warehouse schema design](https://snir.dev/talks/data-warehouse-schema-design)